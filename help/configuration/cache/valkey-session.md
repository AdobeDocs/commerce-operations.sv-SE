---
title: Använd Valkey för sessionslagring
description: Lär dig hur du konfigurerar Valkey för sessionslagring.
feature: Configuration, Cache
exl-id: 986ddb5c-8fc5-4210-8a41-a29e3a7625b7
source-git-commit: bc0274074c0254f649af2f9e2b288017ac82ce9b
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 1%

---


# Använd Valkey för sessionslagring

>[!IMPORTANT]
>
>Du måste [installera Valkey](config-valkey.md#install-valkey) innan du kan fortsätta.

Adobe Commerce tillhandahåller kommandoradsalternativ för att konfigurera Valkey-sessionslagring.

Kör kommandot `setup:config:set` och ange Valkey-specifika parametrar.

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-<parameter_name>=<parameter_value>...
```

- `--session-save=valkey` aktiverar Valkey-sessionslagring. Om den här funktionen redan är aktiverad utelämnar du den här parametern.

- `--session-save-valkey-<parameter_name>=<parameter_value>` är en lista över parameter-/värdepar som konfigurerar sessionslagring:

| Kommandoradsparameter | Parameternamn | Betydelse | Standardvärde |
|----------------------------------------------|--- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| session-save-valkey-host | värd | Fullständigt kvalificerat värdnamn, IP-adress eller absolut sökväg om UNIX-socketar används. | localhost |
| session-save-valkey-port | port | Valkey server listen port. | 6379 |
| session-save-valkey-password | lösenord | Anger ett lösenord om din Valkey-server kräver autentisering. | tom |
| session-save-valkey-timeout | timeout | Anslutningens timeout, i sekunder. | 2,5 |
| session-save-valkey-persistent-id | persistent_identifier | Unik sträng för att aktivera beständiga anslutningar (till exempel sess-db0).<br>[Kända fel med phpredis och php-fpm](https://github.com/phpredis/phpredis/issues/70). |
| session-save-valkey-db | databas | Unikt Valkey-databasnummer som rekommenderas för att skydda mot dataförlust.<br><br>**Viktigt**: Om du använder Valkey för mer än en typ av cachelagring måste databasnumren vara olika. Vi rekommenderar att du tilldelar standardvärdet för cachningsdatabasen till `0`, sidcachningsdatabasnumret till `1` och sessionslagringsdatabasnumret till `2`. | 0 |
| session-save-valkey-compression-threshold | compression_threshold | Ange `0` om du vill inaktivera komprimering (rekommenderas när `suhosin.session.encrypt = On`). | 2048 |
| session-save-valkey-compression-lib | compression_library | Alternativ: gzip, lzf, lz4 eller snappy. | gzip |
| session-save-valkey-log-level | log_level | Ange något av följande, i ordning från minst utförlig till mest utförlig:<ul><li>0 (kris: endast de allvarligaste felen)<li>1 (varning: omedelbar åtgärd krävs)<li>2 (kritiskt: programkomponenten är inte tillgänglig)<li>3 (fel: körningsfel, inte kritiska men måste övervakas)<li>4 (varning: ytterligare information rekommenderas)<li>5 (observera: normalt men signifikant tillstånd)<li>6 (info: informationsmeddelanden)<li>7 (debug: the most information for development or testing only)</ul> | 1 |
| session-save-valkey-max-concurrency | max_concurrency | Maximalt antal processer som kan vänta på ett lås i en session. För stora produktionskluster ska detta anges till minst 10 % av antalet PHP-processer. | 6 |
| session-save-valkey-break-after-front | break_after_front_tend | Antal sekunder att vänta innan du försöker bryta låset för frontend-sessionen (dvs. storefront). | 5 |
| session-save-valkey-break-after-adminhtml | break_after_adminhtml | Antal sekunder att vänta innan låset för en adminhtml-session (d.v.s. Admin) bryts. | 30 |
| session-save-valkey-first-life | first_life | Livstid, i sekunder, för session för icke-bots vid första skrivning, eller använd `0` för att inaktivera. | 600 |
| session-save-valkey-bot-first-life | bot_first_life | Livstid, i sekunder, för session för bots vid första skrivning, eller använd `0` för att inaktivera. | 60 |
| session-save-valkey-bot-life | bot_life | Livstid, i sekunder, för session för start vid efterföljande skrivningar, eller använd `0` för att inaktivera. | 7200 |
| session-save-valkey-disable-locking | disable_locking | Inaktivera sessionslåsning helt. | 0 (false) |
| session-save-valkey-min-life | min_livstid | Minsta sessionstid, i sekunder. | 60 |
| session-save-valkey-max-life | max_livstid | Maximal sessionstid, i sekunder. | 2592000 (720 timmar) |
| session-save-valkey-sentinel-master | sentinel_master | Valkey Sentinel master name. | tom |
| session-save-valkey-sentinel-servers | sentinel_servers | Lista med Valkey Sentinel-servrar, kommaavgränsade. | tom |
| session-save-valkey-sentinel-verify-master | sentinel_verify_master | Verifiera flaggan Valkey Sentinel master status. | 0 (false) |
| session-save-valkey-sentinel-connect-retry | sentinel_connect_reentries | Anslutningsförsök för sändare. | 5 |

## Exempel

I följande exempel anges Valkey som sessionsdatalager, värden ställs in på `127.0.0.1`, loggnivån ställs in på `4` och databasnumret ställs in på `2`. Alla andra parametrar ställs in på standardvärdet.

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-host=127.0.0.1 --session-save-valkey-log-level=4 --session-save-valkey-db=2
```

### Resultat

Commerce lägger till rader som liknar följande i `<magento_root>app/etc/env.php`:

```php
'session' => [
    'save' => 'valkey',
    'redis' => [
        'host' => '127.0.0.1',
        'port' => '6379',
        'password' => '',
        'timeout' => '2.5',
        'persistent_identifier' => '',
        'database' => '2',
        'compression_threshold' => '2048',
        'compression_library' => 'gzip',
        'log_level' => '4',
        'max_concurrency' => '6',
        'break_after_frontend' => '5',
        'break_after_adminhtml' => '30',
        'first_lifetime' => '600',
        'bot_first_lifetime' => '60',
        'bot_lifetime' => '7200',
        'disable_locking' => '0',
        'min_lifetime' => '60',
        'max_lifetime' => '2592000',
    ],
],
```

>[!INFO]
>
>TTL för sessionsposter använder värdet för cookie-livstid, som har konfigurerats i administratören. Om cookie-livstid är inställd på `0` (standardvärdet är `3600`) upphör Valkey-sessionerna att gälla i det antal sekunder som anges i min_livstid (standardvärdet är `60`). Skillnaden beror på skillnader i hur Valkey- och sessionscookies tolkar ett livstidsvärde på `0`. Om du inte vill använda det beteendet ökar du värdet för min_livstid.

## Verifiera Valkey-anslutning

Om du vill verifiera att Valkey och Commerce fungerar ihop på rätt sätt loggar du in på servern där Valkey körs, öppnar en terminal och använder antingen kommandot `valkey-cli monitor` eller kommandot `redis-cli ping`.

### Valkey monitor command

```bash
valkey-cli monitor
```

Exempel på sessionslagringsutdata:

```
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Valkey ping-kommando

```bash
valkey-cli ping
```

Det förväntade svaret är: `PONG`.

Om båda kommandona slutförs, ställs Valkey in korrekt.

### Inspektera komprimerade data

[RESP.app](https://flathub.org/apps/app.resp.RESP) har stöd för automatisk dekomprimering av Commerce 2-sessions- och sidcache och visar PHP-sessionsdata i ett läsbart format för att inspektera komprimerade sessionsdata och sidcache.
