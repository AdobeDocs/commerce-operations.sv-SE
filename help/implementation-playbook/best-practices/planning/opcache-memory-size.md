---
title: Bästa praxis för OPcache-minnesstorlek
description: Beskriver hur du undviker prestandaförsämringar genom särskilda inställningar för OPcache-minnesförbrukning i Adobe Commerce-projekt.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 6c0a9268cb3a3b2e76f4a389846e8407f0893b4f
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Bästa sättet att hantera OPcache-minnesstorlek i Adobe Commerce

För Adobe Commerce i molninfrastruktur rekommenderas Pro-planarkitekturen 2.3.x att ställa in `opcache.memory_consumption` på minst 2 GB för att undvika prestandaförsämringar.

## Berörda produkter och versioner

* Adobe Commerce on cloud infrastructure Pro plan architecture 2.3.x
* PHP 7.0 och senare

## Konfigurera minne

Allokera minst **2 GB** minne för PHP-modulen [OPcache](https://www.php.net/manual/en/book.opcache.php). OPcache-modulen är konfigurerad i filen `php.ini`. Om du vill allokera 2 048 MB minne anger du `opcache.memory_consumption = 2048`.

## Ytterligare information

* [Bästa praxis för prestanda - PHP-inställningar](../../../performance/software.md#php-settings)
* [Konfigurera PHP-alternativ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/configure-app-yaml)
* [Bästa databaspraxis för Adobe Commerce om molninfrastruktur](database-on-cloud.md)
* [De vanligaste databasproblemen i Adobe Commerce om molninfrastruktur](../maintenance/resolve-database-performance-issues.md)
* [Indexerare&quot;Update On Schedule&quot; optimerar Adobe Commerce prestanda](../maintenance/indexer-configuration.md)
