---
title: Migrera från Elasticsearch till OpenSearch
description: Lär dig hur du ersätter sökmotorn som används för lokala installationer av Adobe Commerce.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 54aef3d7db7b8333721fb56db0ba8f098aea030b
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Migrerar till OpenSearch

OpenSearch är en öppen källkodsgaffel till Elasticsearch 7.10.2 som skapades efter att Elasticsearch har ändrat licensvillkoren.

Från och med 2.4.4, 2.4.3-p2 och 2.3.7-p3 stöder Adobe Commerce OpenSearch. Lokala installationer har fortsatt stöd för Elasticsearch, även om det inte längre stöds för Adobe Commerce i molninfrastrukturen. Från och med version 2.4.6 har OpenSearch en egen modul och egna fält i konfigurationsinställningarna för Admin.

## Migreringssökväg

Stegen för att migrera till OpenSearch är enkla och följer i stort sett stegen för konfiguration av Elasticsearch. I dessa steg antas att Adobe Commerce är det enda programmet som använder sökmotorn. Om flera program använder sökmotorn följer du den officiella migreringsguiden [Flytta från Elasticsearch med öppen källkod till OpenSearch](https://opensearch.org/blog/moving-from-opensource-elasticsearch-to-opensearch/).

1. Kontrollera att installationen uppfyller kraven för [sökmotorn](../../installation/prerequisites/search-engine/overview.md).

1. Placera platsen i [underhållsläge](../../installation/tutorials/maintenance-mode.md).

1. Du kan även avinstallera Elasticsearch.

1. [Installera OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Konfigurera sökmotorn &#x200B;](../../configuration/search/configure-search-engine.md) och utför relaterade åtgärder, till exempel tömning av cachen och omindexering av katalogsökindexet.

Inga ytterligare ändringar av konfigurationsvärdet behövs.
