---
title: Cachealternativ
description: Lär dig mer om cachealternativ på låg nivå och lagringskonfiguration i Adobe Commerce. Upptäck frontend, backend och lagringskonfiguration för Redis och databaser.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 0%

---

# Cachealternativ på låg nivå

Commerce-programmet använder en serverdel med låg cachenivå för att ge åtkomst till cachelagringen.

## Lättnivåcache för klientservrar

Commerce utökar [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) genom att implementera [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)-klientcache.

## Serverdelscache på låg nivå

I allmänhet fungerar Commerce-programmet med alla serverdelscache som stöds av [Zend_Cache Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html). Den här guiden täcker dock endast följande backend-cacheminnen på låg nivå:

- [Redis](config-redis.md)
- [Databas](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Filsystem (standard): Ingen konfiguration behövs för att använda filsystemets cachelagring.

[För lack](config-varnish.md) krävs ingen cachebackend på låg nivå.
