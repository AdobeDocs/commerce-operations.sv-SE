---
title: env.php reference
description: Se en lista med värden för filen env.php.
source-git-commit: fe5e16d44213d1864a62230029e9e206eecd1717
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---


# env.php reference

The `env.php` filen innehåller följande avsnitt:

| Namn | Beskrivning |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | Inställningar för området Admin |
| `cache` | Konfigurera redis-sida och standardcache |
| `cache_types` | Lagringsinställningar för cache |
| `consumers_wait_for_messages` | Konfigurera hur konsumenter bearbetar meddelanden från meddelandekön |
| `cron` | Aktivera eller inaktivera cron-jobb |
| `crypt` | Krypteringsnyckeln för kryptografiska funktioner |
| `db` | Inställningar för databasanslutning |
| `default_connection` | Standardanslutning för meddelandeköer |
| `directories` | Mappningsinställningar för Commerce-kataloger |
| `downloadable_domains` | Lista över hämtningsbara domäner |
| `install` | Installationsdatum |
| `lock` | Lås providerinställningar |
| `MAGE_MODE` | The [programläge](../bootstrap/application-modes.md) |
| `queue` | [Meddelandeköer](../queues/manage-message-queues.md) inställningar |
| `resource` | Mappning av resursnamn till en anslutning |
| `session` | Sessionslagringsdata |
| `system` | Inaktiverar fältet för redigering i administratören |
| `x-frame-options` | Inställning för [x-frame-options][x-frame-options] |

## serverdel

Konfigurera **frontName** för Commerce Admin url med `backend` nod i env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cache

Konfigurera redis-sida och standardcachelagring med `cache` noden i `env.php` -fil.

```conf
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
]
```

Läs mer i [Redis-konfiguration](../cache/redis-pg-cache.md).

## cache_types

Alla konfigurationer av cachetyper är tillgängliga från den här noden.

```conf
'cache_types' => [
  'config' => 1,
  'layout' => 1,
  'block_html' => 1,
  'collections' => 1,
  'reflection' => 1,
  'db_ddl' => 1,
  'compiled_config' => 1,
  'eav' => 1,
  'customer_notification' => 1,
  'config_integration' => 1,
  'config_integration_api' => 1,
  'full_page' => 1,
  'config_webservice' => 1,
  'translate' => 1,
  'vertex' => 1
]
```

Läs mer om olika [Cachetyper](../cli/manage-cache.md).

## containers_wait_for_messages

Ange om konsumenterna ska fortsätta att avfråga meddelanden om antalet bearbetade meddelanden är mindre än `max_messages` värde. Standardvärdet är `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

Följande alternativ är tillgängliga:

- `1`—Konsumenterna fortsätter att bearbeta meddelanden från meddelandekön tills de når `max_messages` det värde som anges i `env.php` innan TCP-anslutningen stängs och konsumentprocessen avslutas. Om kön töms innan användaren når `max_messages` värdet, väntar konsumenten på fler meddelanden.

   Vi rekommenderar den här inställningen för stora handlare eftersom ett konstant meddelandeflöde förväntas och förseningar i bearbetningen är oönskade.

- `0`—Konsumenterna bearbetar tillgängliga meddelanden i kön, stänger TCP-anslutningen och avslutar. Konsumenterna väntar inte på att ytterligare meddelanden ska skickas till kön, även om antalet bearbetade meddelanden är mindre än `max_messages` det värde som anges i `env.php` -fil. Detta kan hjälpa till att förhindra problem med kronijobb som orsakas av långa förseningar i meddelandeköhanteringen.

   Vi rekommenderar den här inställningen för mindre handlare som inte förväntar sig ett konstant meddelandeflöde och som föredrar att spara datorresurser i utbyte mot mindre förseningar när det inte finns några meddelanden på några dagar.

## cron

Aktivera eller inaktivera cron-jobb för Commerce-programmet. Kronijobb är som standard aktiverade. Om du vill inaktivera dem lägger du till `cron` till `env.php` och ange värdet till `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Var försiktig när du inaktiverar cron-jobb. När de är inaktiverade kommer viktiga processer som krävs av Commerce-programmet inte att köras.

Läs mer om [Kroner](../cli/configure-cron-jobs.md).

## kryptera

Handel använder en krypteringsnyckel för att skydda lösenord och andra känsliga data. Den här nyckeln genereras under installationsprocessen.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Läs mer om [Krypteringsnyckel](https://docs.magento.com/user-guide/system/encryption-key.html) i _Handbok för Commerce-användare_.

## db

Alla databaskonfigurationer är tillgängliga i den här noden.

```conf
'db' => [
  'table_prefix' => '',
  'connection' => [
    'default' => [
      'host' => 'localhost',
      'dbname' => 'magento_db',
      'username' => 'root',
      'password' => 'admin123',
      'model' => 'mysql4',
      'engine' => 'innodb',
      'initStatements' => 'SET NAMES utf8;',
      'active' => '1'
    ]
  ]
]
```

## default_connection

Definierar standardanslutningen för meddelandeköer. Värdet kan vara `db`, `amqp`eller ett anpassat kösystem som `redismq`. Om du anger något annat värde än `db`måste meddelandeköprogrammet först installeras och konfigureras. Annars kommer meddelanden inte att behandlas korrekt.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

If `queue/default_connection` anges i systemet `env.php` den här anslutningen används för alla meddelandeköer via systemet, såvida inte en viss anslutning definieras i en `queue_topology.xml`, `queue_publisher.xml` eller `queue_consumer.xml` -fil.
Om `queue/default_connection` är `amqp` in `env.php` men en `db` anslutningen anges i kökonfigurations-XML-filerna för en modul, använder modulen MySQL som meddelandehanterare.

## kataloger

Valfria katalogmappningsalternativ som måste anges när webbservern är konfigurerad för att hantera Commerce-appen från `/pub` katalog för [förbättrad säkerhet](../../installation/tutorials/docroot.md).

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domains

En lista över tillgängliga hämtningsbara domäner i den här noden. Ytterligare domäner kan läggas till, tas bort eller listas med CLI-kommandon.

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

Läs mer om [Hämtningsbara domäner](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## installera

Installationsdatumet för Commerce-programmet.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## lock

Lås providerinställningar konfigureras med `lock` nod.

Läs mer om [Lås providerkonfiguration](../../installation/tutorials/lock-provider.md).

## MAGE_MODE

Distributionsläget kan konfigureras i den här noden.

```conf
'MAGE_MODE' => 'developer'
```

Läs mer om [programlägen](../cli/set-mode.md).

## kö

Meddelandekökonfigurationer är tillgängliga i den här noden.

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

Läs mer om [Meddelandekö][message-queue].

## resurs

Resurskonfigurationsinställningar är tillgängliga i den här noden.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## session

Sessionskonfigurationer lagras i `session` nod.

```conf
'session' => [
  'save' => 'files'
],
```

Läs mer om [Session](../storage/sessions.md).

## x-frame-options

Rubriken för x-frame-options kan konfigureras med den här noden.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

Läs mer om [x-frame-options](../security/xframe-options.md).

## system

Med den här noden låses konfigurationsvärdena i `env.php` och sedan inaktiverar fältet i administratören.

```conf
'system' => [
  'default' => [
    'web' => [
      'secure' => [
          'base_url' => 'https://magento.test/'
      ]
    ]
  ]
```

Läs mer i [env-php-config-set](../cli/set-configuration-values.md).

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
