---
title: Bästa tillvägagångssätt för konfiguration av Valkey-tjänster
description: Lär dig hur du förbättrar cachelagringsprestanda med den utökade Valkey-cacheimplementeringen för Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: ca1598b0-07c6-4338-aed1-f2ba05375197
source-git-commit: 75dc606da65196619028e99ec44841db3988a73e
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Bästa tillvägagångssätt för konfiguration av Valkey-tjänster

Adobe rekommenderar följande metodtips när du konfigurerar Valkey-tjänsten:

## Konfigurera Valkey L2-cache

Konfigurera Valkey L2-cachen genom att ange distributionsvariabeln `VALKEY_BACKEND` i konfigurationsfilen `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Om du vill se miljökonfiguration för molninfrastruktur läser du [`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) i _Commerce on Cloud Infrastructure Guide_.

Lokala installationer finns i [Konfigurera cache-lagring för Valkey-sidor](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching) i _konfigurationshandboken_.

>[!NOTE]
>
>Kontrollera att du använder den senaste versionen av paketet `ece-tools`. Om inte, [uppgradera till den senaste versionen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package). Du kan kontrollera vilken version som är installerad i din lokala miljö med hjälp av CLI-kommandot `composer show magento/ece-tools`.

### L2-cacheminnets storlek (Adobe Commerce Cloud)

L2-cache använder ett [tillfälligt filsystem](https://en.wikipedia.org/wiki/Tmpfs) som en lagringsmekanism. Jämfört med specialiserade nyckelvärdesdatabassystem har ett temporärt filsystem ingen nyckelvridningsprincip för att styra minnesanvändningen.

Bristen på kontroll över minnesanvändningen kan få L2-cacheminnets minnesanvändning att växa över tiden genom att det inaktuella cacheminnet samlas.

För att undvika minnesöverbelastning av implementeringar av L2-cache rensar Adobe Commerce lagringsutrymmet när en viss tröskel uppnås. Standardtröskelvärdet är 95 %.

Det är viktigt att justera den maximala användningen av L2-cacheminnet baserat på projektkraven för cache-lagring. Använd någon av följande metoder för att konfigurera minnescachestorleken:

- Skapa en supportbiljett för att begära storleksändringar av monteringen `/dev/shm`.
- Justera egenskapen `cleanup_percentage` på programnivå för att begränsa den maximala fyllningsprocenten för lagringsutrymmet. Det återstående lediga minnet kan användas av andra tjänster.
Du kan justera konfigurationen i distributionskonfigurationen under cachekonfigurationsgruppen `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>Konfigurationsalternativet `cleanup_percentage` infördes i Adobe Commerce 2.4.4.

I följande exempel visas en `CACHE_CONFIGURATION` i filen `.magento.env.yaml`:

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

Cachekraven kan variera beroende på projektkonfiguration och anpassad tredjepartskod. Storleken på L2-cacheminnets storlek gör att L2-cachen kan fungera utan onödiga tröskelträffar.
Helst bör minnesanvändningen för L2-cache stabiliseras på en viss nivå under tröskelvärdet, för att undvika täta rensningar av lagringsutrymmet.

Du kan kontrollera hur mycket lagringsminne i L2-cachen används på varje nod i klustret med följande CLI-kommando och sedan söka efter raden `/dev/shm`.
Användningen kan variera mellan olika noder, men den bör konvergera till samma värde.

```bash
df -h
```

## Aktivera Valkey-slavanslutning

Aktivera en Valkey-slavanslutning i konfigurationsfilen `.magento.env.yaml` om du bara vill tillåta en nod att hantera läs- och skrivtrafik medan de andra noderna hanterar den skrivskyddade trafiken.

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Mer information finns i [VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) i _Commerce on Cloud Infrastructure Guide_.

För Adobe Commerce lokala installationer konfigurerar du den nya Valkey-cacheimplementeringen med kommandona `bin/magento:setup`. Mer information finns i [Använd valnyckel för standardcache](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching) i _Konfigurationshandboken_.

>[!WARNING]
>
>Konfigurera _inte_ en Valkey-slavanslutning för molninfrastrukturprojekt med en [skalad/delad arkitektur](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/scaled-architecture). Detta orsakar anslutningsfel för Valkey. Mer information finns i [Riktlinjerna för värdekonfiguration](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) i guiden _Commerce om molninfrastruktur_.

## Förinläsningsnycklar

Om du vill återanvända data mellan sidor anger du nycklarna för förinläsning i konfigurationsfilen `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

Lokala installationer finns i [Förinläsningsfunktionen Valkey](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature) i _Konfigurationshandboken_.

## Aktivera inaktuell cache

Minska väntetiderna för lås och förbättra prestanda, särskilt när du hanterar många block- och cachenycklar, genom att använda ett föråldrat cacheminne när du genererar ett nytt cacheminne parallellt. Aktivera inaktuell cache och definiera cachetyper i konfigurationsfilen `.magento.env.yaml`:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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
>I det föregående exemplet är cachen `full_page` inte relevant för Adobe Commerce i molninfrastrukturprojekt, eftersom de använder [Fast](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly).

Information om hur du konfigurerar lokala installationer finns i [Inaktuella cachealternativ](../../../configuration/cache/level-two-cache.md#stale-cache-options) i _Konfigurationshandboken_.

Under distributionen bör du se följande rader i [bygg- och distributionsloggen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/log-locations#build-and-deploy-logs):

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'valkey' is 8.0
[2022-08-17 01:13:40] INFO: Version of service 'valkey-session' is 8.0
[2022-08-17 01:13:40] INFO: valkey-session will be used for the session if it was not overridden by SESSION_CONFIGURATION.
```

## Cachekomprimering

Om du använder mer än 6 GB Valkey `maxmemory` kan du använda cachekomprimering för att minska det utrymme som används av nycklarna. Tänk på att det finns en kompromiss med prestanda på klientsidan. Om du har extra processorer föreslår Adobe att du aktiverar dem. Se [Använd Valkey för sessionslagring](../../../configuration/cache/valkey-session.md) i _Konfigurationshandboken_.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # do not compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~70%)
```
