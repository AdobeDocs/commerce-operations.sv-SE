---
title: Felsökningsguide för [!DNL Cloud Automation Patching Service (CAPS)]
description: Felsöka vanliga problem och felmeddelanden i  [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: eff8c0ae9e1d9db6b46ba7cfbb915685ab5b194d
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 0%

---

# [!DNL Cloud Automation Patching Service (CAPS)] felsökningsguide

När du använder [!DNL CAPS] för korrigeringsåtgärder kan du stöta på felmeddelanden och problem som kan förhindra att korrigeringsprogrammet eller den nya versionen slutförs. Den här guiden innehåller lösningar på de vanligaste problemen.

## Snabba felsökningssteg

### Om korrigeringsåtgärden misslyckas

* Kontrollera åtgärdsstatus för att förstå vilken fas som misslyckades
* Granska felmeddelanden för specifika felorsaker
* Granska felloggarna för teknisk information
* Följ lösningarna i den här guiden

### Varaktighet för lagningsåtgärder

I de flesta miljöer beskriver följande tidslinje hur lång korrigeringsåtgärd ska ta, men den kan ta längre tid beroende på miljöns storlek och komplexitet:

* **Förbehandling:** 2-5 minuter
* **Laga:** 5-15 minuter
* **Efterbearbetning:** 10-40 minuter
* **Totalt:** 15-60 minuter

### Avbryt en pågående korrigering

>[!WARNING]
>
>När en korrigeringsåtgärd påbörjas bör den kunna slutföras. Systemet innehåller rensningsprocedurer som körs även om åtgärderna misslyckas. Om du avbryter processen kan miljön hamna i ett inkonsekvent tillstånd.

## Vanliga framgångsmeddelanden

* **&quot;Jobbet har slutförts&quot;** - Korrigeringen har tillämpats/återställts utan några problem.

* **&quot;Patch has been applied&quot;** - Du försöker tillämpa en korrigering som redan har tillämpats. Korrigeringen finns redan i din miljö. Ingen åtgärd krävs.

* **&quot;Patchen har återställts&quot;** - Du försöker återställa en korrigering som redan har återställts. Korrigeringen har inte installerats. Ingen åtgärd krävs.

## Vanliga felmeddelanden och lösningar

### Korrigera programfel

#### &quot;Det går inte att använda korrigeringen eftersom [!DNL CAPS] har upptäckt de här problemen med kodbasen eller korrigeringsfilen&quot;

**När det inträffar:** Under den preliminära kontrollen

**Orsak:** Korrigeringen är i konflikt med din aktuella kodbas ELLER så har det uppstått ett problem med själva korrigeringen

**Lösningar:**

* Granska de detaljerade felloggarna som finns för att se om det är en kodbas eller korrigeringsfil
* Kontrollera om det finns anpassningar i koden som står i konflikt
* Kontrollera att patchen är kompatibel med din Adobe Commerce-version
* Överväg att lösa konflikter manuellt eller kontakta support

#### &quot;Den här korrigeringen hanterades inte av [!DNL CAPS]. Kan inte återgå&quot;

**När det inträffar:** Under återställningsåtgärder

**Orsak:** Du försöker återställa en korrigering som inte tillämpades via [!DNL CAPS]

**Lösning:** Använd samma metod som användes för att tillämpa korrigeringen från början, eller kontakta supporten om du behöver hjälp manuellt

### Miljö- och valideringsfel

#### &quot;Miljön är inte synkroniserad med överordnad&quot;

**När det inträffar:** Under validering

**Orsak:** Integreringsmiljön skiljer sig från den överordnade miljön

**Lösningar:**

* Synkronisera din miljö med den överordnade grenen
* Försök utföra korrigeringen igen
* Kontakta support om synkroniseringsproblem kvarstår

#### &quot;Skyddsåtgärder för produktionsmiljö uppfylls inte&quot;

**När det inträffar:** Under den preliminära kontrollen för produktionsmiljöer

**Orsak:** Produktionsmiljön uppfyller inte de nödvändiga säkerhetsvillkoren

**Lösningar:**

* Aktivera underhållsläge för ditt produktionsarkiv
* Inaktivera cron-jobb i produktionsmiljön
* Kontrollera att båda villkoren uppfylls innan du försöker igen

>[!IMPORTANT]
>
> [!DNL CAPS] aktiverar inte automatiskt underhållsläge eller inaktiverar cron-jobb - dessa måste göras externt av dig

#### &quot;Lappningen har tillämpats, men hälsokontrollen misslyckades. Överväg att återställa&quot;

**När det inträffar:** Efter korrigeringsprogrammet under valideringen

**Orsak:** Korrigeringen har tillämpats, men hälsokontrollerna misslyckades

**Lösningar:**

* Granska programloggarna för specifika fel
* Testa viktiga funktioner manuellt
* Överväg att återställa korrigeringen om problemet kvarstår
* Kontakta support om du behöver hjälp

### Autentiserings- och åtkomstfel

#### &quot;Autentiseringen misslyckades för Adobe Commerce-databasen&quot;

**När det inträffar:** Under alla stadier

**Orsak:** Adobe Commerce-databasens autentiseringsuppgifter är ogiltiga eller har gått ut

**Lösningar:**

Det finns två rekommenderade alternativ för att lösa det här problemet:

**Alternativ 1: Korrigera `env:COMPOSER_AUTH` miljönivåvariabel (rekommenderas)**

* Kontrollera att du har konfigurerat rätt autentiseringsuppgifter för `env:COMPOSER_AUTH`.
* Du får åtkomst till den globala konfigurationen genom att klicka på kugghjulsikonen längst upp till vänster i ditt molnprojekts användargränssnitt och sedan välja fliken **Variabler** .
* Se till att du väljer _Tillgängligt under byggtid_ och avmarkera _Tillgängligt under körning_.

Om alternativ 1 inte löser problemet fortsätter du med alternativ 2.

**Alternativ 2: Skapa och distribuera `auth.json`-filen manuellt**

* SSH in på servern.
* Hämta innehåll för den aktuella `env:COMPOSER_AUTH`-variabeln med:\
  `echo $COMPOSER_AUTH`
* Kopiera allt innehåll från steget ovan (i JSON-format).
* Skapa en ny fil med namnet `auth.json` med det här innehållet.
* Genomför den här nyskapade `auth.json`-filen till databasens rotkatalog.
* Utlös en ny distribution.

#### &quot;Otillräckliga behörigheter för miljöåtkomst&quot;

**När det inträffar:** När miljön skapas eller används

**Orsak:** Ditt användarkonto saknar nödvändiga behörigheter

**Lösningar:**

* Kontrollera din användarroll och dina behörigheter
* Kontakta systemadministratören
* Verifiera att du har behörighet för miljöhantering
* Kontrollera att du har distributionsbehörigheter

### Resurs- och kvotfel

#### &quot;Miljökvoten har överskridits&quot;

**När det inträffar:** När miljön skapas

**Orsak:** Du har nått miljögränsen

**Lösningar:**

* Inaktivera oanvända miljöer
* Rensa gamla grenar och distributioner
* Kontakta support för att begära kvotökning
* Överväg att uppgradera din plan

#### &quot;Otillräckliga resurser för drift&quot;

**När det inträffar:** Under alla stadier

**Orsak:** Din miljö saknar tillräckligt med CPU, minne eller lagringsutrymme

**Lösningar:**

* Kontrollera resursanvändningen för miljön
* Frigör resurser genom att rensa filerna
* Vänta på att resurser blir tillgängliga
* Kontakta support om resursproblemen kvarstår

## Få hjälp

**När ska jag kontakta support:**

Kontakta supporten för Adobe Commerce Cloud när:

* Felmeddelanden är otydliga eller innehåller inte tillräckligt med information
* Lappningsåtgärder misslyckas genomgående
* Du behöver hjälp med manuell konfliktlösning
* Hälsokontrollerna misslyckas men orsaken är inte uppenbar
* Du behöver hjälp med miljösynkroniseringsproblem

**Information som ska anges:**

När du kontaktar supporten ska du ange:

* **Projekt-ID** - Ditt projekt-ID för Adobe Commerce Cloud
* **Miljö-ID** - Den specifika miljö där problemet uppstod
* **Åtgärds-ID** - Åtgärds-ID [!DNL CAPS]
* **Felinformation** - Fullständiga felmeddelanden och loggar
* **Steg för att återskapa** - Det du gjorde när felet inträffade
* **Tidigare försök** - Det du redan har försökt lösa problemet

### Ytterligare resurser

Mer detaljerad teknisk information:

* Granska de fullständiga felloggarna som finns i de misslyckade åtgärderna
* Läs Adobe Commerce-dokumentationen för korrigeringsspecifika riktlinjer
* Kontakta Adobe Commerce Cloud-supporten för miljöspecifika problem

### Relaterade ämnen

* [Adobe Commerce Cloud-dokumentation](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview.html)
* [Adobe Commerce installationshandbok](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/overview.html)
* [Introduktion till CAPS](intro.md)
* [Åtkomst](access.md)
* [Arbetsflöde](workflow.md)
* [God praxis](best-practices.md)
