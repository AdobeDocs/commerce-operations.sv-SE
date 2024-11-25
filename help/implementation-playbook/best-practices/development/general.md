---
title: Bästa metoder för allmän utveckling
description: Läs mer om hur man utvecklar Adobe Commerce-projekt på bästa sätt.
feature: Best Practices
role: Developer
exl-id: 35de9849-2d19-4bb6-b920-9ce3838bc8bc
source-git-commit: 68dc4635df9fc411925fe0d48a578edece8895dc
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Bästa praxis för utveckling av Adobe Commerce

I det här avsnittet beskrivs baslinjen för en sund Adobe Commerce-utvecklingsprocess. Här beskrivs grundläggande processer, kodningsprinciper och principer för programdesign som vägleder utvecklarna.

>[!NOTE]
>
>Adobe tekniska arkitekter använder dessa bästa metoder som referens vid utvecklingsarbete.

Dessa metodtips har utvecklats baserat på många års erfarenhet av att utveckla och leverera Commerce-projekt. Adobe rekommenderar att de tekniska initiativen följer dessa bästa metoder och att ni förbättrar befintliga processer och kod så att de passar dem.

## Textkonventioner

Nyckelorden &quot;MUST&quot;, &quot;MUST NOT&quot;, &quot;REQUIRED&quot;, &quot;SHALL&quot;, &quot;SHOULD&quot;, &quot;SHOULD&quot;, &quot;SHOULD NOT&quot;, &quot;REKOMMENDED&quot;, &quot;MAY&quot; och &quot;OPTIONAL&quot; i detta ämne ska tolkas enligt beskrivningen i [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

## Process

1. En definierad projektmetod MÅSTE överenskommas innan projektverksamheterna inleds. Det kan vara Scrum, Waterfall eller någon annan metod eller kombination av metoder, så länge som det definieras.
1. Utvecklingen bör INTE börja förrän utvecklingsteamet har tillgång till en förgreningsstrategi för versionskontrollsystemet.
1. Utvecklingen BÖR INTE börja förrän vi har godkänt tekniska specifikationer, godkänt användarberättelser och användningsexempel och godkänt testfall är tillgängliga för utvecklingsgruppen.
1. Utveckling BÖR INTE påbörjas förrän minst en utvecklings- och QA-miljö finns tillgänglig.
1. Projektspecifika krav som är obligatoriska för utveckling att starta kan dokumenteras i en _definition av Ready_.
1. Godkännande BÖR utföras av en kundrepresentant som är behörig att underteckna på projektprodukter.
1. I Agile-projektmetoder kan ytterligare krav uppfyllas efter signeringen. Dessa krav bör behandlas som nya krav och bör hämtas, konstrueras och planeras i enlighet med detta.
1. All utveckling MÅSTE funktionstestas av utvecklaren innan den skickas in.
1. All utveckling bör klara automatiska tester innan den skickas in för kodgranskning. Detta kan konfigureras som en automatiserad process efter att en pull-begäran har skapats.
1. All utveckling MÅSTE genomgå manuell kodgranskning av en teknisk arkitekt eller Lead Developer innan den skickas in för kvalitetssäkring.
1. All utveckling MÅSTE ge kvalitetssäkring innan den levereras till kunden.
1. Projektspecifika krav som är obligatoriska för leverans kan dokumenteras i en &quot;Definition av Klar&quot;.

## Miljö

1. Alla utvecklare BÖR använda samma utvecklingsmiljö. PhpStorm rekommenderas för utveckling av Adobe Commerce.
1. Alla utvecklare BÖR utveckla och testa med samma teknologi som används på (framtida) produktionsservrar. Versionerna av programvaran i denna teknologi MÅSTE matcha den större och mindre versionen av programvaran som är installerad på produktionsservrarna. Mer information om den typiska teknikstacken för Adobe Commerce finns i [systemkraven](../../../installation/system-requirements.md).
1. Systemadministratören eller den tekniska arkitekten får förse teamet med en centralt underhållen lokal utvecklingsmiljö för att säkerställa och främja likartade och aktuella lokala miljöer.
1. Utvecklare och QA-tekniker MÅSTE ha tillgång till kommandoraden, databasen och loggfilerna för QA-miljön. Detta kan kräva en VPN-anslutning.

## Versioner

Modulversionerna MÅSTE följa standarden [Semantic Versioning 2.0.0](https://semver.org/).
Beroenden för Adobe Commerce-kodbasen BÖR följa riktlinjerna för [beroende av modulversioner](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

## REVISIONSKONTROLL

Åtagandena MÅSTE åtföljas av meningsfulla bekräftelsemeddelanden.

## Säkerhet

1. [Osäkra funktioner](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) FÅR INTE användas.
1. [XSS-prevent-strategier](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) SKA användas.
1. [Skyddsprofiler för innehåll](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) SKA tillämpas.
1. Nya Adobe Commerce-instanser bör levereras den senaste säkerhetsutgåvan av en version som ännu inte har nått datumet&quot;Slutet av säkerhetskorrigeringen&quot;. Se [Adobe Commerce livscykelpolicy för programvara](../../../release/lifecycle-policy.md).
