---
title: env.php reference
description: Läs mer om konfigurationsvärden och avsnitt för filen env.php i Adobe Commerce. Upptäck miljöinställningar och konfigurationsalternativ.
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 0%

---

# env.php reference

Filen `env.php` innehåller följande avsnitt:

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
| `directories` | Inställningar för mappning av Commerce-kataloger |
| `downloadable_domains` | Lista över hämtningsbara domäner |
| `install` | Installationsdatum |
| `lock` | Lås providerinställningar |
| `MAGE_MODE` | Programläget [&#128279;](../bootstrap/application-modes.md) |
| `queue` | Inställningar för [Meddelandeköer](../queues/manage-message-queues.md) |
| `resource` | Mappning av resursnamn till en anslutning |
| `session` | Sessionslagringsdata |
| `system` | Inaktiverar fältet för redigering i administratören |
| `x-frame-options` | Inställning för [x-frame-options](../security/xframe-options.md) |

## serverdel

Konfigurera **frontName** för Commerce-administratörens URL med noden `backend` i env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cache

Konfigurera redis-sida och standardcachelagring genom att använda noden `cache` i filen `env.php`.

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

Läs mer om olika [cachetyper](../cli/manage-cache.md).

## containers_wait_for_messages

Ange om konsumenterna ska fortsätta att avfråga meddelanden om antalet bearbetade meddelanden är mindre än värdet `max_messages`. Standardvärdet är `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

Följande alternativ är tillgängliga:

- `1` - Konsumenterna fortsätter att bearbeta meddelanden från meddelandekön tills det `max_messages` -värde som anges i filen `env.php` nås innan TCP-anslutningen stängs och konsumentprocessen avslutas. Om kön töms innan värdet `max_messages` uppnås väntar konsumenten på att fler meddelanden ska komma fram.

  Vi rekommenderar den här inställningen för stora handlare eftersom ett konstant meddelandeflöde förväntas och förseningar i bearbetningen är oönskade.

- `0` - Konsumenterna bearbetar tillgängliga meddelanden i kön, stänger TCP-anslutningen och avslutar. Konsumenterna väntar inte på att ytterligare meddelanden ska skickas till kön, även om antalet bearbetade meddelanden är mindre än värdet `max_messages` som anges i filen `env.php`. Detta kan hjälpa till att förhindra problem med kronijobb som orsakas av långa förseningar i meddelandeköhanteringen.

  Vi rekommenderar den här inställningen för mindre handlare som inte förväntar sig ett konstant meddelandeflöde och som föredrar att spara datorresurser i utbyte mot mindre förseningar när det inte finns några meddelanden på några dagar.

## cron

Aktivera eller inaktivera cron-jobb för Commerce-programmet. Kronijobb är som standard aktiverade. Om du vill inaktivera dem lägger du till konfigurationen `cron` i filen `env.php` och anger värdet till `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Var försiktig när du inaktiverar cron-jobb. När de är inaktiverade körs inte de viktiga processer som krävs av Commerce.

Läs mer om [Crons](../cli/configure-cron-jobs.md).

## kryptera

Commerce använder en krypteringsnyckel för att skydda lösenord och andra känsliga data. Den här nyckeln genereras under installationsprocessen.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Läs mer om [Krypteringsnyckel](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/security/encryption-key) i användarhandboken för _Commerce_.

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

Definierar standardanslutningen för meddelandeköer. Värdet kan vara `db`, `amqp`, `stomp` eller ett anpassat kösystem som `redismq`. Om du anger något annat värde än `db` måste meddelandeköprogrammet först installeras och konfigureras. Annars kommer meddelanden inte att behandlas korrekt.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

För STOMP (ActiveMQ Artemis):

```conf
'queue' => [
    'default_connection' => 'stomp'
]
```

Om `queue/default_connection` anges i systemfilen `env.php` används den här anslutningen för alla meddelandeköer via systemet, såvida inte en viss anslutning definieras i en `queue_topology.xml`-, `queue_publisher.xml`- eller `queue_consumer.xml`-fil.
Om `queue/default_connection` till exempel är `amqp` i `env.php` men en `db`-anslutning har angetts i kökonfigurationens XML-filer för en modul, använder modulen MySQL som meddelandehanterare.

## kataloger

Valfria katalogmappningsalternativ som måste anges när webbservern är konfigurerad för att hantera Commerce-programmet från katalogen `/pub` för [förbättrad säkerhet](../../installation/tutorials/docroot.md).

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

Läs mer om [Hämtningsbara domäner](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/cli-reference/commerce-on-premises#downloadabledomainsadd).

## installera

Installationsdatumet för Commerce-programmet.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## lock

Lås providerinställningar konfigureras med noden `lock`.

Läs mer om [Lås providerkonfiguration](../../installation/tutorials/lock-provider.md).

## MAGE_MODE

Distributionsläget kan konfigureras i den här noden.

```conf
'MAGE_MODE' => 'developer'
```

Läs mer om [programlägen](../cli/set-mode.md).

## kö

Meddelandekökonfigurationer är tillgängliga i den här noden. Du kan konfigurera RabbitMQ (AMQP) eller ActiveMQ Artemis (STOMP) som meddelandehanterare.

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-broker"],
    'order.created' => [publisher="default-broker"],
  ]
]
```

Läs mer om [Meddelandekö](https://developer.adobe.com/commerce/php/development/components/message-queues/).

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

Sessionskonfigurationer lagras i noden `session`.

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

Med den här noden låser Commerce konfigurationsvärdena i filen `env.php` och inaktiverar sedan fältet i administratören.

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



## Lägg till variabler i filkonfigurationen

Du kan ställa in eller åsidosätta alla konfigurationsalternativ (variabel med värde) med miljövariabler på operativsystemnivå (OS).

Konfigurationen `env.php` lagras i en matris med kapslade nivåer. Om du vill konvertera en kapslad arraysökväg till en sträng för systemmiljövariabler sammanfogar du varje nyckel i sökvägen med två understreck, `__`, överkant och prefix med `MAGENTO_DC_`.

Låt oss till exempel konvertera hanteraren för sessionssparande från konfigurationen `env.php` till en systemvariabel.

```conf
'session' => [
  'save' => 'files'
],
```

Sammanfogade med `__` och överraderade nycklar blir `SESSION__SAVE`.

Sedan prefixar vi det med `MAGENTO_DC_` för att hämta det resulterande variabelnamnet `MAGENTO_DC_SESSION__SAVE` för operativsystemsmiljön.

```shell
export MAGENTO_DC_SESSION__SAVE=files
```

Som ett annat exempel konverterar vi en skalär sökväg för konfigurationsalternativ för `env.php`.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

>[!INFO]
>
>Variabelnamnet ska översättas, men värdet är skiftlägeskänsligt och ska bevaras som det är dokumenterat.

Det är bara att versalera det och prefix med `MAGENTO_DC_` för att ta emot det slutliga systemmiljövariabelnamnet `MAGENTO_DC_X-FRAME-OPTIONS`.

```shell
export MAGENTO_DC_X-FRAME-OPTIONS=SAMEORIGIN
```

>[!INFO]
>
>Observera att `env.php`-innehåll kommer att ha prioritet framför operativsystemets miljövariabler.

## Åsidosätt filkonfiguration med variabler

Om du vill åsidosätta de befintliga `env.php`-konfigurationsalternativen med en OS-miljövariabel måste konfigurationens matriselement vara JSON-kodat och anges som ett värde för `MAGENTO_DC__OVERRIDE` OS-variabeln.

När `MAGENTO_DC__OVERRIDE` har angetts åsidosätter Commerce-ramverket motsvarande värden i `env.php`-filen och läser konfigurationen direkt från systemvariabeln. Värdena i filen `env.php` förblir oförändrade men ignoreras för de åsidosatta konfigurationsavsnitten.

>[!IMPORTANT]
>
>Variabeln `MAGENTO_DC__OVERRIDE` åsidosätter fullständigt de angivna konfigurationsavsnitten i filen `env.php`. Det här beteendet skiljer sig från enskilda `MAGENTO_DC_`-variabler, som har lägre prioritet än värdena i filen `env.php`.

Om du behöver åsidosätta flera konfigurationsalternativ måste du montera alla i en enda array före JSON-kodning.

Vi kan till exempel åsidosätta följande `env.php`-konfigurationer:

```conf
'session' => [
  'save' => 'files'
],
'x-frame-options' => 'SAMEORIGIN'
```

JSON-kodad text i ovanstående array blir
`{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}`.

Ange det nu som värdet för OS-variabeln `MAGENTO_DC__OVERRIDE`.

```shell
export MAGENTO_DC__OVERRIDE='{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}'
```

>[!INFO]
>
>Kontrollera att den JSON-kodade arrayen är korrekt citerad och/eller escape-konverterad om det behövs, så att operativsystemet inte kan skada den kodade strängen.