---
title: Konfigurera cachelagring
description: Lär dig mer om cachelagring och hur du konfigurerar cachemekanismer för Adobe Commerce och Magento Open Source.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Konfigurera cachelagring

[!DNL Commerce] I kan du konfigurera alternativ till standardfilsystemets cachning. I den här guiden diskuteras några av dessa alternativ. ,

- Ställ in följande [cache](https://glossary.magento.com/cache) i [!DNL Commerce] konfiguration:

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

   Du ändrar bara `<magento_root>/app/etc/di.xml` -fil, Commerce-programmets globala [beroendeinjektion](https://glossary.magento.com/dependency-injection) konfiguration.

- Konfigurera en egen anpassad cacheklientserver -

   Du ändrar bara `<magento_root>/app/etc/env.php` eftersom den åsidosätter motsvarande konfiguration i `di.xml` -fil.

>[!TIP]
>
>På engelska krävs inga ändringar i [!DNL Commerce] konfiguration. Se [Konfigurera och använda engelska](config-varnish.md).
