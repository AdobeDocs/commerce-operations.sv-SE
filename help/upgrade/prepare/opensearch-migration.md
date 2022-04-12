---
title: Migrera från Elasticsearch till OpenSearch
description: Lär dig hur du ersätter sökmotorn som används för lokala installationer av Adobe Commerce och Magento Open Source.
source-git-commit: 8007ff2e77689ec2058a326924dc34b8d91ee570
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# Migrerar till OpenSearch

OpenSearch är en öppen källkodsgaffel i Elasticsearch 7.10.2 som skapades efter att Elasticsearch ändrat licensvillkoren.

Från och med 2.4.4, 2.4.3-p2 och 2.3.7-p3 stöder Adobe Commerce och Magento Open Source OpenSearch. Lokala installationer har fortsatt stöd för Elasticsearch, även om det inte längre stöds för Adobe Commerce i molninfrastruktur.

## Migreringssökväg

Stegen för att migrera till OpenSearch är enkla och följer i stort sett stegen för konfiguration av Elasticsearch. I dessa steg antas att Adobe Commerce är det enda programmet som använder sökmotorn. Om flera program använder sökmotorn följer du den officiella migreringsguiden [Gå från Elasticsearch med öppen källkod till OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Kontrollera att installationen uppfyller [krav för sökmotor](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html).

1. Placera platsen i [Underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. Du kan även avinstallera Elasticsearch.

1. [Installera OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Konfigurera sökmotorn](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) och utföra relaterade uppgifter, till exempel tömma cachen och indexera om katalogsökindexet.

Inga ytterligare ändringar av konfigurationsvärdet behövs.
