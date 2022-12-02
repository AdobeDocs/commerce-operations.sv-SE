---
title: Använd Redis för standardcache
description: Lär dig konfigurera Redis som standardcache för Adobe Commerce och Magento Open Source.
source-git-commit: 47d513e7ca51ad7dbc149d0f1e076f673452918c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Använd Redis för standardcache

Commerce innehåller kommandoradsalternativ för att konfigurera Redis-sidan och standardcachning. Även om du kan konfigurera cachning genom att redigera `<Commerce-install-dir>app/etc/env.php` rekommenderas att du använder kommandoraden, särskilt för ursprungliga konfigurationer. Kommandoraden ger validering och säkerställer att konfigurationen är syntaktiskt korrekt.

Du måste [installera Redis](config-redis.md#install-redis) innan du fortsätter.

## Konfigurera standardcachning för Redis

Kör `setup:config:set` och ange parametrar som är specifika för Redis standardcachning.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Med följande parametrar:

- `--cache-backend=redis` används för standardcachning i Redis. Om den här funktionen redan har aktiverats utelämnar du den här parametern.

- `--cache-backend-redis-<parameter>=<value>` är en lista med nyckel-och-värde-par som konfigurerar standardcachelagringen:

| Kommandoradsparameter | Värde | Betydelse | Standardvärde |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | Fullständigt kvalificerat värdnamn, IP-adress eller absolut sökväg till en UNIX-socket. Standardvärdet 127.0.0.1 anger att Redis är installerat på Commerce-servern. | `127.0.0.1` |
| `cache-backend-redis-port` | port | Redis-serverlyssningsport | `6379` |
| `cache-backend-redis-db` | databas | Krävs om du använder Redis för både standardcache och helsidescache. Du måste ange databasnumret för en av cacherna; det andra cacheminnet använder 0 som standard.<br><br>**Viktigt**: Om du använder Redis för mer än en typ av cachning måste databasnumren vara olika. Vi rekommenderar att du tilldelar standardvärdet för cachningsdatabasen till 0, sidcachningsdatabasnumret till 1 och sessionslagringsdatabasnumret till 2. | `0` |
| `cache-backend-redis-password` | lösenord | När du konfigurerar ett Redis-lösenord aktiveras en av de inbyggda säkerhetsfunktionerna: den `auth` som kräver att klienterna autentiserar för att få åtkomst till databasen. Lösenordet konfigureras direkt i Redis konfigurationsfil: `/etc/redis/redis.conf` |  |

### Exempel, kommando

I följande exempel aktiveras Redis standardcachelagring och värden ställs in på `127.0.0.1`och tilldelar databasnumret 0. Redis använder standardvärden för alla andra parametrar.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Konfigurera Redis-sidcache

Om du vill konfigurera Redis-sidcachning i Commerce kör du `setup:config:set` med ytterligare parametrar.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Med följande parametrar:

- `--page-cache=redis` aktiverar Redis sidcache-lagring. Om den här funktionen redan har aktiverats utelämnar du den här parametern.

- `--page-cache-redis-<parameter>=<value>` är en lista med nyckel-och-värde-par som konfigurerar sidcachning:

| Kommandoradsparameter | Värde | Betydelse | Standardvärde |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | Fullständigt kvalificerat värdnamn, IP-adress eller absolut sökväg till en UNIX-socket. Standardvärdet 127.0.0.1 anger att Redis är installerat på Commerce-servern. | `127.0.0.1` |
| `page-cache-redis-port` | port | Redis-serverlyssningsport | `6379` |
| `page-cache-redis-db` | databas | Krävs om du använder Redis för både standardcache och helsidescache. Du måste ange databasnumret för en av cacherna; det andra cacheminnet använder 0 som standard.<br/>**Viktigt**: Om du använder Redis för mer än en typ av cachning måste databasnumren vara olika. Vi rekommenderar att du tilldelar standardvärdet för cachningsdatabasen till 0, sidcachningsdatabasnumret till 1 och sessionslagringsdatabasnumret till 2. | `0` |
| `page-cache-redis-password` | lösenord | När du konfigurerar ett Redis-lösenord aktiveras en av de inbyggda säkerhetsfunktionerna: den `auth` som kräver att klienterna autentiserar för att få åtkomst till databasen. Konfigurera lösenordet i Redis-konfigurationsfilen: `/etc/redis/redis.conf` |  |

### Exempel, kommando

I följande exempel aktiveras Redis-sidcache och värden ställs in på `127.0.0.1`och tilldelar databasnumret 1. Alla andra parametrar ställs in på standardvärdet.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Resultat

Som ett resultat av de två exempelkommandona lägger Commerce till rader som liknar följande: `<Commerce-install-dir>app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
],
```

## Använda AWS ElastiCache med din EC2-instans

Från och med Commerce 2.4.3 kan instanser på Amazon EC2 använda en AWS ElastiCache i stället för en lokal Redis-instans.

>[!WARNING]
>
>Det här avsnittet fungerar bara för Commerce-instanser som körs på Amazon EC2 VPC. Det fungerar inte för lokala anläggningar.

### Konfigurera ett Redis-kluster

Efter [konfigurera ett Redis-kluster i AWS](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/)konfigurerar du EC2-instansen att använda ElastiCache.

1. [Skapa ett ElastiCache-kluster](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) i samma region och VPC för EC2-instansen.
1. Kontrollera anslutningen.

   - Öppna en SSH-anslutning till din EC2-instans
   - Installera Redis-klienten på EC2-instansen:

      ```bash
      sudo apt-get install redis
      ```

   - Lägg till en inkommande regel till EC2-säkerhetsgruppen: Typ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Lägg till en inkommande regel i säkerhetsgruppen för kluster i ElastiCache: Typ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Anslut till Redis CLI:

      ```bash
      redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
      ```

### Konfigurera Commerce för att använda klustret

Handeln stöder flera typer av cachelagringskonfigurationer. Vanligtvis är cachelagringskonfigurationerna uppdelade mellan klientdel och serverdel. Cachelagring av frontend klassificeras som `default`, används för alla cachetyper. Du kan anpassa eller dela upp i cacheminnen på lägre nivå för att få bättre prestanda. En vanlig Redis-konfiguration separerar standardcachen och sidcachen till sin egen Redis-databas (RDB).

Kör `setup` för att ange Redis-slutpunkter.

Så här konfigurerar du Commerce for Redis som standardcachelagring:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Så här konfigurerar du Commerce för Redis-sidcache:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Så här konfigurerar du Commerce att använda Redis för sessionslagring:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Verifiera anslutning

**Verifiera att Commerce pratar med ElastiCache**:

1. Öppna en SSH-anslutning till Commerce EC2-instansen.
1. Starta Redis-skärmen.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Öppna en sida i Commerce UI.
1. Verifiera [cacheutdata](#verify-redis-connection) i terminalen.

## Ny Redis-cacheimplementering

Från och med Commerce 2.3.5 rekommenderas att implementeringen av Redis-cachen används: `\Magento\Framework\Cache\Backend\Redis`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Förinläsningsfunktion för Redis

Eftersom Commerce lagrar konfigurationsdata i Redis-cachen kan vi förinläsa data som återanvänds mellan sidorna. Om du vill hitta nycklar som måste vara förinlästa analyserar du data som överförs från Redis till Commerce. Vi föreslår att du läser in data i förväg på alla sidor, som `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.

Redis använder `pipeline` för sammansatta lastbegäranden. Nycklarna ska innehålla databasprefixet. om till exempel databasprefixet är `061_`ser förinläsningsnyckeln ut så här: `061_SYSTEM_DEFAULT`

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'password' => '',
                'compress_data' => '1',
                'compression_lib' => '',
                'preload_keys' => [
                    '061_EAV_ENTITY_TYPES',
                    '061_GLOBAL_PLUGIN_LIST',
                    '061_DB_IS_UP_TO_DATE',
                    '061_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => '061_'
        ]
    ]
]
```

Om du använder förinläsningsfunktionen med L2-cachen, glöm inte att lägga till `:hash` suffix till dina nycklar, eftersom L2-cache bara överför hash-informationen, inte själva data:

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Parallell generering

Från och med version 2.4.0 introducerade vi `allow_parallel_generation` för de användare som vill slippa vänta på lås.
Det är inaktiverat som standard och vi rekommenderar att du inaktiverar det tills du har för många konfigurationer och/eller block.

**Aktivera parallell generering**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Eftersom det är en flagga kan du inte inaktivera den med ett kommando. Du måste ange konfigurationsvärdet manuellt till `false`:

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
                'backend_options' => [
                    'server' => 'redis',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                    'compression_lib' => ''
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

## Bekräfta Redis-anslutning

Om du vill verifiera att Redis och Commerce fungerar tillsammans loggar du in på servern som kör Redis, öppnar en terminal och använder kommandot Redis monitor eller ping.

### Redis-bildskärm, kommando

```bash
redis-cli monitor
```

Exempel på sidcachning:

```terminal
1476826133.810090 [0 127.0.0.1:52366] "select" "1"
1476826133.816293 [0 127.0.0.1:52367] "select" "0"
1476826133.817461 [0 127.0.0.1:52367] "hget" "zc:k:ea6_GLOBAL__DICONFIG" "d"
1476826133.829666 [0 127.0.0.1:52367] "hget" "zc:k:ea6_DICONFIG049005964B465901F774DB9751971818" "d"
1476826133.837854 [0 127.0.0.1:52367] "hget" "zc:k:ea6_INTERCEPTION" "d"
1476826133.868374 [0 127.0.0.1:52368] "select" "1"
1476826133.869011 [0 127.0.0.1:52369] "select" "0"
1476826133.869601 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_DEFAULT__10__235__32__1080MAGENTO2" "d"
1476826133.872317 [0 127.0.0.1:52369] "hget" "zc:k:ea6_INITIAL_CONFIG" "d"
1476826133.879267 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL_PRIMARY_PLUGIN_LIST" "d"
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Redis ping, kommando

```bash
redis-cli ping
```

Det förväntade svaret är: `PONG`

Om båda kommandona lyckades är Redis korrekt konfigurerat.

### Inspektera komprimerade data

Om du vill inspektera komprimerade sessionsdata och sidcachen, [RESP.app](https://flathub.org/apps/details/app.resp.RESP) har stöd för automatisk dekomprimering av Commerce 2 Session och Page Cache och visar PHP-sessionsdata i en läsbar form.
