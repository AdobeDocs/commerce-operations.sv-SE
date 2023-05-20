---
title: Betaversioner
description: Läs mer om betaversioner av Adobe Commerce och hur du deltar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Adobe Commerce betaversioner

Från och med juni 2023 och framåt kommer Adobe att publicera betaversioner för depotplåster (&quot;betaversioner&quot;). Betaversioner är tillgängliga för alla Adobe Commerce-kunder och -partners innan de blir allmänt tillgängliga (GA) och omfattar säkerhets-, efterlevnads-, prestanda- och högprioriterade kvalitetskorrigeringar.

>[!IMPORTANT]
>
>Betaversioner kan innehålla defekter och tillhandahålls i befintligt skick utan garanti av något slag. Adobe har ingen skyldighet att upprätthålla, korrigera, uppdatera, ändra, modifiera eller på annat sätt ge support (via Adobe Support Services eller på annat sätt) för betaversioner. Kunderna rekommenderas att iaktta försiktighet och att inte på något sätt förlita sig på att betaversionerna och/eller tillhörande dokumentation eller material fungerar korrekt eller fungerar korrekt. Därför är all användning av betaversioner helt och hållet på kundens egen risk.

## Frisläpp innehåll

Varje betaversion av Adobe Commerce innehåller alla ändringar som skickats till Adobe Commerce kärnkod före det planerade releasedatumet, inklusive, men inte begränsat till, följande funktionsområden:

- Senaste säkerhetskorrigeringar
- Prestandaförbättringar
- Förbättringar i GraphQL
- Allmänna felkorrigeringar av kvalitet
- Bidrag från gemenskapen
- Ändringar som krävs för kompatibilitet med [Adobe Commerce-tjänster](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

## Namngivningskonvention och schema

Adobe kommer att släppa betatestningar två gånger per år. Det första betatestningspaketet frisätts vanligtvis tre månader efter det att en ny viktig depotplåsterrelease finns allmänt tillgänglig.

Betaversionspaket har `-betaX` suffix. I betaversionspaketen för Adobe Commerce 2.4.7 används till exempel följande namnkonvention:

- `2.4.7-beta1`
- `2.4.7-beta2`

Se [publiceringsschema](schedule.md) för listan över kommande allmänna betaversioner.

## Fördelar med att delta

Ju tidigare du ser koden vi utvecklar desto snabbare kan du förbereda tekniken och handlarna för den kommande uppgraderingen.

Även om saker och ting kan förändras kan du med hjälp av betaversionerna börja förstå var i kodbasen ändringar sker och börja förbereda dig inför lanseringsdatumet för GA.

## Tillgång till betaversioner

Adobe Commerce betaversioner distribueras på samma sätt som andra Adobe Commerce-korrigeringsutgåvor: som Composer-metapaket på `https://repo.magento.com`. Källkoden är tillgänglig på [GitHub](https://github.com/magento/magento2).

Se [Snabbstart vid installation av Composer](../installation/composer.md) för mer information.

## Ärenderapportering

Adobe tillhandahåller inte Adobe support som standard för betaversioner.

Följ våra [regelbundet emissionsrapporteringsflöde](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) på [GitHub](https://github.com/magento/magento2).

Våra interna team övervakar alla kritiska problem som rapporteras mot den senaste betaversionen och prioriterar dem så att de kan lösas före GA-lanseringsdatumet.
