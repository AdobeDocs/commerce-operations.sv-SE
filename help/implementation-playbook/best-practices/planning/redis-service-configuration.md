---
title: Bästa tillvägagångssätt för Redis-tjänstkonfiguration
description: Lär dig hur du förbättrar cachelagringsprestanda med den utökade Redis-cacheimplementeringen för Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 6772c4fe31cfcd18463b9112f12a2dc285b39324
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Bästa tillvägagångssätt för Redis-tjänstkonfiguration

- Konfigurera Redis L2-cache
- Aktivera Redis-slavanslutning
- Förinläsningsnycklar
- Aktivera inaktuell cache
- Separera Redis-cachen från Redis-sessionen
- Komprimera Redis-cachen och använd `gzip` för högre komprimering

## Konfigurera Redis L2-cache

Konfigurera Redis L2-cachen genom att ställa in `REDIS_BACKEND` distributionsvariabeln i `.magento.env.yaml` konfigurationsfil.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Om du vill se miljökonfigurationen för molninfrastrukturen kan du gå till [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) i _Handbok för Commerce on Cloud Infrastructure_.

För lokala installationer, se [Konfigurera Redis-sidcache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) i _Konfigurationshandbok_.

>[!NOTE]
>
>Kontrollera att du använder den senaste versionen av `ece-tools` paket. Om inte, [uppgradera till den senaste versionen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). Du kan kontrollera vilken version som är installerad i den lokala miljön med `composer show magento/ece-tools` CLI-kommando.


### L2-cacheminnets storlek (Adobe Commerce Cloud)

L2-cache använder en [temporärt filsystem](https://en.wikipedia.org/wiki/Tmpfs) som en lagringsmekanism. Jämfört med specialiserade nyckelvärdesdatabassystem har ett temporärt filsystem ingen nyckelvridarpolicy för att styra minnesanvändningen.

Bristen på kontroll över minnesanvändningen kan få L2-cacheminnets minnesanvändning att växa över tiden genom att det inaktuella cacheminnet samlas.

För att undvika minnesöverbelastning av implementeringar av L2-cache rensar Adobe Commerce lagringsutrymmet när en viss tröskel uppnås. Standardtröskelvärdet är 95 %.

Det är viktigt att justera den maximala användningen av L2-cacheminnet baserat på projektkraven för cache-lagring. Använd någon av följande metoder för att konfigurera minnescachestorleken:

- Skapa en supportanmälan för att begära storleksändringar av `/dev/shm` montera.
- Justera `cleanup_percentage` på appliceringsnivå för att begränsa den maximala fyllningsprocenten för lagringsutrymmet. Det återstående lediga minnet kan användas av andra tjänster.
Du kan justera konfigurationen i distributionskonfigurationen under cachekonfigurationsgruppen `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>The `cleanup_percentage` konfigurerbara alternativ introducerades i Adobe Commerce 2.4.4.

I följande kod visas en exempelkonfiguration i `.magento.env.yaml` fil:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

Cachekraven kan variera beroende på projektkonfiguration och anpassad tredjepartskod. Omfånget för storleken på L2-cacheminnet gör att L2-cacheminnet kan fungera utan för många tröskelträffar.
Helst bör minnesanvändningen för L2-cache stabiliseras på en viss nivå under tröskelvärdet, för att undvika täta rensningar av lagringsutrymmet.

Du kan kontrollera hur mycket lagringsminne som används för L2-cache på varje nod i klustret med följande CLI-kommando och leta efter `/dev/shm` linje.
Användningen kan variera mellan olika noder, men den bör konvergera till samma värde.

```bash
df -h
```

## Aktivera Redis-slavanslutning

Aktivera en Redis-slavanslutning i `.magento.env.yaml` konfigurationsfilen så att bara en nod kan hantera läs- och skrivtrafik medan de andra noderna hanterar den skrivskyddade trafiken.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Se [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) i _Handbok för Commerce on Cloud Infrastructure_.

Konfigurera den nya Redis-cacheimplementeringen med `bin/magento:setup` kommandon. Se [Använd Redis för standardcache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) i _Konfigurationshandbok_.

>[!WARNING]
>
>Gör _not_ konfigurera en Redis-slavanslutning för molninfrastrukturprojekt med en [skalad/delad arkitektur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Detta orsakar Redis-anslutningsfel. Se [Riktlinjer för konfiguration av Redis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) i _Commerce on Cloud Infrastructure_ guide.

## Förinläsningsnycklar

Om du vill återanvända data mellan sidor anger du nycklarna för förinläsning i `.magento.env.yaml` konfigurationsfil.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_'                       # Prefix for keys to be preloaded
          backend_options:
            preload_keys:                         # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash'
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

För lokala installationer, se [Förinläsningsfunktion för Redis](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) i _Konfigurationshandbok_.

## Aktivera inaktuell cache

Minska väntetiderna för lås och förbättra prestanda - särskilt när du hanterar många block- och cachenycklar - genom att använda ett föråldrat cacheminne när du genererar ett nytt cacheminne parallellt. Aktivera inaktuell cache och definiera cachetyper i `.magento.env.yaml` konfigurationsfil:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      default:
        backend_options:
          use_stale_cache: false
      stale_cache_enabled:
        backend_options:
          use_stale_cache: true
      type:
        default:
          frontend: "default"
        layout:
          frontend: "stale_cache_enabled"
        block_html:
          frontend: "stale_cache_enabled"
        reflection:
          frontend: "stale_cache_enabled"
        config_integration:
          frontend: "stale_cache_enabled"
        config_integration_api:
          frontend: "stale_cache_enabled"
        full_page:
          frontend: "stale_cache_enabled"
        translate:
          frontend: "stale_cache_enabled"
```

Information om hur du konfigurerar lokala installationer finns i [Alternativ för inaktuell cache](../../../configuration/cache/level-two-cache.md#stale-cache-options) i _Konfigurationshandbok_.

## Separat Redis-cache och sessionsinstanser

Genom att separera Redis-cachen från Redis-sessionen kan du hantera cachen och sessioner oberoende av varandra. Det förhindrar att cacheproblem påverkar sessionerna, vilket kan påverka intäkterna. Varje Redis-instans körs i sin egen kärna, vilket förbättrar prestandan.

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

1. Skicka ett [Adobe Commerce Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) för att begära etablering av en ny Redis-instans som är dedikerad till sessioner i produktions- och mellanlagringsmiljöer. Inkludera den uppdaterade `.magento/services.yaml` och `.magento.app.yaml` konfigurationsfiler. Detta orsakar inga driftavbrott, men en distribution krävs för att aktivera den nya tjänsten.

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

Om du använder mer än 6 GB Redis `maxmemory`kan du använda cachekomprimering för att minska det utrymme som tangenterna förbrukar. Tänk på att det finns en kompromiss med prestanda på klientsidan. Om du har en ledig processor aktiverar du den. Se [Använd Redis för sessionslagring](../../../configuration/cache/redis-session.md) i _Konfigurationshandbok_.

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
