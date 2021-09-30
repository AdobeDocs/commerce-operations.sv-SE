---
title: Kopplad butiksarkitektur
description: Läs mer om vad en kopplad butik innebär inom ramen för de headless Adobe Commerce-arkitekturer.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Kopplad (äldre) arkitektur för Adobe Commerce storefront

Det nuvarande standardalternativet för distribution för de flesta företagskunder omfattar:

- Stöd för 100 % i B2B och B2C
- Tema för manuell referens (Luma) som snabbt kan driftsättas/anpassas
- Expertis inom implementering av masters-SI-partner
- Fullt kompatibel med e-handelsfunktioner som Page Builder eller Staging &amp; Preview
- Stor kompatibilitet med tillägg i Adobe Commerce Marketplace

![Bild som visar en kopplad arkitektur för butiker i Adobe Commerce](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Kon från äldre butiker

- **Inte headless** - Alla delar av den monolitiska Adobe Commerce-applikationen. Ingen åtskillnad mellan affärslogik och processer mellan frontend och backend.

- **Inte PWA** - Även om temat är responsivt ligger webbplatsprestandan långt efter PWA i toppklass.

- **Front-end-arkitektur (användargränssnittskomponenter för Adobe Commerce)** - Adobe Commerce/PHP-specialister som bygger på äldre butiker.

Låt oss börja med den mer välbekanta arkitekturen för butiker innan vi börjar använda headless. Om headless är frikopplat är detta den kopplade storefront-arkitekturen, som oftast ses med våra Luma-demos.

Det är här som butiksfunktionerna är nära integrerade med de centrala e-handelstjänsterna, som inte avgränsas av det GraphQL API-lagret. Så det finns en hel del affärslogik kopplad till det temat. Det här tillvägagångssättet är inte headless, och det är inte PWA.

Det här är för närvarande det vanligaste alternativet som handlare använder eftersom det har 100 % funktionsstöd med funktioner för både B2B- och B2C-handel. Det finns ett välbekant ekosystem av expertkunskap kring det, och det är i stort sett kompatibelt med utbyggnadsmöjligheterna i Adobe Commerce Marketplace.

Det saknar dock de fördelar som vi talade om tidigare. Utan att separera lager finns det många beroenden och potentiella felpunkter när ändringar görs. Det är inte lika bra som ett välimplementerat PWA, och om en handlare inte har expertis inom Adobe Commerce eller PHP-utveckling måste de hitta de resurserna.
