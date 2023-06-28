---
title: Headless Adobe Commerce Architecture
description: Läs om vad som gör Adobe Commerce headless Architecture-strategi unik.
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Headless Adobe Commerce Architecture

Fördelen med Adobe Commerce arkitektur är att det inte är ett helt eller ingenting alls-erbjudande och en handlare kan hitta rätt blandning av lösningar för sin verksamhet. De kan bygga en PWA med PWA Studio som primärt kan användas för sin webbplatsupplevelse eller använda Adobe Experience Manager som skikt i komplexa kundresor, samtidigt som de bygger upp en egen front för att experimentera med nya kontaktytor. Ingen annan plattform kan matcha time to market-fördelarna och flexibiliteten som Adobe Commerce erbjuder med sin headless-arkitektur.

![Bild som visar en headless Adobe Commerce storefront-arkitektur](../../../assets/playbooks/headless-storefront-architecture.svg)

Varje tillvägagångssätt utesluter inte varandra. Kunderna kan bygga sin egen frontend (head), använda PWA Studio för webb-/mobilupplevelser och/eller använda Adobe Experience Manager för glaset (antingen i en fullständig eller hybridinstallation).

Adobe Commerce har alltid tillåtit headless-driftsättningar med REST API:er. REST är kraftfullt, särskilt för massbearbetning, men när det gäller headless möjliggör GraphQL API:er snabbare utveckling med en intuitiv utvecklarupplevelse, större flexibilitet genom att tillåta ändringar som inte påverkar befintliga API:er och bättre prestanda genom att minimera mängden data som hämtas till exakt det som behövs.

GraphQL är en branschstandard för presterande API:er, som används av många av de ledande e-handelsplattformarna. Det är bra eftersom det betyder att det finns en beprövad lösning och expertis på marknaden.

Även om Adobe Commerce har en kopplad butik som tillval behöver en handlare inte använda den gamla Adobe Commerce-fronten. En handlare kan utnyttja Adobe Commerce ledande e-handelstjänster för att hantera affärsprocesserna och, med våra butiks-API:er, integrera sin egen fristående butik för att skapa en förstklassig upplevelse.

Nu ska vi titta på de olika rubrikfria alternativen.

## PWA Studio

Det första är ett progressivt webbprogram som skapats med PWA Studio. En del av detta möjliggörs av det faktum att PWA är en headless storefront som frikopplas från e-handelsbackend. Med PWA Studio kan handlare bygga högpresterande, tillförlitliga och kostnadseffektiva PWA utöver Adobe Commerce och leverera högklassigt webbmaterial, både på mobiler och datorer. I takt med att tiden går kommer det kopplade arkivet att åsidosättas som standardalternativ.

De flesta handlare förstår inriktningen på branschen när det gäller PWA och många potentiella blockerare håller snabbt på att avlägsnas.

Vecka för vecka växer antalet partners som bygger upp expertis i PWA Studio och vi får allt fler kundstarter. Den senaste uppdateringen av PWA Studio innehöll utökningsmöjligheter som kommer att göra betydande framsteg när det gäller kompatibiliteten med Adobe Commerce Marketplace-tillägg.

Många handlare känner att de inte är redo för headless och PWA eftersom de kräver stort beroende av utvecklare. En av de stora fördelarna med att ha både e-handelsprogrammet och huvudrollen som utvecklats av Adobe Commerce är att det bidrar till att säkerställa kompatibiliteten mellan olika e-handelsfunktioner.

För att göra PWA mer lättillgänglig och enklare att hantera för våra handlare ger vi företagsanvändare möjlighet att hantera dagliga innehållsändringar, skapa nya landningssidor och mycket mer med hjälp av Page Builder. Dessa två kraftfulla funktioner tillsammans gör det möjligt att snabbt marknadsföra alla enheter och upplevelser.

## Adobe Experience Manager

Adobe Experience Manager är en kraftfull kombination för ert innehåll och era digitala resurshanteringsbehov och hjälper handlarna att få ut personaliserade, innehållsledda upplevelser på marknaden snabbare genom att kombinera digital resurshantering med kraften i maskininlärning, Adobe Sensei-drivet innehåll och kundresehantering.

Adobe Commerce plus Adobe Experience Manager är en kraftfull historia i och med att e-handelsmotorn gör det möjligt för företag att möjliggöra handel via kundgränssnitt som drivs av Adobe Experience Manager.

## Anpassade huvuden

Det sista alternativet att diskutera här är möjligheten att bygga en anpassad front. Det här alternativet är till för företag som har befintlig expertis och interna utvecklare som är kunniga i en viss frontgrupp, som React. Om de inte har någon kunskap i Adobe Commerce traditionella frontutveckling kan de bestämma sig för att det är mer kostnadseffektivt att bygga en egen, anpassad kontaktledning.

Den här modellen kräver naturligtvis starka kunskaper och resurser för kund- eller systemintegration i frontend, och du får inte den inbyggda kompatibiliteten med exempelvis Page Builder som du får med PWA Studio. Varje gång en handlare bygger något helt anpassat kan de förlora time-to-market-fördelar.

Anpassade gränssnitt möjliggör också innovationer och experimenterande. Det talas mycket om AR/VR eller rösthandel och med en arkitektur som Adobe Commerce kan handlare utforska dessa alternativ utan att påverka sina befintliga webbutiker.
