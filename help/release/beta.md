---
title: Beta-versioner
description: Läs mer om betaversioner av Adobe Commerce och hur du deltar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: f90279e0e152204ac976db307ca14d4418cbcba8
workflow-type: tm+mt
source-wordcount: '1094'
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

### Förbättrade sökfunktioner för Live Search (Public Beta)

Den här betaversionen stöder tre nya funktioner i [`productSearch`-frågan ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/):

- **Skiktad sökning** - Sök i ett annat söksammanhang - Med den här funktionen kan du utföra upp till två söklager för dina sökfrågor. Exempel:

   - **Layer 1-sökning** - Sök efter &quot;motor&quot; i &quot;product_attribute_1&quot;.
   - **Layer 2 search** - Search for &quot;part number 123&quot; on &quot;product_attribute_2&quot;. Det här exemplet söker efter &quot;part number 123&quot; i resultatet för &quot;engine&quot;.

  Skiktad sökning är tillgänglig för både `startsWith`-sökindexering och `contains`-sökindexering enligt beskrivningen nedan:

- **börjarMed sökindexering** - Sök med `startsWith`-indexering. Den nya funktionen gör att:

   - Söker efter produkter där attributvärdet börjar med en viss sträng.
   - Om du konfigurerar en&quot;slutar med&quot;-sökning kan kunderna söka efter produkter där attributvärdet slutar med en viss sträng. Om du vill aktivera sökningen &quot;slutar med&quot; måste produktattributet vara inverterat och API-anropet ska också vara en omvänd sträng.

- **innehåller sökindexering** -Sök efter ett attribut som använder innehåller indexering. Den nya funktionen gör att:

   - Söker efter en fråga i en större sträng. Om en kund till exempel söker efter produktnumret &quot;PE-123&quot; i strängen &quot;HAPE-123&quot;.

      - Obs! Den här söktypen skiljer sig från den befintliga [frassökningen](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase), som utför en automatisk sökning. Om produktattributvärdet till exempel är &quot;utomhusbyxor&quot; returnerar en frassökning ett svar för &quot;out pan&quot;, men returnerar inget svar för &quot;or ants&quot;. En sökning innehåller emellertid ett svar på &quot;eller ants&quot;.

De här nya villkoren förbättrar funktionen för filtrering av sökfrågor för att förfina sökresultaten. De här nya villkoren påverkar inte huvudsökfrågan. Skicka ett e-postmeddelande till `sagonzal@adobe.com` eller `alexj@adobe.com` för betaåtkomst.

Mer information om hur du installerar betaversionen av Live Search finns i [Live Search-guiden](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install#install-the-live-search-beta).

### Experience Manager Assets Integration för Commerce (Private Beta)

Experience Manager Assets Integration för Commerce möjliggör effektiv hantering och leverans av ett stort antal produktbilder från Experience Manager Assets till Adobe Commerce med låg eller ingen driftansträngning.

Viktiga funktioner:

- Integrering med Plug and play - Tillhandahåll en Adobe-baserad integrering mellan Experience Manager Assets och Adobe Commerce som gör det möjligt för handlare att fokusera på det som är viktigast, med minskade driftskostnader och ökad effektivitet.

- Anpassa produktbilder i stor skala Använd Experience Manager Assets för att generera miljontals produktvarianter för personaliserade Commerce-upplevelser med lättanvända gränssnittsbaserade redigeringsverktyg, generativt innehåll med Adobe Firefly och arbetsflöden för tilldelade resurser för att säkerställa ett enhetligt varumärke. När du är nöjd med materialet kan du smidigt leverera det till dina Commerce-butiker med Experience Manager Assets Integration.

- Enkel introduktion - Förenkla kundintroduktionen med en konfigurerbar synkroniseringsprocess som möjliggör fullständig synkronisering mellan Experience Manager Assets-databasen och Commerce-katalogen.

- Flexibel matchningsstrategi - Integreringen innehåller standardalgoritmer för tillgångsmatchning baserat på SKU:er för produkter som synkroniserar bilder mellan AEM Assets och Commerce, och den kan utökas med Adobe Developer App Builder. Samarbeta med er lösningspartner för att bygga upp en anpassad strategi för tillgångsmatchning utöver integreringen för att få plats med en databasstruktur för resurshantering.

Om du vill delta i betaversionen skickar du en e-postförfrågan till [Shaun McCran](mailto:mccran@adobe.com).

### IBM Sterling Order Management System Integration (Private Beta)

Integrationsacceleratorn för IBM Sterling Order Management gör det möjligt för Adobe Commerce-kunder att komma igång med avancerade orderhanteringsfunktioner som bygger på IBM Sterling OMS. Med den här integreringen får handlare:

- Synlighet i realtid av lagernivåer och korrekta leveransdatum för era kunder.
- Automatiserad anskaffning för beställningar baserat på konfigurerbara regler, så att ni kan optimera ert leveransnätverk och lager.
- En universell vy över beställningar över flera kanaler från en enda kontrollpanel så att era supportteam kan leverera utomordentliga tjänster och snabbt identifiera och hantera undantag.
- Ett mallat returhanteringsflöde som förenklar returhanteringen.

Om du vill delta i betaversionen skickar du en e-postförfrågan till [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Dataanslutning och Audience Activation (offentlig Beta)

Bättre datadelning mellan Adobe Commerce och Adobe Experience Platform för effektivare personaliserade upplevelser. Detta gör att säljarna kan

- Dela Commerce kundprofiler
- Skapa anpassade attribut

Om du vill delta i betaversionen skickar du en e-postförfrågan till [DataConnection@adobe.com](mailto:DataConnection@adobe.com).

### Adobe Commerce Foundation (offentlig Beta)

Varje betaversion av Adobe Commerce Foundation innehåller alla ändringar som levererats till Adobe Commerce kärnkod vid det schemalagda releasedatumet, inklusive, men inte begränsat till, följande funktionsområden:

- Senaste säkerhetskorrigeringar
- Prestandaförbättringar
- Förbättringar i GraphQL
- Allmänna felkorrigeringar av kvalitet
- Bidrag från gemenskapen
- Ändringar som krävs för kompatibilitet med [Adobe Commerce-tjänster](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### Namngivningskonvention och schema

Adobe släpper normalt betatestningar två gånger per år.

Beta-versionspaket har suffixet `-betaX`. I betaversionspaketen för Adobe Commerce 2.4.7 används till exempel följande namnkonvention:

- `2.4.7-beta1`
- `2.4.7-beta2`

Se [releaseplanen](schedule.md) för en lista över kommande allmänna betaversionsdatum.


#### Tillgång till releaser från Beta

Adobe Commerce betaversioner distribueras på samma sätt som andra Adobe Commerce-korrigeringsutgåvor: som Composer-metapaket på `https://repo.magento.com`. Källkoden är tillgänglig på [GitHub](https://github.com/magento/magento2).

Mer information finns i [Snabbstart för installation av disposition](../installation/composer.md).

#### Ärenderapportering

Adobe tillhandahåller inte Adobe support som standard för betaversioner.

Följ vårt [regelbundna rapportflöde](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) på [GitHub](https://github.com/magento/magento2) om du vill skicka feedback som gäller betaversioner.

Våra interna team övervakar alla kritiska problem som rapporteras mot den senaste betaversionen och prioriterar dem så att de kan lösas före GA-lanseringsdatumet.
