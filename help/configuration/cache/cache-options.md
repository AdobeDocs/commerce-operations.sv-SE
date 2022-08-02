---
title: Cachealternativ
description: Konfigurera åtkomst till cachelagring på låg nivå.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---

# Cachealternativ på låg nivå

I Commerce-programmet används en låg nivå [cache](https://glossary.magento.com/cache) [frontend](https://glossary.magento.com/frontend) och [serverdel](https://glossary.magento.com/backend) för att ge åtkomst till cacheminnet.

## Lättnivåcache för klientservrar

Commerce extends [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) genom att implementera [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) klientcache.

## Serverdelscache på låg nivå

I allmänhet fungerar Commerce-programmet med alla serverdelscache som [Zend_Cache Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) stöder. Den här guiden täcker dock endast följande backend-cacheminnen på låg nivå:

- [Redis](config-redis.md)
- [Databas](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Filsystem (standard): Ingen konfiguration krävs för att använda filsystemets cachelagring.

[Varnish](config-varnish.md) kräver inte att en cachebackend på låg nivå ställs in.
