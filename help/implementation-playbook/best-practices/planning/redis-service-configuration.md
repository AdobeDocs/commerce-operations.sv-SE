---
title: Bästa tillvägagångssätt för Redis-tjänstkonfiguration
description: Lär dig hur du förbättrar cachelagringsprestanda med den utökade Redis-cacheimplementeringen för Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Bästa tillvägagångssätt för Redis-tjänstkonfiguration

- Använd den utökade Redis-cacheimplementeringen, som innehåller följande optimeringar för att minimera antalet Redis-frågor som utförs på varje begäran från Adobe Commerce:
   - Minskar storleken på nätverksdataöverföringar mellan Redis och Adobe Commerce
   - Minskar Redis förbrukning av processorcykler genom att förbättra adapterns förmåga att automatiskt avgöra vad som behöver läsas in
   - Minskar tävlingsvillkoren för Redis-skrivåtgärder
- Separera Redis-cachen från Redis-sessionen
- Komprimera Redis-cachen och använd `gzip` förbättra prestanda

## Utökad Redis-cacheimplementering

Uppdatera konfigurationen så att den utökade Redis-cacheimplementeringen används `\Magento\Framework\Cache\Backend\Redis`.

### Konfigurera molndistributioner

Konfigurera förbättrad Redis-cache genom att ställa in `REDIS_BACKEND` distributionsvariabeln i `.magento.env.yaml` konfigurationsfil.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Mer information finns i [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) variabelbeskrivning i _Handbok för Commerce on Cloud Infrastructure_.

>[!NOTE]
>
> Kontrollera `ece-tools` version som installerats i din lokala miljö från kommandoraden med `composer show magento/ece-tools` -kommando. Vid behov, [uppdatera till den senaste versionen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>Gör _not_ konfigurera en Redis-slavanslutning för molninfrastrukturprojekt med en [skalad arkitektur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Detta orsakar Redis-anslutningsfel. Se [Redis konfigurationsguide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) i _Commerce on Cloud Infrastructure_ guide.

### Konfigurera lokala distributioner

För Adobe Commerce lokala distributioner konfigurerar du den nya Redis-cacheimplementeringen med `bin/magento:setup` kommandon. Instruktioner finns i [Använd Redis för standardcache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Separata cache- och sessionsinstanser

Genom att separera Redis-cachen från Redis-sessionen kan du hantera cachen och sessioner oberoende av varandra för att förhindra att cacheproblem påverkar sessionerna.

1. Uppdatera `.magento/services.yaml` konfigurationsfil.

   ```yaml
   mysql:
       type: mysql:10.4
       disk: 35000
   
   redis:
      type: redis:6.0
   
   redis-session:              # This is for the new Redis instance
      type: redis:6.0
   
   search:
      type: elasticsearch:7.9
      disk: 5000
   
   rabbitmq:
      type: rabbitmq:3.8
      disk: 2048
   ```

1. Uppdatera `.magento.app.yaml` konfigurationsfil.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Skicka ett [Adobe Commerce Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) om du vill ändra Redis tjänstkonfiguration i Pro Production- och Staging-miljöer. Inkludera den uppdaterade `.magento/services.yaml` och `.magento.app.yaml` konfigurationsfiler.

1. Kontrollera att den nya instansen körs och notera portnumret.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Lägg till portnumret i `.magento.env.yaml` konfigurationsfil.

   >[!NOTE]
   >`disable_locking` måste anges till `1`.
   >   

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374       # check the port in $MAGENTO_CLOUD_RELATIONSHIPS
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Ta bort sessioner från [standarddatabas](../../../configuration/cache/redis-pg-cache.md) (`db 0`) på Redis-cacheinstansen.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Under distributionen ska du se följande rader i [skapa och distribuera logg](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```terminal
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'redis' is 6.0
[2022-08-17 01:13:40] INFO: Version of service 'redis-session' is 6.0
[2022-08-17 01:13:40] INFO: redis-session will be used for session if it was not override by SESSION_CONFIGURATION
```

## Cachekomprimering

Använd cachekomprimering, men tänk på att det finns en kompromiss mellan prestanda på klientsidan. Om du har en ledig processor aktiverar du den. Se [Använd Redis för sessionslagring](../../../configuration/cache/redis-session.md).

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Ytterligare information

- [Redis Page Cache](../../../configuration/cache/redis-pg-cache.md)
- [Använd Redis för sessionslagring](../../../configuration/cache/redis-session.md)
