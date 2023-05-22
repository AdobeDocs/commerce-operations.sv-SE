---
title: Cachealternativ
description: Konfigurera åtkomst till cachelagring på låg nivå.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Cachealternativ på låg nivå

I Commerce-programmet används en cacheklientdel och serverdel på låg nivå för att ge åtkomst till cachelagringen.

## Lättnivåcache för klientservrar

Commerce extends [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) genom att implementera [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) klientcache.

## Serverdelscache på låg nivå

I allmänhet fungerar Commerce-programmet med alla serverdelscache som [Zend_Cache Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) stöder. Den här guiden täcker dock endast följande backend-cacheminnen på låg nivå:

- [Redis](config-redis.md)
- [Databas](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Filsystem (standard): Ingen konfiguration krävs för att använda filsystemets cachelagring.

[Varnish](config-varnish.md) kräver inte att en cachebackend på låg nivå ställs in.
