---
title: Bästa metoder för allmän utveckling
description: Läs mer om hur man utvecklar Adobe Commerce-projekt på bästa sätt.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# Bästa praxis för utveckling av Adobe Commerce

I det här avsnittet beskrivs baslinjen för en sund Adobe Commerce-utvecklingsprocess. Här beskrivs grundläggande processer, kodningsprinciper och principer för programdesign som vägleder utvecklarna.

>[!NOTE]
>
>Adobe tekniska arkitekter använder dessa bästa metoder som referens vid utvecklingsarbete.

Dessa bästa metoder har utvecklats utifrån många års erfarenhet av att utveckla och leverera handelsprojekt. Adobe rekommenderar att de tekniska initiativen följer dessa bästa metoder och att ni förbättrar befintliga processer och kod så att de passar dem.

## Textkonventioner

Nyckelorden &quot;MUST&quot;, &quot;MUST NOT&quot;, &quot;REQUI&quot;, &quot;SHALL&quot;, &quot;SHOULD&quot;, &quot;SHOULD&quot;, &quot;SHOULD NOT&quot;, &quot;REKOMMENDED&quot;, &quot;MAY&quot; och &quot;OPTIONAL&quot; i detta ämne skall tolkas enligt beskrivningen i [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

## Process

1. En definierad projektmetod MÅSTE överenskommas innan projektverksamheterna inleds. Det kan vara Scrum, Waterfall eller någon annan metod eller kombination av metoder, så länge som det definieras.
1. Utvecklingen bör INTE börja förrän utvecklingsteamet har tillgång till en förgreningsstrategi för versionskontrollsystemet.
1. Utvecklingen BÖR INTE börja förrän vi har godkänt tekniska specifikationer, godkänt användarberättelser och användningsexempel och godkänt testfall är tillgängliga för utvecklingsgruppen.
1. Utveckling BÖR INTE påbörjas förrän minst en utvecklings- och QA-miljö finns tillgänglig.
1. Projektspecifika krav som är obligatoriska för utveckling att starta kan dokumenteras i en _Definition av klar_.
1. Godkännande BÖR utföras av en kundrepresentant som är behörig att underteckna på projektprodukter.
1. I Agile-projektmetoder kan ytterligare krav uppfyllas efter signeringen. Dessa krav bör behandlas som nya krav och bör hämtas, konstrueras och planeras i enlighet med detta.
1. All utveckling MÅSTE funktionstestas av utvecklaren innan den skickas in.
1. All utveckling bör klara automatiska tester innan den skickas in för kodgranskning. Detta kan konfigureras som en automatiserad process efter att en pull-begäran har skapats.
1. All utveckling MÅSTE genomgå manuell kodgranskning av en teknisk arkitekt eller Lead Developer innan den skickas in för kvalitetssäkring.
1. All utveckling MÅSTE ge kvalitetssäkring innan den levereras till kunden.
1. Projektspecifika krav som är obligatoriska för leverans kan dokumenteras i en &quot;Definition av Klar&quot;.

## Miljö

1. Alla utvecklare BÖR använda samma utvecklingsmiljö. PhpStorm rekommenderas för utveckling av Adobe Commerce.
1. Alla utvecklare BÖR utveckla och testa med samma teknologi som används på (framtida) produktionsservrar. Versionerna av programvaran i denna teknologi MÅSTE matcha den större och mindre versionen av programvaran som är installerad på produktionsservrarna. Se [systemkrav](../../../installation/system-requirements.md) om du vill ha information om den typiska teknikhögen för Adobe Commerce.
1. Systemadministratören eller den tekniska arkitekten får förse teamet med en centralt underhållen lokal utvecklingsmiljö för att säkerställa och främja likartade och aktuella lokala miljöer.
1. Utvecklare och QA-tekniker MÅSTE ha tillgång till kommandoraden, databasen och loggfilerna för QA-miljön. Detta kan kräva en VPN-anslutning.

## Kodstandarder

1. All kod ska följa konventionerna om arkitektur, metoder och kodningsstandarder. Kreativitet önskas i funktion, inte i form.
1. All kod SKA vara i linje med [Adobe Commerce Architecture Guide](https://developer.adobe.com/commerce/php/architecture/){target="_blank}.
1. All kod SKA följa [Adobe Commerce Coding Standards](https://developer.adobe.com/commerce/php/coding-standards/).
1. All kod SKA följa [Adobe Commerce tekniska riktlinjer](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).
1. All kod SKA implementera [Adobe Commerce bästa praxis](../phases.md), om tillämpligt.
1. All kod SKA följa [PHP-Framework Interoperability Group-standarder (FIG)](https://www.php-fig.org/).
1. Där det är möjligt rekommenderas att man [Adobe Commerce Technical Visions](https://developer.adobe.com/commerce/php/architecture/technical-vision/) med hänsyn till.
1. Alla integreringar med externa system BÖR ha integrationstester som validerar affärsprocessen.
1. Alla moduler SKA ha testtäckning. Hur man testar exakt bör bestämmas av utvecklingsteamet i samarbete med den tekniska arkitekten eller den ledande utvecklaren. Detta fastställande bör bygga på kvalitativa åtgärder och inte på kvantitativa åtgärder. En hög kodsatser är inte en indikator på framgång och inte heller en hög kodkvalitet. I stället fastställa risken för att inte täcka en del av koden genom att bedöma sannolikheten för och svårighetsgraden av regressioner i den delen av programmet.

## Versioner

Modulversionerna MÅSTE följa [Semantic Versioning 2.0.0 Standard](https://semver.org/).
Beroenden av Adobe Commerce-kodbas BÖR följa [Riktlinjer för beroende av modulversion](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

## REVISIONSKONTROLL

Åtagandena MÅSTE åtföljas av meningsfulla bekräftelsemeddelanden.

## Säkerhet

1. [Icke-säkra funktioner](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) SKA INTE ANVÄNDAS.
1. [XSS-förebyggande strategier](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) BÖR ANVÄNDAS.
1. [Skyddsprofiler för innehåll](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) BÖR ANVÄNDAS.
1. Nya Adobe Commerce-instanser bör levereras den senaste säkerhetsutgåvan av en version som ännu inte har nått datumet&quot;Slutet av säkerhetskorrigeringen&quot;. Se [Adobe Commerce Software Lifecycle Policy](../../../release/lifecycle-policy.md).
