---
title: Cachestorlek för Realpath
description: Lär dig hur du optimerar Adobe Commerce prestanda genom att uppdatera konfigurationen av PHP-lässökvägscachen så att den använder de rekommenderade inställningarna.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Bästa praxis för konfiguration av Realpath-cache

Realpath-cache cachelagrar de verkliga filsystemsökvägarna för filnamn som refereras i stället för att leta upp dem varje gång. Varje gång olika filfunktioner utförs eller kräver en fil och använder en relativ sökväg, måste PHP leta upp var filen verkligen finns.

Använd följande rekommenderade inställningar för att konfigurera `realpath_cache` inställningarna i `php.ini` fil:

- Ställ in cachestorleken till 10 MB (`realpath cache_size=10M`)
- Ställ in tiden till live (ttl) till 7 200 sekunder (`realpath_cache_ttl=7200`)

Konfigurationsanvisningar finns i [Ange PHP-alternativ](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## Berörda produkter och versioner

- Adobe Commerce lokalt, alla versioner 2.3.x och senare
- Adobe Commerce om molninfrastruktur, alla versioner 2.3.x och senare

## Potentiell inverkan på prestanda

Om konfigurationsvärdena för Realpath-cachen är för låga eller för höga läggs extra overhead till under cachegenereringen, vilket försämrar prestandan.

## Ytterligare information

- [Lokalt: PHP-inställningar](../../../performance/software.md#php-settings)
- I molninfrastruktur:
   - [Bästa praxis för databaser](database-on-cloud.md)
   - [De vanligaste databasproblemen i Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [Indexerare&quot;Update On Schedule&quot; optimerar Magento prestanda](../maintenance/indexer-configuration.md)

