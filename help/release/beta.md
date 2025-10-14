---
title: Beta-versioner
description: Läs mer om betaversioner av Adobe Commerce och hur du deltar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: d467ada97a81d64dff358bc83acd489f69ba0677
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 0%

---

# Adobe Commerce betaversioner

Adobe Commerce betaprogram är ett sätt för handlare att få tillgång till betaversionsfunktioner och -kod, ge feedback och vägleda Adobe Commerce framtid. Det finns två typer av betaprogram:

- Offentlig Beta: Ett offentligt betaversionsprogram är tillgängligt för alla Adobe Commerce kunder och partners
- Private Beta: Ett privat betaprogram kan kräva ett godkännande baserat på kvalificeringskriterier för deltagande

>[!IMPORTANT]
>
>Beta-releaser kan innehålla defekter och tillhandahålls i befintligt skick utan någon garanti av något slag. Adobe har ingen skyldighet att upprätthålla, korrigera, uppdatera, ändra, modifiera eller på annat sätt ge support (via Adobe Support Services eller på annat sätt) för betaversioner. Kunderna rekommenderas att iaktta försiktighet och att inte på något sätt förlita sig på att betaversionerna och/eller tillhörande dokumentation eller material fungerar korrekt eller fungerar korrekt. Funktioner och API:er i betaversionen kan ändras utan föregående meddelande. Därför är all användning av betaversioner helt och hållet på kundens egen risk.

## Fördelar

Genom att få tidig tillgång till funktioner som Adobe utvecklar kan kunder och partners ge feedback, utforma produktutvecklingen och förbereda sig för att använda nya funktioner innan de blir allmänt tillgängliga.

## Beta-program

I följande avsnitt finns en lista med aktiva betaprogram.

### Patcheringstjänst för molnautomatisering (Private Beta)

[Tjänsten &#x200B;](../tools/caps-tool/intro.md) Creative Cloud Automation Patching automatiserar processen för att tillämpa isolerade säkerhetspatchar i [Adobe Commerce på molninfrastrukturen](https://experienceleague.adobe.com/sv/docs/commerce-on-cloud/user-guide/overview) -miljöer.

I oktober 2025 kommer betaversionen av Cloud Automation Patching Service att läggas till på kontrollpanelen för [Site-Wide Analysis-verktyget](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard). Den här tjänsten stöder Commerce projektadministratörer med ett smidigt arbetsflöde för patchning som innefattar:

- Automatiserad installation av korrigeringsfiler
- Återställning
- Verifiering efter distribution.

Tjänsten säkerställer att du kan upprätthålla säkra, stabila och uppdaterade miljöer med minimal manuell insats och risk.

Betaversionen innehåller följande funktioner:

- **Automatisera installation av korrigeringsfiler**: Förenkla och automatisera processen att åtgärda kritiska säkerhetsluckor i olika miljöer.
- **Minimera risken**: Förhindra webbplatsavbrott med hälsokontroll och återställningsfunktioner efter distributionen.

>[!NOTE]
>
>Eftersom tjänsten Cloud Automation Patching automatiskt tillämpar isolerade säkerhetspatchar måste du ha rollen [Contributor eller Project Admin](https://experienceleague.adobe.com/sv/docs/commerce-on-cloud/user-guide/project/user-access) för att kunna använda den.

Om du vill delta i den här betaversionen fyller du i och skickar [Cloud Automation Patching Service - Beta Sign-formulär](https://forms.office.com/r/3Wfxj5nPdB).

### Förbättrade sökfunktioner för Live Search (Public Beta)

Den här betaversionen stöder tre nya funktioner i [`productSearch`-frågan &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/):

- **Skiktad sökning** - Sök i ett annat söksammanhang - Med den här funktionen kan du utföra upp till två söklager för dina sökfrågor. Exempel:

   - **Layer 1-sökning** - Sök efter &quot;motor&quot; i &quot;product_attribute_1&quot;.
   - **Layer 2 search** - Search for &quot;part number 123&quot; on &quot;product_attribute_2&quot;. Det här exemplet söker efter &quot;part number 123&quot; i resultatet för &quot;engine&quot;.

  Skiktad sökning är tillgänglig för både `startsWith`-sökindexering och `contains`-sökindexering enligt beskrivningen nedan:

- **börjarMed sökindexering** - Sök med `startsWith`-indexering. Den nya funktionen gör att:

   - Söker efter produkter där attributvärdet börjar med en viss sträng.
   - Om du konfigurerar en&quot;slutar med&quot;-sökning kan kunderna söka efter produkter där attributvärdet slutar med en viss sträng. Om du vill aktivera sökningen &quot;slutar med&quot; måste produktattributet vara inverterat och API-anropet ska också vara en omvänd sträng.

- **innehåller sökindexering** -Sök efter ett attribut som använder innehåller indexering. Den nya funktionen gör att:

   - Söker efter en fråga i en större sträng. Om en kund till exempel söker efter produktnumret &quot;PE-123&quot; i strängen &quot;HAPE-123&quot;.

     >[!NOTE]
     >
     >Den här söktypen skiljer sig från den befintliga [frassökningen](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/), som utför en automatisk sökning. Om produktattributvärdet till exempel är &quot;utomhusbyxor&quot; returnerar en frassökning ett svar för &quot;out pan&quot;, men returnerar inget svar för &quot;or ants&quot;. En sökning innehåller emellertid ett svar på &quot;eller ants&quot;.

De här nya villkoren förbättrar funktionen för filtrering av sökfrågor för att förfina sökresultaten. De här nya villkoren påverkar inte huvudsökfrågan. Om du vill delta i betaversionen skickar du en e-postförfrågan till [commerce-storefront-services](mailto:commerce-storefront-services@adobe.com).

Mer information om hur du installerar betaversionen av Live Search finns i [Live Search-guiden](https://experienceleague.adobe.com/sv/docs/commerce/live-search/install#install-the-live-search-beta).

### IBM Sterling Order Management System Integration (Private Beta)

Integrationsacceleratorn för IBM Sterling Order Management gör det möjligt för Adobe Commerce-kunder att komma igång med avancerade orderhanteringsfunktioner som bygger på IBM Sterling OMS. Med den här integreringen får handlare:

- Synlighet i realtid av lagernivåer och korrekta leveransdatum för era kunder.
- Automatiserad anskaffning för beställningar baserat på konfigurerbara regler, så att ni kan optimera ert leveransnätverk och lager.
- En universell vy över beställningar över flera kanaler från en enda kontrollpanel så att era supportteam kan leverera utomordentliga tjänster och snabbt identifiera och hantera undantag.
- Ett mallat returhanteringsflöde som förenklar returhanteringen.

Om du vill delta i betaversionen skickar du en e-postförfrågan till [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Adobe Commerce Foundation (offentlig Alpha/Beta)

Alla Adobe Commerce Foundation alfa- och betaversioner innehåller alla ändringar som levereras till Adobe Commerce kärnkod före det planerade releasedatumet, inklusive, men inte begränsat till, följande funktionsområden:

- Senaste säkerhetskorrigeringar
- Prestandaförbättringar
- Förbättringar i GraphQL
- Allmänna felkorrigeringar av kvalitet
- Bidrag från gemenskapen
- Ändringar som krävs för kompatibilitet med [Adobe Commerce-tjänster](https://experienceleague.adobe.com/sv/docs/commerce/user-guides/home)

#### Namngivningskonvention och schema

Adobe släpper normalt alfa- och betatestningar flera gånger per år.

Alpha-versionspaket har suffixet `-alphaX`. Följande namnkonvention används till exempel i alfabetet för Adobe Commerce 2.4.7:

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Beta-versionspaket har suffixet `-betaX`. I betaversionspaketen för Adobe Commerce 2.4.7 används till exempel följande namnkonvention:

- `2.4.7-beta1`
- `2.4.7-beta2`

I [releaseplanen](schedule.md) finns en lista över kommande allmänna alfa- och betaversionsdatum.

#### Frigör åtkomst

Adobe Commerce alfa- och betaversioner distribueras på samma sätt som andra Adobe Commerce-korrigeringsutgåvor: som Composer-metapaket på `https://repo.magento.com`. Källkoden är tillgänglig på [GitHub](https://github.com/magento/magento2).

Mer information finns i [Snabbstart för installation av disposition](../installation/composer.md).

#### Ärenderapportering

Adobe tillhandahåller inte Adobe standardsupport för alfa- och betaversioner.

Om du vill skicka feedback om alfa- och betaversioner följer du det [regelbundna rapportflödet](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) på [GitHub](https://github.com/magento/magento2).

Adobe övervakar alla kritiska problem som rapporteras mot den senaste alfa- eller betaversionen och prioriterar dem så att de kan lösas före GA-releasedatum.
