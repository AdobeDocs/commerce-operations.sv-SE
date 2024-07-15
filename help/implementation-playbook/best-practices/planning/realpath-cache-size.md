---
title: Cachestorlek för Realpath
description: Lär dig hur du optimerar Adobe Commerce prestanda genom att uppdatera konfigurationen av PHP-lässökvägscachen så att den använder de rekommenderade inställningarna.
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# Bästa praxis för konfiguration av Realpath-cache

Realpath-cache cachelagrar de verkliga filsystemsökvägarna för filnamn som refereras i stället för att leta upp dem varje gång. Varje gång olika filfunktioner utförs eller kräver en fil och använder en relativ sökväg, måste PHP leta upp var filen verkligen finns.

Använd följande rekommenderade inställningar för att konfigurera inställningarna för `realpath_cache` i filen `php.ini` om du vill förbättra Commerce prestanda:

- Ange cachestorleken till 10 MB (`realpath cache_size=10M`)
- Ställ in tiden till live (ttl) till 7 200 sekunder (`realpath_cache_ttl=7200`)

Konfigurationsanvisningar finns i [Så här anger du PHP-alternativ](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

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
