---
title: Bästa tillvägagångssätt för att konfigurera webbplatser, butiker och butiksvyer
description: Lär dig de bästa sätten att konfigurera webbplatser, butiker och butiksvyn för att maximera webbplatsens prestanda.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# Bästa tillvägagångssätt för att konfigurera webbplatser, butiker och butiksvy

För bästa webbplatsprestanda kan du konfigurera högst 50 webbplatser, 50 butiker och 50 butiksvyer för Adobe Commerce i molninfrastrukturprojekt.

>[!NOTE]
>
>För Adobe Commerce i molninfrastruktur gäller de bästa metoderna specifikt för produktionsmiljön (och eventuellt för Stage i Pro-arkitekturen, med förbehåll för resursbegränsningar) som skulle ha mer resurser än för integrering och utveckling. För integrerings- (Pro och Starter) och mellanlagringsmiljöer (Starter) kan du minska antalet butiksvyer till mindre än 5 eller 10 (med reservation för teknisk granskning).

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Strategier för att förbättra resultaten

Om ditt projekt kräver många webbplatser, butiker eller butiksvyer kan du förbättra prestanda med följande strategier:

- Strukturera om katalogen genom att byta logik till kategorier
- Skilj prislistor från katalogdata med hjälp av externa priser och ett prishanteringssystem (PMS).
- Använd en alternativ noSQL-datalagring som Elasticsearch

## Potentiella resultateffekter

Webbplatser och butiker är multipler för katalogdata, så om du har många webbplatser och butiker kan det påverka webbplatsens prestanda negativt på följande sätt:

- Större indextabeller ökar den tid som krävs för att slutföra indexeringsåtgärder [Prisindex].
- Ökad tid för hämtning av programkonfiguration försämrar svarstiden för butiker för icke-cachelagrade katalogsidor.
- Avsevärt längre tid än vad som krävs för att slutföra Spara-åtgärder i Admin eftersom data sparas separat för varje webbplats.


## Ytterligare information

- [Förstå webbplatser, butiker och butiksvyer](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Konfigurera flera webbplatser eller butiker](https://devdocs.magento.com/cloud/project/project-multi-sites.html)

