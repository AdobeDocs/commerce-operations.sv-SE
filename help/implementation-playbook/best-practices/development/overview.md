---
title: Implementeringsutvecklingsfas
description: Lär dig mer om de effektivaste strategierna för implementering i utvecklingsfasen av Adobe Commerce-projekt.
exl-id: 499c16df-0e4d-4950-8169-96356bdff1a7
feature: Best Practices
role: Developer
source-git-commit: cca301a72b972d843b878fae28901a47c8fc0489
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# Utvecklingsfas

Utvecklingsfasen omfattar följande verksamheter:

- Lokal konfiguration och mellanlagringsmiljö
- Sprint-planering
- Biljettkörning
- Felsökning
- Granska, sammanfoga och testa kod
- Sprint-granskning
- Kundens godkännande

>[!TIP]
>
>Se [allmän bästa praxis](general.md) för rekommendationer på hög nivå om övergripande hantering av utvecklingsprocessen.

Följande avsnitt innehåller information om bästa praxis för utvecklingsfasen.

## Kodhantering

| Bästa praxis | Beskrivning |
|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| [Kodgranskning](code-review.md) | Rekommenderad valideringsprocess för att säkerställa att den implementerade funktionen uppfyller kraven |
| [Disposition jämfört med Git](code-management.md) | Bestäm hur anpassad kod ska distribueras med hänsyn till versionshantering, komplexitet i kod och beroendehantering |
| [Förgreningsstrategi](git-branching.md) | Hantera källkod i Git-databaser |

## Plattform och tjänster

| Bästa praxis | Beskrivning |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [Skapar och distribuerar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html?lang=sv-SE){target="_blank"} | Beskriver de bästa sätten att skapa och distribuera Adobe Commerce-faser i molninfrastrukturprojekt |
| Felsökning | Systematisk och effektiv felsökning av Adobe Commerce-ramverket |
| [Statisk innehållsdistribution](static-content-deployment.md) | Undvik problem med statiskt innehåll som inte visas i butiken |
| [Felsökning](troubleshooting.md) | Felsöka vanliga problem med Adobe Commerce-implementering |

## Databas

| Bästa praxis | Beskrivning |
|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| [Tabelländring](modifying-core-and-third-party-tables.md) | Bestäm hur och när databastabeller från Adobe Commerce och tredje part ska ändras |

## Filoptimering

| Bästa praxis | Beskrivning |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [Storleksändring av katalogbild](catalog-image-resizing.md) | Tillhandahåller vägledning om storleksändring av bilder innan en butik går till produktion för att säkerställa optimala prestanda |
| [CSS och JS](optimize-css-js-files.md) | Sammanfoga och miniatyrbilder av CSS- och JavaScript-filer (JS) från Admin eller kommandoraden |
| [Bilder](image-optimization.md) | Optimera bilder och använd snabbt för att optimera svarstiden |

## Framtidsutveckling

| Bästa praxis | Beskrivning |
|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| [Temautveckling](https://developer.adobe.com/commerce/frontend-core/guide/best-practices/){target="_blank"} | Beskriver utvecklingsmönster för att säkerställa kompatibilitet mellan ditt tema, framtida versioner av Adobe Commerce och anpassade tillägg |

## PHP-utveckling

| Bästa praxis | Beskrivning |
|-----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| [Undantagshantering](exception-handling.md) | Beskriver rekommenderade metoder för att logga undantag |
| [Tillägg](https://developer.adobe.com/commerce/php/best-practices/){target="_blank"} | Beskriver utvecklingsmönster för att säkerställa kompatibilitet mellan ditt tillägg, framtida versioner av Adobe Commerce och andra anpassade tillägg |
| [Privata innehållsblock](private-content-block-configuration.md) | Konfigurera privata innehållsblock för att optimera prestanda för butiker |
| [Ändra PHP-kod från kärnan och tredje part](modifying-core-and-third-party-code.md) | Ändra funktionaliteten, resultatet eller indata för kod som du inte har skapat eller inte har direkt kontroll över |
