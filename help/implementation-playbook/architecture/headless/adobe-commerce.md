---
title: Headless Adobe Commerce Architecture
description: Läs om vad som gör Adobe Commerce till ett unikt sätt att arbeta med headless-arkitektur.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---


# Headless Adobe Commerce Architecture

Fördelen med Adobe Commerce är att det inte är ett helt eller ingenting-erbjudande och en handlare kan hitta rätt blandning av lösningar för sin verksamhet. De kan bygga ett PWA med PWA Studio som bas för sin primära webbplatsupplevelse eller använda Adobe Experience Manager som lager i komplexa kundresor, samtidigt som de bygger ut en egen front för att experimentera med nya kontaktytor. No other platform can match the time to market benefits and the flexibility that Adobe Commerce offers with its headless architecture.

![Diagram showing a headless Adobe Commerce storefront architecture](../../../assets/playbooks/headless-storefront-architecture.svg)

Each approach is not mutually exclusive. Kunderna kan bygga sin egen frontend (head), använda PWA Studio för webb-/mobilupplevelser och/eller använda Adobe Experience Manager för glaset (antingen i en fullständig eller hybridinstallation).

Adobe Commerce har alltid tillåtit headless-driftsättningar med REST API:er. While REST is powerful, especially for bulk processing, when it comes to headless, GraphQL APIs enable faster development through an intuitive developer experience, greater flexibility by allowing for changes that don’t impact existing APIs, and better performance by minimizing the amount of data retrieved to only exactly what is needed.

GraphQL är en branschstandard för prestanda-API:er, som används av många av de ledande e-handelsplattformarna. Det är bra eftersom det betyder att det finns en beprövad lösning och expertis på marknaden.

Även om Adobe Commerce har ett kopplat butiksområde som alternativ behöver en handlare inte använda den gamla Adobe Commerce-fronten. A merchant can take advantage of Adobe Commerce’s best-in-class commerce services to handle the backend business processes and, using our storefront APIs, integrate their own decoupled storefront to drive the frontend experience.

Now, let’s take a look at the various headless options.

## PWA Studio

Det första är ett progressivt webbprogram som skapats med PWA Studio. En del av detta möjliggörs av det faktum att PWA är en headless storefront som frikopplas från e-handelsbackend. Med PWA Studio kan handlare bygga högpresterande, tillförlitliga och kostnadseffektiva PWA ovanpå Adobe Commerce för att leverera förstklassiga webbupplevelser, både på mobiler och datorer. I takt med att tiden går kommer det kopplade arkivet att åsidosättas som standardalternativ.

De flesta handlare förstår inriktningen som branschen är på väg mot när det gäller PWA och många potentiella blockerare tas bort snabbt.

Vecka för vecka växer antalet partners som bygger upp expertis i PWA Studio och vi får allt fler kundstarter. I den senaste uppdateringen av PWA Studio ingick utökningsmöjligheter som kommer att göra betydande framsteg när det gäller kompatibilitet med tillägg från Adobe Commerce Marketplace.

Många handlare känner att de inte är redo för headless och PWA eftersom de kräver stort beroende av utvecklare. En av de stora fördelarna med att ha både handelsapplikationen och huvudrollen som utvecklats av Adobe Commerce är att den bidrar till att säkerställa kompatibiliteten mellan olika affärsfunktioner.

För att göra PWA mer lättillgänglig och enklare att hantera för våra handlare ger vi företagsanvändare möjlighet att hantera dagliga innehållsändringar, skapa nya landningssidor och mycket mer med hjälp av Page Builder. Dessa två kraftfulla funktioner tillsammans gör det möjligt att snabbt marknadsföra alla enheter och upplevelser.

## Adobe Experience Manager

Adobe Experience Manager är en kraftfull kombination för ert innehåll och era digitala resurshanteringsbehov som hjälper handlare att få ut personaliserade, innehållsledda upplevelser på marknaden snabbare och kombinera digital resurshantering med kraften i maskininlärning, Adobe Sensei-drivet innehåll och kundresehantering.

Adobe Commerce plus Adobe Experience Manager är en kraftfull historia i och med att e-handelsmotorn gör det möjligt för företag att bedriva handel via kundgränssnitt som drivs av Adobe Experience Manager.

## Custom Heads

Det sista alternativet att diskutera här är möjligheten att bygga en anpassad front. Det här alternativet är till för företag som har befintlig expertis och interna utvecklare som är kunniga i en viss frontgrupp, som React. Om de inte har någon kunskap i Adobe Commerces traditionella frontutveckling kan de bestämma sig för att det är mer kostnadseffektivt att bygga sin egen anpassade React Front.

Den här modellen kräver naturligtvis starka kunskaper och resurser för kund- eller systemintegration i frontend, och du får inte den inbyggda kompatibiliteten med exempelvis Page Builder som du får med PWA Studio. Varje gång en handlare bygger något helt anpassat kan de förlora time-to-market-fördelar.

Anpassade gränssnitt möjliggör också innovationer och experimenterande. There’s a lot of talk about AR/VR or voice commerce, and an architecture like Adobe Commerce’s allows merchants to explore these options without impacting their existing webstores.
