---
title: Best Practices for Redis and Valkey Service Configuration
description: Lär dig hur du konfigurerar Redis- och Valkey-tjänster för Adobe Commerce. Förbättra cachningsprestanda med L2-cache, slavanslutningar, inaktuell cache och sessionsseparation.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 381d58d5fc9844aca88239e8e7ac39151dfc766c
workflow-type: tm+mt
source-wordcount: '1909'
ht-degree: 0%

---


# Bästa tillvägagångssätt för Redis- och Valkey-tjänstkonfiguration

Använd de här rekommendationerna för att konfigurera Redis eller Valkey för Adobe Commerce-cachning och sessioner.

- Konfigurera L2-cache
- Aktivera slavanslutning
- Förhandsladda nycklar
- Aktivera inaktuell cache
- Separat cache och session
- Komprimera cachen
- Konfigurationsexempel

>[!NOTE]
>
>Kontrollera att du använder den senaste versionen av `ece-tools`-paketet för infrastrukturmiljöer i Commerce på Cloud. Om inte, [uppgradera till den senaste versionen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=sv-SE). Du kan kontrollera vilken version som är installerad i din lokala miljö med hjälp av CLI-kommandot `composer show magento/ece-tools`.

## Konfigurera L2-cache

Konfigurera L2-cachen genom att ange distributionsvariabeln `REDIS_BACKEND` eller `VALKEY_BACKEND` i konfigurationsfilen `.magento.env.yaml`.

>[!BEGINTABS]

>[!TAB Redis-konfiguration]

För Redis, använd:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Om du vill se miljökonfiguration för molninfrastruktur läser du [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=sv-SE#redis_backend) konfigurationsreferens i _Commerce on Cloud Infrastructure Guide_.

Information om lokala installationer finns i [Konfigurera Redis-sidcache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) i _konfigurationshandboken_.

>[!TAB Nyckelkonfiguration]

Använd Valkey:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Mer information om miljökonfiguration för molninfrastruktur finns i [`VALKEY_BACKEND`](https://experienceleague.adobe.com/sv/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) konfigurationsreferens i _Commerce on Cloud Infrastructure Guide_.

Information om lokala installationer finns i [Konfigurera Valkey](../../../configuration/cache/config-valkey.md) i _Konfigurationshandboken_.

>[!ENDTABS]


### L2-cacheminnets storlek för Adobe Commerce Cloud

L2-cache använder ett [tillfälligt filsystem](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`) som lagringsmekanism. Till skillnad från specialiserade nyckelvärdenheter har tmpfs ingen huvudavhämtningsprincip, vilket innebär att minnesanvändningen kan öka obegränsat. För att förhindra övertömning rensar Adobe Commerce automatiskt L2-lagringen när användningen når ett konfigurerbart tröskelvärde (95 % som standard). Du kan kontrollera minnesanvändningen genom att begära ett större `/dev/shm`-paket eller genom att sänka rensningströskeln.

Justera den maximala minnesanvändningen för L2-cache baserat på dina projektkrav. Använd någon av följande metoder:

- Skapa en supportbiljett för att justera monteringsstorleken `/dev/shm`. I det här scenariot rekommenderar Adobe att du anger monteringsstorleken `/dev/shm` till 15 GB.
- Justera egenskapen `cleanup_percentage` på programnivå för att begränsa lagringsanvändningen och frigöra minne för andra tjänster.
Du kan justera konfigurationen i distributionskonfigurationen under cachekonfigurationsgruppen `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>Det konfigurerbara alternativet `cleanup_percentage` introducerades i Adobe Commerce 2.4.4.

I följande exempel visas konfigurationskoden i filen `.magento.env.yaml`:

>[!BEGINTABS]

>[!TAB Redis-konfiguration]

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

>[!TAB Nyckelkonfiguration]

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!ENDTABS]

Cachekraven varierar beroende på din projektkonfiguration och anpassad tredjepartskod. Anpassa L2-cacheminnet så att cacheminnet kan fungera utan täta tröskelträffar.

Helst stabiliseras minnesanvändningen för L2-cache under tröskelvärdet för att undvika täta rensningar av lagringsutrymmet.

Du kan kontrollera minnesanvändningen för L2-cache på varje nod i klustret genom att köra följande CLI-kommando och granska raden `/dev/shm`.

```bash
df -h /dev/shm
```

Användningen kan variera mellan olika noder, men den bör konverteras till ett liknande värde.

## Aktivera slavanslutning

Aktivera slavanslutningen i filen `.magento.env.yaml` om du vill att Adobe Commerce ska kunna använda ytterligare en skrivskyddad cacheanslutning för läsningar medan den primära slutpunkten för skrivningar fortsätter att användas. Den här konfigurationen kan minska läsbelastningen på den primära cachetjänsten och distribuera lästrafik mer effektivt.

>[!BEGINTABS]

>[!TAB Redis-konfiguration]

För Redis, använd:

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Om du vill se miljökonfiguration för Commerce Cloud infrastruktur läser du [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=sv-SE#redis_use_slave_connection) i _Commerce on Cloud Infrastructure Guide_.

För Adobe Commerce lokala installationer konfigurerar du den nya Redis-cacheimplementeringen med kommandona `bin/magento setup`. Se [Använd Redis för standardcache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) i _Konfigurationshandboken_.

>[!TAB Nyckelkonfiguration]

Använd Valkey:

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Om du vill se miljökonfiguration för Commerce Cloud infrastruktur läser du [VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=sv-SE#valkey_use_slave_connection) i _Commerce on Cloud Infrastructure Guide_.

För Adobe Commerce lokala installationer konfigurerar du den nya Valkey-cacheimplementeringen med kommandona `bin/magento setup`. Se [Konfigurera Valkey](../../../configuration/cache/config-valkey.md) i _Konfigurationshandboken_.

>[!ENDTABS]

## Förhandsladda nycklar

Magento läser vanligtvis in cacheposter från Redis eller Valkey en nyckel i taget. Med funktionen för förinläsning kan du visa en lista med ofta använda nycklar som Magento hämtar i en enda pipeline vid första åtkomsten under en begäran. Magento behåller sedan de hämtade värdena i PHP-minnet för resten av den begäran, vilket minskar antalet upprepade rundresor till Redis eller Valkey och kan förbättra Bootstrap-prestanda för dessa nycklar.

Du kan identifiera tangenter som används ofta genom att övervaka aktiva kommandon på Redis eller Valkey:

>[!BEGINTABS]

>[!TAB Avvisa konfigurationen för förinläsningsnyckeln igen]

Förinläsningsnycklarna är konfigurerade i konfigurationsfilen `.magento.env.yaml`.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Kör följande kommando om du vill visa en lista över tangenterna:

```terminal
redis-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Efter 10 sekunder trycker du på **[!UICONTROL Ctrl+C]**. Kör sedan följande kommando:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

I den här loggen visas de nycklar som du kan läsa in i förväg. Om du vill visa innehållet i en tangent kör du följande kommando:

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

Lokala installationer finns i [Redis-förinläsningsfunktionen](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) i _Konfigurationshandboken_.

>[!TAB Nyckelkonfiguration för förhandsladdning av nyckel]

Förinläsningsnycklarna är konfigurerade i konfigurationsfilen `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Kör följande kommando om du vill visa en lista över tangenterna:

```terminal
valkey-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Efter 10 sekunder trycker du på **[!UICONTROL Ctrl+C]**. Kör sedan följande kommando:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

I den här loggen visas de nycklar som du kan läsa in i förväg. Om du vill visa innehållet i en tangent kör du följande kommando:

```terminal
valkey-cli -p 6370 -n 1 hgetall "<key_name>"
```

Lokala installationer finns i [Förinläsningsfunktionen Valkey](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature) i _Konfigurationshandboken_.

>[!ENDTABS]

## Aktivera inaktuell cache

Inaktuell cache är en L2-cachefunktion i `RemoteSynchronizedCache`. När det här alternativet är aktiverat kan Adobe Commerce leverera ett befintligt lokalt cachevärde från `/dev/shm` medan en annan begäran redan återskapar samma post, i stället för att göra varje väntan på samtidiga begäranden. Detta minskar cachestämplar och låskonflikter vid omgenerering av dyra cacheposter.

### Så här fungerar det

Med `RemoteSynchronizedCache` har Magento två kopior av varje cachepost: en lokal kopia i `/dev/shm` och en fjärrkopia i Redis eller Valkey. När fjärrkopian inte är tillgänglig och det redan finns ett regenereringslås för den nyckeln, kan samtidiga begäranden ta emot det tidigare lokala värdet i stället för att vänta tills det nya värdet skrivs.

Om du vill aktivera inaktuellt cacheminne konfigurerar du det i filen `.magento.env.yaml`.

>[!BEGINTABS]

>[!TAB Konfigurera inaktuell cache för Redis]

För Redis:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!TAB Konfigurera inaktuell cache för Valkey]

För Valkey:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!ENDTABS]

>[!NOTE]
>
>Cachetypen `full_page` är inte relevant för Adobe Commerce i Cloud-infrastrukturprojekt eftersom de använder [Fast](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/cdn/fastly).

Lokala installationer beskrivs i [Alternativ för inaktuell cache](../../../configuration/cache/level-two-cache.md#stale-cache-options) i _Konfigurationshandboken_.

>[!WARNING]
>
>Med konfigurationen ovan aktiveras inaktuell cache på cachefrontend för `default`, vilket tillämpar beteende för inaktuell cache för alla cacheposter som använder den förgreningen. Magento centrala cachetyper fungerar normalt som förväntat med den här inställningen. Om ditt projekt innehåller anpassad kod eller tillägg som skriver till cacheminnet via det generiska `\Magento\Framework\App\Cache`-API:t (till exempel `$this->cache->save()`) utan en dedikerad cacheklientdel, kan dessa poster även generera stale-värden under omgenereringen.
>
>
>Om detta resulterar i oväntat beteende i dina anpassningar, låter du inaktuell cache vara inaktiverat på `default`-frontend och bara aktivera den för valda cachetyper, vilket vanligtvis är [utförd lokalt](../../../configuration/cache/level-two-cache.md#stale-cache-options).

### Aktivera inaktuell cache per cachetyp individuellt

Du kan bara aktivera inaktuell cache för de valda cachetyperna genom att definiera en dedikerad cacheklientmapp i `.magento.env.yaml` och mappa de valda cachetyperna till den.

För att den anpassade förgreningen ska fungera korrekt måste den definieras som en fullständig förskjutning under `CACHE_CONFIGURATION.frontend`. Det räcker inte att bara definiera `use_stale_cache: true` för ett nytt klientnamn.

**Exempelkonfigurationer**

>[!BEGINTABS]

>[!TAB Konfigurera inaktuell cache för Redis]

För Redis:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':

        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!TAB Konfigurera inaktuell cache för Valkey]

För Valkey:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':
 
        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!ENDTABS]

>[!NOTE]
>
>Om källfilens klientstruktur har konfigurerats med ytterligare alternativ för serverdelen, som komprimering, nya försök, förinläsningsnycklar eller andra justeringsvärden, kopierar du dessa alternativ till `stale_cache_enabled` så att den nya frontend behåller samma beteende.


## Separata cache- och sessionsinstanser

Genom att separera cacheminnet från sessionerna kan du hantera dem oberoende av varandra. Det minskar konflikter mellan cache- och sessionstrafik, förhindrar cacherelaterat tryck från att påverka sessioner och gör att varje Redis- eller Valkey-instans kan storleksändras och justeras för sin egen arbetsbelastning.

Följ stegen nedan för att skapa en dedikerad instans för sessioner:

>[!BEGINTABS]

>[!TAB Redis]

1. Uppdatera konfigurationsfilen `.magento/services.yaml`.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   redis:
     type: redis:6.0
   
   redis-session: # This is for the new Redis instance
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

1. Begär en ny Redis-instans som är dedikerad till sessioner i produktions- och mellanlagringsmiljöer.

   Skicka en [Adobe Commerce-supportanmälan](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=sv-SE#submit-ticket). Inkludera de uppdaterade konfigurationsfilerna för `.magento/services.yaml` och `.magento.app.yaml`.

   Uppdateringen orsakar inga driftavbrott, men en distribution krävs för att aktivera den nya tjänsten.

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
   >Ange `disable_locking` till `1` för bästa prestanda. I sällsynta fall där konkurrensförhållanden inträffar på grund av hög samtidiga sessionsaktivitet, anger du det till `0` för att aktivera låsning.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Ta bort sessioner från [standarddatabasen](../../../configuration/cache/redis-pg-cache.md) (`db 0`) i Redis-cacheinstansen.

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Valkey]

1. Uppdatera konfigurationsfilen `.magento/services.yaml`.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   valkey:
     type: valkey:8.0
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:8.0
   
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
     valkey: "valkey:valkey"
     valkey-session: "valkey-session:valkey"   # Relationship of the new Valkey instance
     search: "search:elasticsearch"
     rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Begär en ny Valkey-instans som är dedikerad till sessioner i produktions- och mellanlagringsmiljöer.

   Skicka en [Adobe Commerce-supportanmälan](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=sv-SE#submit-ticket). Inkludera de uppdaterade konfigurationsfilerna för `.magento/services.yaml` och `.magento.app.yaml`.

   Uppdateringen orsakar inga driftavbrott, men en distribution krävs för att aktivera den nya tjänsten.

1. Kontrollera att den nya instansen körs och notera portnumret.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Lägg till portnumret i konfigurationsfilen `.magento.env.yaml`.

   >[!IMPORTANT]
   >
   >Konfigurera endast Valkey-sessionsporten om `ece-tools` inte automatiskt kan identifiera den från definitionen för Valkey-sessionstjänsten i `MAGENTO_CLOUD_RELATIONSHIPS`.

   >[!NOTE]
   >
   >Ange `disable_locking` till `1` för bästa prestanda. I sällsynta fall där konkurrensförhållanden inträffar på grund av hög samtidiga sessionsaktivitet, anger du det till `0` för att aktivera låsning.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis: # keep 'redis' even if you are using Valkey.
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Ta bort sessioner från [standarddatabasen](../../../configuration/cache/redis-pg-cache.md) (`db 0`) i instansen av Valkey-cachen.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## Cachekomprimering

Om du använder mer än 6 GB Redis eller Valkey `maxmemory` kan du aktivera cachekomprimering för att minska det utrymme som används av nycklarna. Tänk på att den här inställningen påverkar prestanda på klientsidan för minnesbesparingar. Om du har en ledig CPU-kapacitet bör du överväga att aktivera den. Se [Använd Redis för sessionslagring](../../../configuration/cache/redis-session.md) eller [Använd Valkey för sessionslagring](../../../configuration/cache/valkey-session.md) i _konfigurationshandboken_.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Aktivera asynkron frigivning

Om du vill aktivera `lazyfree` på Adobe Commerce i molninfrastrukturen skickar du en [Adobe Commerce Support-biljett](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=sv-SE#submit-ticket) med en begäran om att följande Redis- eller Valkey-konfiguration ska användas i dina miljöer:

```text
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

När `lazyfree` är aktiverat avlastar Redis eller Valkey minnesåtergivningen till bakgrundstrådar för borttagningar, förfallotider, serverinitierade borttagningar, användarborttagningar och tömningar av replikdatauppsättningar. Detta minskar blockeringen av huvudtråden och kan minska fördröjningen för förfrågningar.

>[!NOTE]
>
>Alternativet `lazyfree-lazy-user-del yes` gör att kommandot `DEL` beter sig som `UNLINK`, som omedelbart bryter länken till tangenterna och frigör deras minne asynkront.

>[!WARNING]
>
>Eftersom frigöring sker i bakgrunden kommer minne som används av borttagna, utgångna eller vräknade tangenter att allokeras tills bakgrundstrådarna slutför arbetet. Om Redis- eller Valkey-instansen redan har ett starkt minnestryck bör du testa försiktigt och överväga att minska minnestrycket först. Du kan till exempel inaktivera blockcachen för specifika fall och separata cacheminne- och sessionsinstanser för Redis enligt beskrivningen ovan.

## Aktivera flertrådig I/O

Om du vill aktivera Redis I/O-trådning på Adobe Commerce i molninfrastruktur skickar du en [Adobe Commerce Support-biljett](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=sv-SE#submit-ticket) med en I/O-trådningskonfiguration nedan. Den här konfigurationen kan förbättra genomströmningen genom att avlasta socketläsningar och -skrivningar och kommandoparsning från huvudtråden, till priset av högre CPU-användning. Validera under inläsning och övervaka dina värdar.

>[!BEGINTABS]

>[!TAB Konfigurera I/O-trådar för Redis]

För Redis:

```text
io-threads-do-reads yes
io-threads 8 # Choose a value lower than the number of CPU cores (check with nproc), and then tune under load.
```

>[!TAB Konfigurera I/O-trådar för Valkey]

För Valkey:

```text
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
events-per-io-thread 2
```

>[!ENDTABS]


>[!NOTE]
>
>I/O-trådar fungerar parallellt med klientens I/O och endast parsing. Redis-kommandokörning förblir entrådad.

>[!WARNING]
>
>Att aktivera I/O-trådar kan öka CPU användning och är inte till någon nytta för alla arbetsbelastningar. Börja med ett konservativt värde och ett riktmärke. Om fördröjningen ökar eller CPU mättas minskar du `io-threads` eller inaktiverar läsningar i I/O-trådar.


## Öka klientens tidsgränser och försök

Öka Redis- eller Valkey-cacheklientens tolerans mot korta mättnadsperioder genom att justera serverdelsalternativen i `.magento.env.yaml`.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            connect_retries: 3 # Number of connection retries
            remote_backend_options:
              read_timeout: 10 # Timeout
```

Dessa inställningar kan minska antalet intermittenta anslutnings- och lästimeout-fel under korta toppar genom att försöka konfigurera anslutningen igen och ge mer tid för svar från Redis eller Valkey.

>[!NOTE]
>
>De här inställningarna kan vara till hjälp vid kort överbelastning, men de åtgärdar inte beständig överbelastning.

## Konfigurationsexempel

Använd följande exempel som utgångspunkt för Redis- eller Valkey-tjänstkonfigurationer.


### Använd alla rekommendationer för bästa praxis

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # Any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:

        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.

        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Exempel på värdekonfiguration]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

### Använd alla rekommendationer för bästa praxis och separata inaktuella cacheminnen efter cachetyp

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis: # keep 'redis' even if you are using Valkey.
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

## Ytterligare information

Se följande relaterade ämnen:

- [Redis Page Cache](../../../configuration/cache/redis-pg-cache.md)
- [Använd Redis för sessionslagring](../../../configuration/cache/redis-session.md)
- [Använd Valkey för standardcache](../../../configuration/cache/valkey-pg-cache.md)
- [Använd Valkey för sessionslagring](../../../configuration/cache/valkey-session.md)
