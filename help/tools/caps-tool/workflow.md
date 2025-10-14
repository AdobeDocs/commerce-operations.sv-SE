---
title: Så här fungerar  [!DNL Cloud Automation Patching Service (CAPS)] arbetsflödet
description: Lär dig mer om arbetsflödesprocessen i  [!DNL Cloud Automation Patching Service (CAPS)] , inklusive terminologi, arbetsflödesfaser och åtgärder för automatiserad korrigeringshantering.
hide: true
hidefromtoc: true
source-git-commit: eff8c0ae9e1d9db6b46ba7cfbb915685ab5b194d
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 0%

---

# Så här fungerar arbetsflödet i [!DNL Cloud Automation Patching Service (CAPS)]

Det här avsnittet innehåller en översikt på hög nivå över hur korrigeringsåtgärder fungerar med [!DNL CAPS (Cloud Automation Patching Service)].

## Terminologi

* **Åtgärder** - de huvudåtgärder som har utförts av [!DNL CAPS]:
   * Använd
   * Återställ
* **Fas** - de tre faserna i arbetsflödet:
   * Förhandskontroll
   * Lappa
   * Validering
* **Miljö** - Adobe Commerce Cloud-miljön där korrigeringar tillämpas.

## Operationer

[!DNL CAPS] har stöd för två *huvudsakliga åtgärder* för att hantera korrigeringar i Adobe Commerce Cloud-miljön:

* **Använd åtgärd** - lägger till korrigeringsändringar i kodbasen via en säker, validerad process. Patchar tillämpas genom att du placerar korrigeringsfiler i mappen &#39;m2-hotfixes&#39;.

* **Återställ åtgärd** - tar bort tidigare tillämpade korrigeringsfiler från kodbasen genom att ta bort korrigeringsfiler från mappen m2-hotfixes.

>[!IMPORTANT]
>
>Återställningsåtgärder är bara tillgängliga för korrigeringsfiler som ursprungligen tillämpades via [!DNL CAPS]. Patchar som används manuellt eller med andra metoder kan inte återställas med den här tjänsten.

## Faser

Arbetsflödet i [!DNL CAPS] använder tre *faser* som alltid körs i den här ordningen för att säkerställa att korrigeringarna tillämpas på ett säkert och tillförlitligt sätt:

* **Preliminär kontroll** - verifierar korrigeringens kompatibilitet och miljöberedskap.
* **Lappning** - tillämpar eller återställer korrigeringen i en integreringsmiljö.
* **Validering** - validerar korrigeringsprogrammet och utför hälsokontroller.

## Phase details

### Fas 1: Preliminär kontroll

Under fasen för förhandskontroll valideras att korrigeringen kan appliceras i din miljö.

**Vad händer:**

* **Skyddar produktionsmiljön** (endast produktionsmiljöer):
   * Kontrollerar om butiken är i underhållsläge
   * Verifierar att cron-jobb är inaktiverade
   * Blockpatchar om villkoren inte uppfylls
   * Visar bekräftelsedialogrutan om villkoren uppfylls
* **Patch validation** - verifierar att patchfilen är giltig och kompatibel
* **Miljöutvärdering** - kontrollerar miljöberedskap och resurser
* **Konfliktidentifiering** - identifierar potentiella konflikter med befintlig kod
* **Beroendekontroll** - validerar Adobe Commerce-versionskompatibilitet

### Fas 2: Lappning

Patcheringsfasen tillämpar eller återställer patchen i en temporär integreringsmiljö för testning. Under den här fasen skapar [!DNL CAPS] en tillfällig testmiljö för att säkert tillämpa och testa korrigeringen innan du gör ändringar i den faktiska miljön.

Detta tillvägagångssätt ger:

* **Säkerhet** - håller målmiljön orörd tills korrigeringen har validerats
* **Testar** - i en riktig miljö innan produktionen påverkas
* **Återställningsfunktion** - om problem upptäcks
* **Isolering** - för varje korrigeringsåtgärd

#### Steg 2a: Skapande av integreringsmiljö

**Skapande av gren** - [!DNL CAPS] skapar en temporär integreringsmiljögren med namnet `{target-environment}-CAPS-{patch-id}`

**Miljöinställningar** - Integreringsmiljön skapas som en underordnad till målmiljön

**Kodsynkronisering** - Integreringsmiljön ärver det exakta tillståndet för målmiljön

**Resurskrav** - [!DNL CAPS] skapar en tillfällig miljö med kodbasen från målmiljön. Enligt dokumentationen för Adobe Commerce Cloud har varje miljö (inklusive integreringsmiljöer) separat lagringstilldelning baserat på din avtalade lagringsplan. Mängden lagringsutrymme som du har anslutit motsvarar den totala lagringsmängden för varje miljö. I de flesta fall har du inga problem med resursbegränsningar. Om du råkar ut för något fel med resursbegränsningar bör du kontrollera programstorleken och det avtalade lagringsutrymmet i din plan.

#### Steg 2b: Programfix i integreringsmiljön

**Säker testning** - Korrigeringen tillämpas på integreringsmiljön, inte direkt på målmiljön

**Filhantering** - Korrigeringsfiler placeras i katalogen `m2-hotfixes/`

**Git-åtgärder** - Ändringarna har implementerats och skickats till integreringsmiljögrenen

**Miljöaktivering** - Integreringsmiljön aktiveras för att distribuera den patchade koden

#### Steg 2c: Lägg samman tillbaka till målmiljön

**Miljöutcheckning** - [!DNL CAPS] checkar ut målmiljön lokalt

**Sammanfogningsåtgärd** - Integreringsmiljögrenen sammanfogas i målmiljön

**Konfliktlösning** - Om det uppstår konflikter löses de automatiskt när det är möjligt

**Distribution** - De sammanslagna ändringarna distribueras till målmiljön

**Verifiering** - [!DNL CAPS] verifierar att sammanslagningen lyckades och att miljöerna är synkroniserade

**Miljörensning** - Den temporära integreringsmiljön tas bort för att frigöra resurser

## Integreringsmiljöns livscykel

Integrationsmiljöer har en särskild livscykel under patchningsfasen:

* **Skapad** - skapades i början av patchningssteget
* **Aktiv period** - förbli aktiv under korrigeringsprogram och testning
* **Rensa** - tas bort automatiskt efter sammanslagningen eller om åtgärden misslyckas

### Fas 3: Validering

Valideringsfasen säkerställer att det patchade programmet fungerar korrekt och utför hälsokontroller.

**Vad händer:**

* **Programhälsokontroll** - verifierar att programmet startar och körs korrekt
* **Rensa** - tar bort temporär miljö, uppdateringsloggar, meddelar slutförande

## Resultatindikatorer

**Tillämpa åtgärd:**

* &quot;Jobbet slutfördes utan fel&quot; - Korrigering utförd utan problem
* &quot;Patch has been applied&quot; - Patch was already present (no action needed)
* Korrigeringsfilen har placerats i mappen m2-hotfixes
* Alla valideringskontroller har godkänts
* Hälsokontrollerna i programmet har slutförts

**Återgå:**

* &quot;Jobbet har slutförts&quot; - korrigeringen har återställts utan problem
* &quot;Patch has been reverted&quot; - Patch was already reverted (no action needed)
* Korrigeringsfilen har tagits bort från mappen &#39;m2-hotfixes&#39;
* Alla valideringskontroller har godkänts
* Hälsokontrollerna i programmet har slutförts

## Skyddar produktionsmiljön

[!DNL CAPS] innehåller specifika säkerhetsfunktioner för produktionsmiljöer för att förhindra oavsiktliga avbrott och för att säkerställa att korrigeringsfiler valideras i förväg.

### Villkor för produktionspatchning

[!DNL CAPS] söker efter två kritiska förhållanden innan korrigeringar tillämpas på produktionsmiljöer:

* **Underhållsläge** - Butiken måste vara i underhållsläge
* **Kron-jobb inaktiverade** - Kron-jobb måste inaktiveras

Om något av villkoren inte uppfylls blockeras korrigeringsprogrammet och användaren meddelas om detta.

## Relaterade ämnen

* [Introduktion till CAPS](intro.md)
* [Åtkomst](access.md)
* [God praxis](best-practices.md)
* [Felsökning](troubleshooting.md)
