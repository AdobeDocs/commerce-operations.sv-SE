---
title: L2-cachekonfiguration
description: Lär dig att konfigurera L2-cachen.
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '405'
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
>För Adobe Commerce om molninfrastruktur bör du överväga de bästa metoderna i [Utökad Redis-cacheimplementering](https://support.magento.com/hc/en-us/articles/360049292532) supportartikel.

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

Börja med [!DNL Commerce] 2.4, `stale_cache` kan förbättra prestandan i vissa specifika fall.

I allmänhet accepteras en kompromiss med låsväntetider från prestandasidan, men ju fler block eller cacheminne handlaren har desto mer tid går det att vänta på lås. I vissa scenarier kan du vänta **antal tangenter** \* **timeout för sökning** hur lång tid processen tar. I vissa sällsynta fall kan handlaren ha hundratals nycklar i `Block/Config` cache, så även liten timeout för låsningen kan kosta sekunder.

Inaktuell cache fungerar bara med L2-cache. Med en inaktuell cache kan du skicka en inaktuell cache, medan en ny genereras i en parallell process. Om du vill aktivera inaktuell cache lägger du till `'use_stale_cache' => true` till högsta konfigurationen av L2-cachen.
