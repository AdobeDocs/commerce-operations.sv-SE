---
title: Använd Valkey för standardcache
description: Lär dig att konfigurera Valkey som standardcache för Adobe Commerce.
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
source-git-commit: dea0ad57a8c4525be9bc442708bdd2495f28d72d
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 0%

---


# Använd Valkey för standardcache

Commerce innehåller kommandoradsalternativ för att konfigurera Valkey-sidan och standardcachning. Du kan konfigurera cachelagring genom att redigera filen `<Commerce-install-dir>app/etc/env.php`, men du bör använda kommandoraden, särskilt för inledande konfigurationer. Kommandoraden ger validering och säkerställer att konfigurationen är syntaktiskt korrekt.

Du måste [installera Valkey](config-redis.md#install-redis) innan du kan fortsätta.

## Konfigurera standardcachelagring för Valkey

Kör kommandot `setup:config:set` och ange parametrar för standardcachelagring av Valkey.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey` aktiverar värdenas standardcachelagring. Om den här funktionen redan har aktiverats utelämnar du den här parametern.

- `--cache-backend-valkey-<parameter>=<value>` är en lista med nyckelvärdepar som konfigurerar standardcachelagring:

>[!NOTE]
>
>Från och med **Adobe Commerce 2.4.9-alpha2** har **Valkey** officiellt ersatt Redis i CLI-verktygen på grund av ändrade licensalternativ. Valkey är en gaffel till Redis och har nästan identiska funktioner. För **version 2.4.8 och tidigare** är de CLI-kommandon som används för att konfigurera Valkey desamma som för Redis, vilket ger sömlös bakåtkompatibilitet och förenklar migrering eller stöd för dubbla miljöer. I följande exempel visas det Valkey-specifika kommandot.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-valkey-<parameter>=<value>...
```

| Kommandoradsparameter | Värde | Betydelse | Standardvärde |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | server | Fullständigt kvalificerat värdnamn, IP-adress eller absolut sökväg till en UNIX-socket. Standardvärdet `127.0.0.1` anger att Valkey är installerat på Commerce-servern. | `127.0.0.1` |
| `cache-backend-valkey-port` | port | avlyssningsport för Valkey-server | `6379` |
| `cache-backend-valkey-db` | databas | Krävs om du använder Valkey för både standardcache och helsidescache. Du måste ange databasnumret för en av cacherna. I det andra cacheminnet används `0` som standard.<br><br>**Viktigt**: Om du använder Valkey för mer än en typ av cachelagring måste databasnumren vara olika. Adobe rekommenderar att du tilldelar standardvärdet för cachningsdatabasen till `0`, sidcachningsdatabasnumret till `1` och sessionslagringsdatabasnumret till `2`. | `0` |
| `cache-backend-valkey-password` | lösenord | När du konfigurerar ett Valkey-lösenord aktiveras en av de inbyggda säkerhetsfunktionerna: kommandot `auth`, som kräver att klienter autentiserar för att få åtkomst till databasen. Lösenordet har konfigurerats direkt i Valkey-konfigurationsfilen: `/etc/valkey/valkey.conf` | |

### Exempel, kommando

I följande exempel aktiveras standardcachelagring för Valkey, värddatorn ställs in på `127.0.0.1` och databasnumret tilldelas till `0`. Valkey använder standardvärden för alla andra parametrar.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

>[!NOTE]
>
>Från och med **Adobe Commerce 2.4.9-alpha2** har **Valkey** officiellt ersatt Redis i CLI-verktygen på grund av ändrade licensalternativ. Valkey är en gaffel till Redis och har nästan identiska funktioner. För **version 2.4.8 och tidigare** är de CLI-kommandon som används för att konfigurera Valkey desamma som för Redis, vilket ger sömlös bakåtkompatibilitet och förenklar migrering eller stöd för dubbla miljöer. I följande exempel visas det Valkey-specifika kommandot.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Konfigurera sidcache

Kör kommandot `setup:config:set` med ytterligare parametrar för att konfigurera Valkey-sidcache på Commerce.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

Med följande parametrar:

- `--page-cache=valkey` aktiverar cachelagring av Valkey-sidor. Om den här funktionen redan har aktiverats utelämnar du den här parametern.

- `--page-cache-valkey-<parameter>=<value>` är en lista med nyckel-och-värde-par som konfigurerar sidcache:

>[!NOTE]
>
>Från och med **Adobe Commerce 2.4.9-alpha2** har **Valkey** officiellt ersatt Redis i CLI-verktygen på grund av ändrade licensalternativ. Valkey är en gaffel till Redis och har nästan identiska funktioner. För **version 2.4.8 och tidigare** är de CLI-kommandon som används för att konfigurera Valkey desamma som för Redis, vilket ger sömlös bakåtkompatibilitet och förenklar migrering eller stöd för dubbla miljöer. I följande exempel visas det Valkey-specifika kommandot.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

| Kommandoradsparameter | Värde | Betydelse | Standardvärde |
|------------------------------| --------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | server | Fullständigt kvalificerat värdnamn, IP-adress eller absolut sökväg till en UNIX-socket. Standardvärdet `127.0.0.1` anger att Valkey är installerat på Commerce-servern. | `127.0.0.1` |
| `page-cache-valkey-port` | port | Valkey server listen port. | `6379` |
| `page-cache-valkey-db` | databas | Krävs om du använder Valkey för både standardcache och helsidescache. Du måste ange databasnumret för en av cacherna. I det andra cacheminnet används `0` som standard.<br/>**Viktigt**: Om du använder Valkey för mer än en typ av cachelagring måste databasnumren vara olika. Vi rekommenderar att du tilldelar standardvärdet för cachningsdatabasen till `0`, sidcachningsdatabasnumret till `1` och sessionslagringsdatabasnumret till `2`. | `0` |
| `page-cache-valkey-password` | lösenord | När du konfigurerar ett Valkey-lösenord aktiveras en av de inbyggda säkerhetsfunktionerna: kommandot `auth`, som kräver att klienter autentiserar för att få åtkomst till databasen. Konfigurera lösenordet i Valkey-konfigurationsfilen: `/etc/valkey/valkey.conf` | |

### Exempel, kommando

I följande exempel aktiveras cachelagring av Valkey-sidor, värddatorn ställs in på `127.0.0.1` och databasnumret tilldelas till `1`. Alla andra parametrar ställs in på standardvärdet.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

>[!NOTE]
>
>Från och med **Adobe Commerce 2.4.9-alpha2** har **Valkey** officiellt ersatt Redis i CLI-verktygen på grund av ändrade licensalternativ. Valkey är en gaffel till Redis och har nästan identiska funktioner. För **version 2.4.8 och tidigare** är de CLI-kommandon som används för att konfigurera Valkey desamma som för Redis, vilket ger sömlös bakåtkompatibilitet och förenklar migrering eller stöd för dubbla miljöer. I följande exempel visas det Valkey-specifika kommandot.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-valkey-db=1
```

## Resultat

Som ett resultat av de två exempelkommandona lägger Commerce till rader som liknar följande i `<Commerce-install-dir>app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

## Ny implementering av värdenyckelcache

[!BADGE 2.4.9-alpha]{type=Negative tooltip="Finns endast i 2.4.9-alfa."}

Från och med Adobe Commerce 2.4.9 rekommenderar Adobe att du använder implementeringen av Valkey-cache: `\Magento\Framework\Cache\Backend\Valkey`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Förinläsningsfunktion för Valkey

Eftersom Commerce lagrar konfigurationsdata i Valkey-cachen kan du förhandsladda data som återanvänds mellan sidorna. Analysera data som överförs från Valkey till Commerce för att hitta nycklar som måste vara förinlästa. Adobe föreslår att data läses in i förväg på alla sidor, till exempel `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` och `DB_IS_UP_TO_DATE`.

Valkey använder `pipeline` för sammansatta inläsningsbegäranden. Nycklar ska innehålla databasprefixet. Om till exempel databasprefixet är `061_` ser förinläsningsnyckeln ut så här: `061_SYSTEM_DEFAULT`

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => 'valkey',
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

När du använder förinläsningsfunktionen med en L2-cache måste du lägga till suffixet `:hash` till dina nycklar. L2-cachen överför bara hash-värdet av data, inte själva data.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Parallell generering

Från och med Commerce 2.4.0 introducerade Adobe alternativet `allow_parallel_generation` för användare som inte vill vänta på lås.
Det är inaktiverat som standard och Adobe rekommenderar att du inaktiverar det tills du har för många konfigurationer och/eller block.

**Så här aktiverar du parallell generering**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Eftersom det är en flagga kan du inte inaktivera den med ett kommando. Du måste ange konfigurationsvärdet manuellt till `false`:

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

## Verifiera Valkey-anslutning

Om du vill verifiera att Valkey och Commerce fungerar ihop på rätt sätt loggar du in på servern som kör Valkey, öppnar en terminal och använder antingen kommandot `valkey-cli monitor` eller kommandot `redis-cli ping`.

### Valkey monitor command

```bash
valkey-cli monitor
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

### Valkey ping-kommando

```bash
redis-cli ping
```

Det förväntade svaret är: `PONG`

Om båda kommandona slutförs, ställs Valkey in korrekt.

### Inspektera komprimerade data

[RESP.app](https://flathub.org/apps/app.resp.RESP) har stöd för automatisk dekomprimering av Commerce 2-sessions- och sidcache och visar PHP-sessionsdata i ett läsbart format för att inspektera komprimerade sessionsdata och sidcache.
