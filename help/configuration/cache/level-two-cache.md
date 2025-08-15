---
title: L2-cachekonfiguration
description: Lär dig att konfigurera L2-cachen.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: ba3c656566af47f16f58f476d7bc9f4781bb0234
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# L2-cachekonfiguration

Cachelagring ger en minskning av nätverkstrafiken mellan lagringsutrymmet i fjärrcachen och Commerce-programmet. En standardinstans i Commerce överför cirka 300 kb per begäran, och trafiken kan snabbt öka till över cirka 1 000 förfrågningar i vissa situationer.

Om du vill minska nätverksbandbredden till Redis sparar du cachedata lokalt på varje webbnod och använder fjärrcachen i två syften:

- Kontrollera cachedataversionen och se till att den senaste cachen lagras lokalt
- Överför den senaste cachen från fjärrdatorn till den lokala datorn

Commerce lagrar den hash-kodade dataversionen i Redis, med suffixet :hash som läggs till i den vanliga nyckeln. Om det finns ett föråldrat lokalt cacheminne överförs data till den lokala datorn med ett cacheminne.

>[!INFO]
>
>För Adobe Commerce i molninfrastruktur kan du använda [distribuera variabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) för L2-cachekonfiguration.

## Konfigurationsexempel

Använd följande exempel för att ändra eller ersätta det befintliga cacheavsnittet i filen `app/etc/env.php`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

Var:

- `backend` är L2-cacheimplementeringen.
- `backend_options` är L2-cachekonfigurationen.
   - `remote_backend` är fjärrexplementeringen av cachen: Redis eller MySQL.
   - `remote_backend_options` är fjärrcachekonfigurationen.
   - `local_backend` är den lokala cacheimplementeringen: `Cm_Cache_Backend_File`
   - `local_backend_options` är den lokala cachekonfigurationen.
   - `cache_dir` är ett filcachespecifikt alternativ för den katalog där det lokala cacheminnet lagras.

Adobe rekommenderar att Redis används för fjärrcachelagring (`\Magento\Framework\Cache\Backend\Redis`) och `Cm_Cache_Backend_File` för lokal cachelagring av data i delat minne, med: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe rekommenderar att du använder funktionen [`cache preload`](redis-pg-cache.md#redis-preload-feature) eftersom den drastiskt minskar trycket på Redis. Glöm inte att lägga till suffixet :hash för förinläsningsnycklar.

## Alternativ för inaktuell cache

Från och med [!DNL Commerce] 2.4 kan alternativet `use_stale_cache` förbättra prestandan i vissa specifika fall.

I allmänhet accepteras en kompromiss med låsväntetider från prestandasidan, men ju fler block eller cacheminne handlaren har desto mer tid går det att vänta på lås. I vissa scenarier kan du vänta i **antal tangenter** \* **timeout** så länge som processen pågår. I vissa sällsynta fall kan handlaren ha hundratals nycklar i cachen `Block/Config`, så även en liten timeout för låsningen kan kosta sekunder.

Inaktuell cache fungerar bara med L2-cache. Med ett inaktuellt cacheminne kan du skicka ett inaktuellt cacheminne, medan ett nytt genereras i en parallell process. Om du vill aktivera inaktuell cache lägger du till `'use_stale_cache' => true` i den översta konfigurationen för L2-cachen.

Adobe rekommenderar att du bara aktiverar alternativet `use_stale_cache` för de cachetyper som drar störst nytta av det, bland annat:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobe rekommenderar inte att du aktiverar alternativet `use_stale_cache` för cachetypen `default`.

I följande kod visas en exempelkonfiguration:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ],
         'stale_cache_enabled' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ],
                'use_stale_cache' => true,
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled']
    ],
],
```
