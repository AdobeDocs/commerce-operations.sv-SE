---
title: Bästa praxis för OPcache-minnesstorlek
description: Beskriver hur du undviker prestandaförsämringar genom särskilda inställningar för OPcache-minnesförbrukning i Adobe Commerce-projekt.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# Bästa sättet att hantera OPcache-minnesstorlek i Adobe Commerce

För Adobe Commerce on cloud infrastructure Pro rekommenderas arkitektur 2.3.x `opcache.memory_consumption` till minst 2 GB för att undvika prestandaförsämringar.

## Berörda produkter och versioner

* Adobe Commerce on cloud infrastructure Pro plan architecture 2.3.x
* PHP 7.0 och senare

## Konfigurera minne

Allokera minst **2 GB** av minnet för [PHP-modul för OPcache](https://www.php.net/manual/en/book.opcache.php). OPcache-modulen är konfigurerad i `php.ini` -fil. Om du vill allokera 2 048 MB minne anger du `opcache.memory_consumption = 2048`.

## Ytterligare information

* [Bästa praxis för prestanda - PHP-inställningar](../../../performance/software.md#php-settings)
* [Konfigurera PHP-alternativ](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [Bästa databaspraxis för Adobe Commerce om molninfrastruktur](database-on-cloud.md)
* [De vanligaste databasproblemen i Adobe Commerce om molninfrastruktur](../maintenance/resolve-database-performance-issues.md)
* [Indexerare&quot;Update On Schedule&quot; optimerar Adobe Commerce prestanda](../maintenance/indexer-configuration.md)
