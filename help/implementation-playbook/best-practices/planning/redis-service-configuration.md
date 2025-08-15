---
title: Bästa tillvägagångssätt för Redis-tjänstkonfiguration
description: Lär dig hur du förbättrar cachelagringsprestanda med den utökade Redis-cacheimplementeringen för Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: bbebb414ae3b8c255e17b1f3673a6c4b7c6f23b2
workflow-type: tm+mt
source-wordcount: '840'
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

Konfigurera Redis L2-cachen genom att ange distributionsvariabeln `REDIS_BACKEND` i konfigurationsfilen `.magento.env.yaml`.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Om du vill se miljökonfiguration för molninfrastruktur läser du [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=sv-SE#redis_backend) i _Commerce on Cloud Infrastructure Guide_.

Information om lokala installationer finns i [Konfigurera Redis-sidcache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) i _konfigurationshandboken_.

>[!NOTE]
>
>Kontrollera att du använder den senaste versionen av paketet `ece-tools`. Om inte, [uppgradera till den senaste versionen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=sv-SE). Du kan kontrollera vilken version som är installerad i din lokala miljö med hjälp av CLI-kommandot `composer show magento/ece-tools`.


### L2-cacheminnets storlek (Adobe Commerce Cloud)

L2-cache använder ett [tillfälligt filsystem](https://en.wikipedia.org/wiki/Tmpfs) som en lagringsmekanism. Jämfört med specialiserade nyckelvärdesdatabassystem har ett temporärt filsystem ingen nyckelvridarpolicy för att styra minnesanvändningen.

Bristen på kontroll över minnesanvändningen kan få L2-cacheminnets minnesanvändning att växa över tiden genom att det inaktuella cacheminnet samlas.

För att undvika minnesöverbelastning av implementeringar av L2-cache rensar Adobe Commerce lagringsutrymmet när en viss tröskel uppnås. Standardtröskelvärdet är 95 %.

Det är viktigt att justera den maximala användningen av L2-cacheminnet baserat på projektkraven för cache-lagring. Använd någon av följande metoder för att konfigurera minnescachestorleken:

- Skapa en supportbiljett för att begära storleksändringar av monteringen `/dev/shm`.
- Justera egenskapen `cleanup_percentage` på programnivå för att begränsa den maximala fyllningsprocenten för lagringsutrymmet. Det återstående lediga minnet kan användas av andra tjänster.
Du kan justera konfigurationen i distributionskonfigurationen under cachekonfigurationsgruppen `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>Det konfigurerbara alternativet `cleanup_percentage` introducerades i Adobe Commerce 2.4.4.

I följande kod visas en exempelkonfiguration i filen `.magento.env.yaml`:

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

Du kan kontrollera hur mycket lagringsminne L2-cache används på varje nod i klustret med följande CLI-kommando och leta efter raden `/dev/shm`.
Användningen kan variera mellan olika noder, men den bör konvergera till samma värde.

```bash
df -h
```

## Aktivera Redis-slavanslutning

Aktivera en Redis-slavanslutning i konfigurationsfilen `.magento.env.yaml` om du bara vill tillåta en nod att hantera läs- och skrivtrafik medan de andra noderna hanterar den skrivskyddade trafiken.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Se [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=sv-SE#redis_use_slave_connection) i _Commerce on Cloud Infrastructure Guide_.

För Adobe Commerce lokala installationer konfigurerar du den nya Redis-cacheimplementeringen med kommandona `bin/magento:setup`. Se [Använd Redis för standardcache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) i _Konfigurationshandboken_.

>[!WARNING]
>
>Konfigurera _inte_ en Redis-slavanslutning för molninfrastrukturprojekt med en [skalad/delad arkitektur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html?lang=sv-SE). Detta orsakar Redis-anslutningsfel. Se [Redis-konfigurationsvägledning](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=sv-SE#redis_use_slave_connection) i guiden _Commerce om molninfrastruktur_.

## Förinläsningsnycklar

Om du vill återanvända data mellan sidor anger du nycklarna för förinläsning i konfigurationsfilen `.magento.env.yaml`.

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

Lokala installationer finns i [Redis-förinläsningsfunktionen](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) i _Konfigurationshandboken_.

## Aktivera inaktuell cache

Minska väntetiderna för lås och förbättra prestanda - särskilt när du hanterar många block- och cachenycklar - genom att använda ett föråldrat cacheminne när du genererar ett nytt cacheminne parallellt. Aktivera inaktuell cache och definiera cachetyper i konfigurationsfilen `.magento.env.yaml`:

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

>[!NOTE]
>
>I det föregående exemplet är cachen `full_page` inte relevant för Adobe Commerce i molninfrastrukturprojekt, eftersom de använder [Fast](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/cdn/fastly).

Information om hur du konfigurerar lokala installationer finns i [Inaktuella cachealternativ](../../../configuration/cache/level-two-cache.md#stale-cache-options) i _Konfigurationshandboken_.

## Separat Redis-cache och sessionsinstanser

Genom att separera Redis-cachen från Redis-sessionen kan du hantera cachen och sessioner oberoende av varandra. Det förhindrar att cacheproblem påverkar sessionerna, vilket kan påverka intäkterna. Varje Redis-instans körs i sin egen kärna, vilket förbättrar prestandan.

1. Uppdatera konfigurationsfilen `.magento/services.yaml`.

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

1. Uppdatera konfigurationsfilen `.magento.app.yaml`.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Skicka en [Adobe Commerce-supportanmälan](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=sv-SE#submit-ticket) för att begära etablering av en ny Redis-instans som är dedikerad till sessioner i produktions- och mellanlagringsmiljöer. Inkludera de uppdaterade konfigurationsfilerna för `.magento/services.yaml` och `.magento.app.yaml`. Detta orsakar inga driftavbrott, men en distribution krävs för att aktivera den nya tjänsten.

1. Kontrollera att den nya instansen körs och notera portnumret.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Lägg till portnumret i konfigurationsfilen `.magento.env.yaml`.

   >[!IMPORTANT]
   >
   >Konfigurera endast Redis-sessionsporten om `ece-tools` inte kan identifiera den automatiskt från definitionen för Redis-sessionstjänsten i `MAGENTO_CLOUD_RELATIONSHIPS`.

   >[!NOTE]
   >
   >`disable_locking` måste anges till `1`.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374 # check the port in $MAGENTO_CLOUD_RELATIONSHIPS and put it here (by default, you can delete this line!!)
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Ta bort sessioner från [standarddatabasen](../../../configuration/cache/redis-pg-cache.md) (`db 0`) i Redis-cacheinstansen.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Under distributionen bör du se följande rader i [bygg- och distributionsloggen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=sv-SE#build-and-deploy-logs):

```
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

Om du använder mer än 6 GB Redis `maxmemory` kan du använda cachekomprimering för att minska utrymmet som nycklarna förbrukar. Tänk på att det finns en kompromiss med prestanda på klientsidan. Om du har en ledig processor aktiverar du den. Se [Använd Redis för sessionslagring](../../../configuration/cache/redis-session.md) i _Konfigurationshandboken_.

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
