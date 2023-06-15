---
title: Migrera från Elasticsearch till OpenSearch
description: Lär dig hur du ersätter sökmotorn som används för lokala installationer av Adobe Commerce och Magento Open Source.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Migrerar till OpenSearch

OpenSearch är en öppen källkodsgaffel i Elasticsearch 7.10.2 som skapades efter att Elasticsearch ändrat licensvillkoren.

Från och med 2.4.4, 2.4.3-p2 och 2.3.7-p3 stöder Adobe Commerce och Magento Open Source OpenSearch. Lokala installationer har fortsatt stöd för Elasticsearch, även om det inte längre stöds för Adobe Commerce i molninfrastruktur. Från och med version 2.4.6 har OpenSearch en egen modul och egna fält i konfigurationsinställningarna för Admin.

## Migreringssökväg

Stegen för att migrera till OpenSearch är enkla och följer i stort sett stegen för konfiguration av Elasticsearch. I dessa steg antas att Adobe Commerce är det enda programmet som använder sökmotorn. Om flera program använder sökmotorn följer du den officiella migreringsguiden [Gå från Elasticsearch med öppen källkod till OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Kontrollera att installationen uppfyller [krav för sökmotor](../../installation/prerequisites/search-engine/overview.md).

1. Placera platsen i [Underhållsläge](../../installation/tutorials/maintenance-mode.md).

1. Du kan även avinstallera Elasticsearch.

1. [Installera OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Konfigurera sökmotorn](../../configuration/search/configure-search-engine.md) och utföra relaterade uppgifter, till exempel tömma cachen och indexera om katalogsökindexet.

Inga ytterligare ändringar av konfigurationsvärdet behövs.
