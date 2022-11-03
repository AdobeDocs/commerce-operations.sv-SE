---
title: Bästa tillvägagångssätt för Redis-tjänstkonfiguration
description: Lär dig hur du förbättrar cachelagringsprestanda med den utökade Redis-cacheimplementeringen för Adobe Commerce 2.3.5.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# Bästa tillvägagångssätt för Redis-tjänstkonfiguration

- För Adobe Commerce 2.3.3 och senare versioner som körs i molninfrastruktur bör du uppgradera till Redis version 5.0.
- För Adobe Commerce version 2.3.5 eller senare använder du den utökade Redis-cacheimplementeringen. Implementeringen innehåller följande optimeringar för att minimera antalet Redis-frågor som utförs på varje begäran från Adobe Commerce:
   - Minska storleken på nätverksdataöverföringar mellan Redis och Adobe Commerce
   - Sänk Redis förbrukning av CPU-cykler genom att förbättra adapterns förmåga att automatiskt avgöra vad som behöver läsas in
   - Minska tävlingsvillkoren för Redis-skrivåtgärder

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur med version 2.3.3 eller senare.
Adobe Commerce (alla distributionsmetoder), version 2.3.5 och senare

## Uppdatera Redis-version för molndistributioner

För Adobe Commerce-installationer på molninfrastruktur med Adobe Commerce 2.3.3 eller senare, uppgradera Redis-tjänsten till Redis version 5.0. Instruktioner finns i följande avsnitt i Adobe Commerce om molninfrastruktur:

- [Konfigurera Redis-tjänsten](https://devdocs.magento.com/cloud/project/services-redis.html)
- [Ändra tjänstversionen](https://devdocs.magento.com/cloud/project/services.html#change-service-version)

## Konfigurera den utökade Redis-cacheimplementeringen

För Adobe Commerce 2.3.5 och senare ska du uppdatera konfigurationen så att den utökade Redis-cacheimplementeringen används `\Magento\Framework\Cache\Backend\Redis`.

### Konfiguration för molndistributioner

Med `ece-tools` 2002.1.1 eller senare konfigurerar du förbättrat Redis-cacheminne genom att ange `REDIS_BACKEND` Distributionsvariabel i miljökonfigurationsfilen. `.magento.env.yaml`

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Mer information finns i [Distribuera variabler > `REDIS_BACKEND`](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend) i dokumentationen för Adobe Commerce om molninfrastruktur.

>[!NOTE]
>
> Kontrollera vilken version av hjälpverktygen som är installerad i den lokala molnmiljön från kommandoraden med hjälp av `composer show magento/ece-tools` -kommando. Vid behov [uppdatera versionen för verktygen](https://devdocs.magento.com/cloud/project/ece-tools-update.html).

### Konfiguration för lokala distributioner

För Adobe Commerce lokala distributioner konfigurerar du den nya Redis-cacheimplementeringen med `bin/magento:setup` kommandon. Instruktioner finns i [Använd Redis för standardcache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Ytterligare information

- [Adobe Commerce Release v2.3.5 - Prestandaförbättringar](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#performance-boosts)
- [Redis Page Cache](../../../configuration/cache/redis-pg-cache.md)


