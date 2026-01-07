---
title: Använd Redis för standardcache
description: Lär dig hur du konfigurerar Redis som standardcache för Adobe Commerce. Upptäck kommandoradskonfiguration, konfigurationsalternativ och valideringstekniker.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: ee4a873a73e8fd747e7d4c8e157327fab1074cc9
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---

# Använd Redis för standardcache

Commerce tillhandahåller kommandoradsalternativ för att konfigurera Redis-sidan och standardcachning. Du kan konfigurera cachelagring genom att redigera filen `<Commerce-install-dir>app/etc/env.php`, men du bör använda kommandoraden, särskilt för inledande konfigurationer. Kommandoraden ger validering och säkerställer att konfigurationen är syntaktiskt korrekt.

Du måste [installera Redis](config-redis.md#install-redis) innan du kan fortsätta.

>[!NOTE]
>
>För Commerce-instanser som finns på EC2 kan du använda AWS ElastiCache i stället för en lokal Redis-instans. Se [Konfigurera elasticache för EC2-instanser](redis-elasticache-for-ec2.md).

## Konfigurera standardcachning för Redis

Kör kommandot `setup:config:set` och ange parametrar som är specifika för Redis standardcachning.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Med följande parametrar:

- `--cache-backend=redis` aktiverar Redis standardcachning. Om den här funktionen redan har aktiverats utelämnar du den här parametern.

- `--cache-backend-redis-<parameter>=<value>` är en lista med nyckel-och-värde-par som konfigurerar standardcachelagring:

| Kommandoradsparameter | Värde | Betydelse | Standardvärde |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | Fullständigt kvalificerat värdnamn, IP-adress eller absolut sökväg till en UNIX-socket. Standardvärdet 127.0.0.1 anger att Redis är installerat på Commerce-servern. | `127.0.0.1` |
| `cache-backend-redis-port` | port | Redis-serverlyssningsport | `6379` |
| `cache-backend-redis-db` | databas | Krävs om du använder Redis för både standardcache och helsidescache. Du måste ange databasnumret för en av cacherna. I det andra cacheminnet används 0 som standard.<br><br>**Viktigt**: Om du använder Redis för mer än en typ av cachelagring måste databasnumren vara olika. Vi rekommenderar att du tilldelar standardvärdet för cachningsdatabasen till 0, sidcachningsdatabasnumret till 1 och sessionslagringsdatabasnumret till 2. | `0` |
| `cache-backend-redis-password` | lösenord | När du konfigurerar ett Redis-lösenord aktiveras en av de inbyggda säkerhetsfunktionerna: kommandot `auth`, som kräver att klienterna autentiseras för att få åtkomst till databasen. Lösenordet har konfigurerats direkt i Redis konfigurationsfil: `/etc/redis/redis.conf` | |
| `--cache-backend-redis-use-lua` | use_lua | Aktivera eller inaktivera LUA. <br><br>**LUA**: Med Lua kan vi köra en del av programlogiken i Redis, vilket förbättrar prestanda och säkerställer datakonsekvens genom dess atomära körning. | `0` |
| `--cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | Aktivera eller inaktivera LUA för skräpinsamling. <br><br>**LUA**: Med Lua kan vi köra en del av programlogiken i Redis, vilket förbättrar prestanda och säkerställer datakonsekvens genom dess atomära körning. | `1` |

### Exempel, kommando

I följande exempel aktiveras Redis standardcachelagring, värden ställs in på `127.0.0.1` och databasnumret tilldelas till 0. Redis använder standardvärden för alla andra parametrar.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Konfigurera Redis-sidcache

Om du vill konfigurera Redis-sidcache på Commerce kör du kommandot `setup:config:set` med ytterligare parametrar.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Med följande parametrar:

- `--page-cache=redis` aktiverar Redis-sidcache. Om den här funktionen redan har aktiverats utelämnar du den här parametern.

- `--page-cache-redis-<parameter>=<value>` är en lista med nyckel-och-värde-par som konfigurerar sidcache:

| Kommandoradsparameter | Värde | Betydelse | Standardvärde |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | Fullständigt kvalificerat värdnamn, IP-adress eller absolut sökväg till en UNIX-socket. Standardvärdet 127.0.0.1 anger att Redis är installerat på Commerce-servern. | `127.0.0.1` |
| `page-cache-redis-port` | port | Redis-serverlyssningsport | `6379` |
| `page-cache-redis-db` | databas | Krävs om du använder Redis för både standardcache och helsidescache. Du måste ange databasnumret för en av cacherna. I det andra cacheminnet används 0 som standard.<br/>**Viktigt**: Om du använder Redis för mer än en typ av cachelagring måste databasnumren vara olika. Vi rekommenderar att du tilldelar standardvärdet för cachningsdatabasen till 0, sidcachningsdatabasnumret till 1 och sessionslagringsdatabasnumret till 2. | `0` |
| `page-cache-redis-password` | lösenord | När du konfigurerar ett Redis-lösenord aktiveras en av de inbyggda säkerhetsfunktionerna: kommandot `auth`, som kräver att klienterna autentiseras för att få åtkomst till databasen. Konfigurera lösenordet i Redis-konfigurationsfilen: `/etc/redis/redis.conf` | |

### Exempel, kommando

I följande exempel aktiveras Redis sidcache-lagring, värddatorn ställs in på `127.0.0.1` och databasnumret tilldelas till 1. Alla andra parametrar ställs in på standardvärdet.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Granska konfigurationen av Commerce-miljön

Kör kommandona för att konfigurera Redis-cachelagring, uppdaterar Commerce-miljökonfigurationen (`<Commerce-install-dir>app/etc/env.php`):

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

## Konfigurera ytterligare cachealternativ

I det här avsnittet beskrivs hur du aktiverar valfria konfigurationsinställningar som är inaktiverade som standard.

### Förinläsningsfunktion för Redis

Eftersom Commerce lagrar konfigurationsdata i Redis-cachen kan vi förinläsa data som återanvänds mellan sidorna. Analysera data som överförs från Redis till Commerce för att hitta nycklar som måste läsas in i förväg. Vi föreslår att data som läses in på varje sida läses in i förväg, till exempel `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.

Redis använder `pipeline` för att sammanfoga inläsningsbegäranden. Nycklar ska innehålla databasprefixet. Om databasprefixet är `061_` ser preload-nyckeln ut så här: `061_SYSTEM_DEFAULT`

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

Om du använder förinläsningsfunktionen med L2-cachen ska du inte glömma att lägga till suffixet `:hash` i nycklarna, eftersom L2-cachen bara överför hashen av data, inte själva data:

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### Parallell generering

Eliminera väntan på lås genom att aktivera alternativet `allow_parallel_generation`.

Det här alternativet är inaktiverat som standard och Adobe rekommenderar att du inaktiverar det tills du har ett stort antal konfigurationer eller block.

**Så här aktiverar du parallell generering**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Eftersom det här alternativet är en flagga kan du inte inaktivera det med ett kommando. Du måste ange konfigurationsvärdet manuellt till `false`:

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

## Kontrollera Redis-anslutningen

Om du vill verifiera att Redis och Commerce fungerar tillsammans loggar du in på servern som kör Redis, öppnar en terminal och använder kommandot Redis monitor eller ping.

### Redis-bildskärm, kommando

```bash
redis-cli monitor
```

Exempel på sidcachning:

```
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

Om du vill inspektera komprimerade sessionsdata och sidcache stöder [RESP.app](https://flathub.org/apps/details/app.resp.RESP) automatisk dekomprimering av Commerce 2 Session och Page Cache och visar PHP-sessionsdata i en läsbar form.
