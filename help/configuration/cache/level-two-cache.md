---
title: L2-cachekonfiguration
description: Lär dig att konfigurera L2-cachen.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# L2-cachekonfiguration

Cachelagring ger en minskning av nätverkstrafiken mellan fjärrcachelagringen och Commerce-programmet. En standard Commerce-instans överför cirka 300 kb per begäran, och trafiken kan snabbt öka till över cirka 1 000 förfrågningar i vissa situationer.

Om du vill minska nätverksbandbredden till Redis sparar du cachedata lokalt på varje webbnod och använder fjärrcachen i två syften:

- Kontrollera cachedataversionen och se till att den senaste cachen lagras lokalt
- Överför det senaste cacheminnet från fjärrdatorn till den lokala datorn

Commerce lagrar den hashade dataversionen i Redis, med suffixet &#39;:hash&#39; som tillägg till den vanliga nyckeln. Om det finns ett föråldrat lokalt cacheminne överförs data till den lokala datorn med ett cacheminne.

>[!INFO]
>
>För Adobe Commerce i molninfrastruktur kan du använda [driftsättningsvariabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) för L2-cachekonfiguration.

## Konfigurationsexempel

Använd följande exempel för att ändra eller ersätta det befintliga cacheavsnittet i `app/etc/env.php` -fil.

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
                ],
                'use_stale_cache' => false,
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

- `backend` är implementeringen av L2-cache.
- `backend_options` är L2-cachekonfigurationen.
   - `remote_backend` är implementeringen av fjärrcachen: Redis eller MySQL.
   - `remote_backend_options` är fjärrcachekonfigurationen.
   - `local_backend` är den lokala cacheimplementeringen: `Cm_Cache_Backend_File`
   - `local_backend_options` är den lokala cachekonfigurationen.
      - `cache_dir` är ett filcachespecifikt alternativ för den katalog där det lokala cacheminnet lagras.
   - `use_stale_cache` är en flagga som aktiverar eller inaktiverar användning av inaktuell cache.

Adobe rekommenderar att du använder Redis för fjärrcachelagring (`\Magento\Framework\Cache\Backend\Redis`) och `Cm_Cache_Backend_File` för lokal cachelagring av data i delat minne, med: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe rekommenderar att du använder [`cache preload`](redis-pg-cache.md#redis-preload-feature) eftersom det drastiskt minskar trycket på Redis. Glöm inte att lägga till suffixet &#39;:hash&#39; för förinläsningsnycklar.

## Alternativ för inaktuell cache

Börja med [!DNL Commerce] 2.4, `use_stale_cache` kan förbättra prestandan i vissa specifika fall.

I allmänhet accepteras en kompromiss med låsväntetider från prestandasidan, men ju fler block eller cacheminne handlaren har desto mer tid går det att vänta på lås. I vissa scenarier kan du vänta **antal tangenter** \* **timeout för sökning** hur lång tid processen tar. I vissa sällsynta fall kan handlaren ha hundratals nycklar i `Block/Config` cache, så även liten timeout för låsningen kan kosta sekunder.

Inaktuell cache fungerar bara med L2-cache. Med en inaktuell cache kan du skicka en inaktuell cache, medan en ny genereras i en parallell process. Om du vill aktivera inaktuell cache lägger du till `'use_stale_cache' => true` till högsta konfigurationen av L2-cachen.

Adobe rekommenderar att du aktiverar `use_stale_cache` endast för cachetyper som drar störst nytta av det, inklusive:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

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
                ],
                'use_stale_cache' => false,
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
