---
title: Referensarkitektur för företag
description: Lär dig hur du implementerar Adobe Commerce med hjälp av Adobe senaste teknik för sammanställbar e-handel.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 581a7dbcc19c31df80e03cb9f321a6adb5fa1a73
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Adobe Commerce referensarkitektur

Adobe Commerce är den upplevelsestyrda plattformen som unikt förenar teknisk flexibilitet med användarvänlighet, och som helt och hållet används för att skapa exceptionella upplevelser som ger affärsresultat.

Commerce har utvecklats för att uppfylla företagets krav på prestanda, skalbarhet och säkerhet. Att implementera en modern implementeringsstrategi som använder de senaste kompositbara e-handelslösningarna från Adobe är avgörande för företagets framgång. På den här sidan beskrivs den moderna metoden för Commerce-implementering i detalj.

Följande arkitekturdiagram visar dataflödet mellan Adobe Commerce och alla Adobe Experience Cloud lösningar.

![Arkitekturdiagram som visar hur Adobe Commerce ansluter till lösningar från Experience Cloud](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"}

>[!NOTE]
>
>De högnivådataflöden som visas i diagrammet är konsekventa för de flesta företagsimplementationer. Den viktigaste komponenten som kan göra implementeringar unika är hur du skapar katalogen (särskilt för B2B). Du bör mappa katalogarkitekturen noggrant till [Commerce webb-API:er](https://developer.adobe.com/commerce/webapi/get-started/).

## Molngrund

[Adobe Commerce i molninfrastrukturen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) är grunden för din Commerce-implementering. Den ger en [säker](../../security-and-compliance/shared-responsibility.md) automatiserad värdplattform med en självbetjäningsmetod för att bygga, distribuera, övervaka och hantera ditt Commerce-program i en molnbaserad miljö.

Se följande tekniska information om molnbasen:

- [**Skalad arkitektur**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) - Automatiskt justerad kapacitet för att upprätthålla stabila, förutsägbara prestanda
- [**Flera miljöer**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture) - Företablerat med PHP, MySQL (MariaDB), Redis, RabbitMQ och stödda sökmotortekniker för att utveckla, testa och distribuera din webbplats
- [**Konfigurationshantering**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview) - Konfigurationsfiler för anpassningsbar miljö och kommandoradsgränssnitt (CLI) för att hantera programinställningar, vägar, skapa och distribuera åtgärder och meddelanden.
- [**Git-baserat arbetsflöde**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow) - Bygg och distribuera automatiskt efter push-kodändringar för snabb utveckling och kontinuerlig driftsättning
- [**Inbyggd observerbarhet**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) - Verktyg som kombinerar loggdata från flera källor för att hjälpa dig att hantera webbplatsens prestanda och diagnostisera problem
- [**Omfattande API-täckning**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) och [REST](https://developer.adobe.com/commerce/webapi/rest) API:er för integrering av Commerce kärnprogram med tredjepartssystem och utökade Commerce-funktioner

## Integration med Experience Cloud

Adobe Commerce kan integreras med alla Experience Cloud-lösningar för att leverera [personaliserade e-handelsupplevelser i stor skala](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[Dataanslutning](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) låser upp insikter om kundernas köpbeteende så att ni kan skapa personaliserade shoppingupplevelser i alla kanaler med andra Adobe-produkter för digitala upplevelser.

>[!NOTE]
>
>Mer information finns i följande källor:
>
>- [Digital Experience-utkast](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) för mer teknisk information.
>- Se [Anpassa kundupplevelsen](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/personalization).


## Integrering med tredjepartssystem

Adobe förser utvecklarna med omfattande tilläggspunkter och verktyg för att bygga applikationer som utökar Commerce kärnfunktioner och integrerar Commerce med tredjepartssystem (som CRM, ERPS och PIMS). Med dessa verktyg minskar du den totala ägandekostnaden för plattformen på följande sätt:

- **Skalbarhet** - Program kan skalas separat från kärnprogramvaran, vilket ger ökad effektivitet och förenklar uppgraderingar.
- **Isolering** - En isolerad miljö innebär att utvecklare kan uppgradera eller ändra sina tillägg efter eget gottfinnande utan att förlita sig på en kärnversion.
- **Tekniskt oberoende**-Utvecklare kan välja vilket teknikläge och vilka kodningsspråk som passar deras behov.

Adobe tillhandahåller följande utvecklingsverktyg för att bygga integreringar och anpassningar:

- [**API-nät för Adobe Developer App Builder**](https://developer.adobe.com/graphql-mesh-gateway/) - Koordinera och kombinera flera API:er, GraphQL, REST och andra källor till en enda frågningsbar slutpunkt för GraphQL.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/) - Bygg och distribuera säkra och skalbara webbprogram som utökar Commerce funktionalitet och integreras med tredjepartslösningar.
- [**Händelser**](https://developer.adobe.com/commerce/extensibility/events/) - Använd anpassade händelseutlösare för att interagera med andra utökningsbara utvecklingsverktyg.
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/) - Använd webhooks för att automatiskt aktivera interaktion mellan Commerce och tredjepartssystem.
- [**Admin UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/) - Anpassa och förbättra Commerce Admin med nya sidor och funktioner för era handlare.
- [**Integration Starter Kit**](https://developer.adobe.com/commerce/extensibility/starter-kit/) - Snabba upp integreringen med referensintegreringar, introduktionsskript och en standardiserad arkitektur.

>[!NOTE]
>
>Se [Den moderna metoden: Effektiv utökningsbarhet i Adobe Commerce](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/extensibility).

## Tjänster för butikstjänster

Adobe erbjuder en mängd intelligenta, sammanställningsbara tjänster för att hjälpa er att uppnå era affärsmål. Dessa tjänster tillhandahåller även API:er som är viktiga för att optimera prestanda i stor skala.

- [Livesökning](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview) - Få smartare, snabbare och relevanta resultat för kunderna med det här AI-baserade sökverktyget.
- [Produkt-Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview) - Lägg till AI-baserade rekommendationer baserat på kundbeteende, populära trender, produktlikhet med mera.
- [Katalogtjänst](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview) - Ge dina kunder en optimerad produktupplevelse samtidigt som du förbättrar prestanda, skalbarhet och ökar antalet konverteringar.
- [Betalningstjänster](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview) - Öka kundnöjdheten genom att erbjuda olika betalningsmetoder, inklusive räntefria betalningar, och en enda vy över betalningshantering, order och fakturor.

## Headless storefront

Headless commerce is API-first commerce. Adobe Commerce är helt headless med en frikopplad arkitektur som ger alla e-handelstjänster och data via ett GraphQL API-lager. Med den här arkitekturen kan teamen utveckla sina gränser oberoende av huvudapplikationen, vilket gör det enkelt att snabbt skapa och testa nya kontaktytor med ny teknik.

Adobe har en modern, headless storefront-teknik som innehåller samma fördelar och funktioner som [Edge Delivery Services](https://www.aem.live/home) har med dokumentbaserad redigering, en arkitektur som sätter prestanda först och som har färdiga inbyggda experiment. Den utnyttjar skalan och prestandan hos Adobe Commerce [storefront-tjänster](#storefront-services) och flexibiliteten och bekvämligheten hos [drop-in-komponenter](https://experienceleague.adobe.com/developer/commerce/storefront/) för att leverera e-handelsfunktioner.

