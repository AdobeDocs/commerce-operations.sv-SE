---
title: Kopplad butiksarkitektur
description: Läs mer om vad en kopplad butik innebär i kontexten med headless Adobe Commerce-arkitekturer.
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Kopplad (äldre) Adobe Commerce storefront-arkitektur

Det nuvarande standardalternativet för distribution för de flesta företagskunder omfattar:

- Stöd för 100 % i B2B och B2C
- Tema för manuell referens (Luma) som snabbt kan driftsättas/anpassas
- Expertis inom implementering av masters-SI
- Fullt kompatibel med e-handelsfunktioner som Page Builder eller Staging &amp; Preview
- Bred kompatibilitet med tillägg i Adobe Commerce Marketplace

![Bild som visar en kopplad Adobe Commerce storefront-arkitektur](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Kon från äldre butiker

- **Inte headless**—All part of the monolithic Adobe Commerce application. Ingen åtskillnad mellan affärslogik och processer mellan frontend och backend.

- **Inte PWA**- Även om temat är responsivt ligger webbplatsens prestanda långt efter PWA i toppklass.

- **Front-end-arkitektur (Adobe Commerce UI-komponenter)**—Adobe Commerce/PHP-specialister bygger vidare på äldre butiker.

Låt oss börja med den mer välbekanta arkitekturen för butiker innan vi kommer in i headless. Om headless är frikopplat är detta den kopplade storefront-arkitekturen, som oftast ses med våra Luma-demos.

Det är här som butiksfunktionerna är nära integrerade med de centrala e-handelstjänsterna, som inte avgränsas av GraphQL API-lager. Så det finns en hel del affärslogik kopplad till det temat. Det här tillvägagångssättet är inte headless, och det är inte PWA.

Det här är för närvarande det vanligaste alternativet som handlare använder eftersom det har 100 % funktionsstöd med funktioner för både B2B- och B2C-handel. Den är välbekant, det finns ett välutvecklat ekosystem av expertkunskaper kring den och den är i stort sett kompatibel med Adobe Commerce Marketplace-tillägg.

Det saknar dock de fördelar som vi talade om tidigare. Utan att separera lager finns det många beroenden och potentiella felpunkter när ändringar görs. Det är inte lika bra som ett välimplementerat PWA, och om en handlare inte har expertis inom Adobe Commerce eller PHP-utveckling måste de hitta de resurserna.
