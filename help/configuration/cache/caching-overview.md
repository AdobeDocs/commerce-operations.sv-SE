---
title: Konfigurera cachelagring
description: Lär dig mer om cachningsmekanismer och konfigurationsalternativ för Adobe Commerce-program. Upptäck alternativ till standardcachelagring av filsystem.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Konfigurera cachelagring

Med [!DNL Commerce] kan du konfigurera alternativ till standardfilsystemets cachelagring. I den här guiden diskuteras några av dessa alternativ, nämligen

- Ställ in följande cachemekanismer i konfigurationen [!DNL Commerce]:

   - [Databas](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Filsystem (standard): Ingen konfiguration behövs för att använda standardfilsystemets cachelagring.

- Konfigurera [lack](config-varnish.md) utan att ändra [!DNL Commerce]-konfigurationen.

## Cachelagring av terminologi

[!DNL Commerce] använder följande cachelagringsterminologi:

- **Frontend** - Liknar ett gränssnitt eller en gateway för cache-lagring, som implementeras av [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Cachetyper** - Kan vara någon av typerna i [!DNL Commerce] eller så kan du [skapa egna](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Backend** - Anger information om [cache-lagring](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) som implementeras av [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Backend på två nivåer** - Lagrar cacheposter i två backends: en snabbare och en långsammare.

  >[!INFO]
  >
  >Konfiguration av serverdelscache på två nivåer ligger utanför den här guidens omfång.

## Konfigurationsalternativ

- Ändrar angiven `default`-cacheklientstruktur—

  Du ändrar bara filen `<magento_root>/app/etc/di.xml`, Commerce-programmets globala konfiguration för beroendeinjicering.

- Konfigurera en egen anpassad cacheklientserver -

  Du ändrar bara filen `<magento_root>/app/etc/env.php` eftersom den åsidosätter motsvarande konfiguration i filen `di.xml`.

>[!TIP]
>
>För lack krävs inga ändringar av konfigurationen [!DNL Commerce]. Se [Konfigurera och använda engelska](config-varnish.md).
