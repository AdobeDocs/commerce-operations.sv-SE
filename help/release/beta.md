---
title: Betaversioner
description: Läs mer om betaversioner av Adobe Commerce och hur du deltar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 07e616b26784a6e2e8994efc5816a5005619b5bb
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---

# Adobe Commerce betaversioner

Adobe Commerce betaprogram är ett sätt för handlare att få tillgång till betaversionsfunktioner och -kod, ge feedback och vägleda Adobe Commerce framtid. Det finns två typer av betaprogram:

- Betaversion: Ett offentligt betaprogram är tillgängligt för alla Adobe Commerce kunder och partners
- Private Bata: Ett privat betaprogram kan kräva ett godkännande baserat på kvalificeringskriterier för att kunna delta

>[!IMPORTANT]
>
>Betaversioner kan innehålla defekter och tillhandahålls i befintligt skick utan garanti av något slag. Adobe har ingen skyldighet att upprätthålla, korrigera, uppdatera, ändra, modifiera eller på annat sätt ge support (via Adobe Support Services eller på annat sätt) för betaversioner. Kunderna rekommenderas att iaktta försiktighet och att inte på något sätt förlita sig på att betaversionerna och/eller tillhörande dokumentation eller material fungerar korrekt eller fungerar korrekt. Funktioner och API:er i betaversionen kan ändras utan föregående meddelande. Därför är all användning av betaversioner helt och hållet på kundens egen risk.

## Fördelar

Genom att få tidig tillgång till funktioner som Adobe utvecklar kan kunder och partners ge feedback, utforma produktutvecklingen och förbereda sig för att använda nya funktioner innan de blir allmänt tillgängliga.

## Aktuella betaprogram

I följande avsnitt finns en lista med aktiva betaprogram.

### Integrering av IBM Sterling Order Management System (privat betaversion)

Integrationsacceleratorn för IBM Sterling Order Management gör det möjligt för Adobe Commerce-kunder att komma igång med avancerade orderhanteringsfunktioner som bygger på IBM Sterling OMS. Med den här integreringen får handlare:
- Synlighet i realtid av lagernivåer och korrekta leveransdatum för era kunder.
- Automatiserad anskaffning för beställningar baserat på konfigurerbara regler, så att ni kan optimera ert leveransnätverk och lager.
- En universell vy över beställningar över flera kanaler från en enda kontrollpanel så att era supportteam kan leverera utomordentliga tjänster och snabbt identifiera och hantera undantag.
- Ett mallat returhanteringsflöde som förenklar returhanteringen.

Om du vill delta i betaversionen skickar du en e-postförfrågan till [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Dataanslutning och Audience Activation (offentlig betaversion)

Bättre datadelning mellan Adobe Commerce och Adobe Experience Platform för effektivare personaliserade upplevelser. Detta gör att säljarna kan
- Dela Commerce kundprofiler
- Skapa anpassade attribut
- Få insikter om Commerce i Real-Time CDP och Adobe Journey Optimizer
- Stöd för flera datauppsättningar och datastreams

Om du vill delta i betaversionen skickar du en e-postförfrågan till [DataConnection@adobe.com](mailto:DataConnection@adobe.com).

### Backoffice Integration Starter Kit (privat betaversion)

The backoffice [startpaket för integrering](https://developer-stage.adobe.com/commerce/extensibility/app-development/starter-kit/) ger utvecklare en accelerator för att bygga händelsestyrda integreringar med system som ERP, CRM och OMS. Med startpaketet kan du minska utvecklingskostnaderna med upp till 50 %. Starter Kit följer också Adobe Commerce bästa praxis som minskar underhållskostnaderna avsevärt. Några av nyheterna i startpaketet:
- Datasynkronisering för vanliga objekt som produkt, order, kund, lager och leverans
- Arkitekturritningar som följer vedertagna standarder
- Inledande skript snabbar upp utvecklingen

Om du vill delta i betaversionen fyller du i [anmälningsformulär](https://forms.office.com/r/YbYArqE3DT).

### Adobe Commerce Foundation (offentlig betaversion)

Varje betaversion av Adobe Commerce Foundation innehåller alla ändringar som levererats till Adobe Commerce kärnkod vid det schemalagda releasedatumet, inklusive, men inte begränsat till, följande funktionsområden:

- Senaste säkerhetskorrigeringar
- Prestandaförbättringar
- Förbättringar i GraphQL
- Allmänna felkorrigeringar av kvalitet
- Bidrag från gemenskapen
- Ändringar som krävs för kompatibilitet med [Adobe Commerce-tjänster](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### Namngivningskonvention och schema

Adobe kommer att släppa betatestningar två gånger per år. Det första betatestet frisätts vanligtvis tre månader efter det att en ny viktig depotplåsterrelease allmänt finns tillgänglig.

Betaversionspaket har `-betaX` suffix. I betaversionspaketen för Adobe Commerce 2.4.7 används till exempel följande namnkonvention:

- `2.4.7-beta1`
- `2.4.7-beta2`

Se [publiceringsschema](schedule.md) om du vill se en lista över kommande allmänna betaversioner.


#### Tillgång till betaversioner

Adobe Commerce betaversioner distribueras på samma sätt som andra Adobe Commerce-korrigeringsutgåvor: som Composer-metapaket på `https://repo.magento.com`. Källkoden är tillgänglig på [GitHub](https://github.com/magento/magento2).

Se [Snabbstart vid installation av Composer](../installation/composer.md) för mer information.

#### Ärenderapportering

Adobe tillhandahåller inte Adobe support som standard för betaversioner.

Följ våra [regelbundet emissionsrapporteringsflöde](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) på [GitHub](https://github.com/magento/magento2).

Våra interna team övervakar alla kritiska problem som rapporteras mot den senaste betaversionen och prioriterar dem så att de kan lösas före GA-lanseringsdatumet.
