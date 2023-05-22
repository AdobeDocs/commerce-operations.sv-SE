---
title: Konfigurera cachelagring
description: Lär dig mer om cachelagring och hur du konfigurerar cachemekanismer för Adobe Commerce och Magento Open Source.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Konfigurera cachelagring

[!DNL Commerce] I kan du konfigurera alternativ till standardfilsystemets cachning. I den här guiden diskuteras några av dessa alternativ. ,

- Ställ in följande cacheminnesmekanismer i [!DNL Commerce] konfiguration:

   - [Databas](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Filsystem (standard): Ingen konfiguration krävs för att använda standardfilsystemets cachelagring.

- Konfigurera [Varnish](config-varnish.md) utan att ändra [!DNL Commerce] konfiguration.

## Cachelagring av terminologi

[!DNL Commerce] använder följande cachelagringsterminologi:

- **Frontend**- Liknar ett gränssnitt eller en gateway för cachelagring, implementerat av [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Cachetyper**—Kan vara någon av typerna i [!DNL Commerce] eller du kan [skapa egna](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Backend**—Anger information om [cache-lagring](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementerat av [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Backend på två nivåer**—Lagrar cacheposter i två bakgrunder: en snabbare och långsammare en.

   >[!INFO]
   >
   >Konfiguration av serverdelscache på två nivåer ligger utanför den här guidens omfång.

## Konfigurationsalternativ

- Ändra angiven `default` cachefrontend—

   Du ändrar bara `<magento_root>/app/etc/di.xml` -filen, Commerce-programmets globala beroendeinjektionskonfiguration.

- Konfigurera en egen anpassad cacheklientserver -

   Du ändrar bara `<magento_root>/app/etc/env.php` eftersom den åsidosätter motsvarande konfiguration i `di.xml` -fil.

>[!TIP]
>
>På engelska krävs inga ändringar i [!DNL Commerce] konfiguration. Se [Konfigurera och använda engelska](config-varnish.md).
