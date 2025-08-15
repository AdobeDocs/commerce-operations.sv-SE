---
title: Implementeringsunderhållsfas
description: Lär dig mer om de effektivaste strategierna för implementering i underhållsfasen av Adobe Commerce-projekt.
exl-id: bd052412-a41c-4dbd-9aba-ba2fcac31f2d
feature: Best Practices
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# Underhållsfas

Underhållsfasen omfattar följande verksamheter:

- Felkorrigering
- Kataloghantering
- Konfiguration
- Förbättrade funktioner
- Indexering
- Managed Services
- Platsövervakning
- Uppgraderingar

Följande avsnitt innehåller information om bästa praxis för underhållsfasen.

## Felkorrigeringar

| Bästa praxis | Beskrivning |
|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| [[!DNL Quality Patches Tool] användning](../../../tools/quality-patches-tool/usage.md) | Använd, ångra och visa allmän information om alla Adobe Commerce-patchar. |

## Kataloghantering

| Bästa praxis | Beskrivning |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| [Hantering av produktkataloger](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/2eea2782fc874047a020391000519f8b/watch?source=CHANNEL) | Commerce &amp; Coffee-inspelning som beskriver strategier för hantering av produktkataloger. |

## Konfiguration

| Bästa praxis | Beskrivning |
|-------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| [Schemalägger administratörsuppdateringar på produktionsplatser](scheduling-admin-updates-in-production.md) | Hantera viktiga Adobe Commerce-uppdateringar för att förhindra långsamma prestanda och driftavbrott. |

## Databashantering

| Bästa praxis | Beskrivning |
|--------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| [Åtgärda databasprestandaproblem &#x200B;](resolve-database-performance-issues.md) | Åtgärda databasproblem som försämrar prestandan på Adobe Commerce webbplatser som körs i molninfrastrukturen. |
| [Adobe Commerce uppgraderingskrav för MariaDB &#x200B;](mariadb-upgrade.md) | Förbered din MariaDB-databas för en uppgradering. |

## Förbättrade funktioner

| Bästa praxis | Beskrivning |
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| [Personalization](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/e218545a77de490fb5102eca07d0580a/watch?source=CHANNEL) | Commerce &amp; Coffee-inspelning som beskriver personaliseringsstrategier. |
| [E-Commerce Trends](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/9a772468d7b64409a3d5dff4d67e656d/watch?source=CHANNEL) | Inspelning av Commerce och kaffe som beskriver e-handelstrender. |
| [AI-automatisering](https://www.gotostage.com/channel/fca90f7960be436f9b849215d9e06026/recording/27ae23699c2847be981a23ca098e548f/watch?source=CHANNEL) | Commerce &amp; Coffee-inspelning som beskriver personaliseringsmöjligheterna med artificiell intelligens och automatisering. |

## Indexering

| Bästa praxis | Beskrivning |
|------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| [Indexera om](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex) | Använd cron-jobb eller CLI-verktyget för att köra omindexering. |
| [Konfigurera indexerare &#x200B;](indexer-configuration.md) | Optimera webbplatsens prestanda genom att följa vedertagna standarder för indexerarkonfiguration. |
| [Beställningsbearbetning](order-processing-configuration.md) | Förbättra utcheckningen och beställningsprocessernas prestanda. |

## Platsövervakning och -säkerhet

| Bästa praxis | Beskrivning |
|-------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [Granska klientprestanda](frontend-performance.md) | Identifiera och åtgärda problem som negativt påverkar webbplatsens prestanda genom att använda verktyg för webbprestanda. |
| [Klar, uppsättning, underhåll](https://business.adobe.com/blog/basics/ready-set-maintain) | Tips för att underhålla dina Adobe Commerce-sajter för att maximera affärsvärdet och drifttiden. |
| [Använd  [!DNL Site-Wide Analysis Tool]](../../../tools/site-wide-analysis-tool/intro.md#integrations-with-other-adobe-commerce-support-tools) | Se viktiga insikter om Adobe Commerce webbplats på ett och samma ställe. |
| [Övervaka prestanda, diskutrymme och loggar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html?lang=sv-SE) | Använd New Relic för att övervaka viktiga prestandainsikter om Adobe Commerce på molninfrastruktursajten. |
| [Svara på säkerhetsincidenter](respond-to-security-incident.md) | Använd New Relic för att övervaka viktiga prestandainsikter om Adobe Commerce på molninfrastruktursajten. |

### Uppgraderingar

| Bästa praxis | Beskrivning |
|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| [Lappa i skala](patching-at-scale.md) | Se hur centraliserad patchning för Adobe Commerce kan hjälpa er att hantera företagsprojekt. |
| [Uppdatera tjänster och komponenter till den senaste versionen &#x200B;](update-services.md) | håller din Adobe Commerce i molninfrastruktur uppdaterad. |
| [Upgrade checklist for Adobe Commerce &#x200B;](upgrade-checklist.md) | Skapa och använd en checklista för uppgradering för att planera din Adobe Commerce uppgraderingsstrategi. |
