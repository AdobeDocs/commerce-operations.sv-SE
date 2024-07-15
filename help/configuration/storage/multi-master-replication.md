---
title: Databasreplikering
description: Se fördelarna med att konfigurera databasreplikering.
recommendations: noCatalog
exl-id: 0e41dca0-5a23-4d12-96fe-241c511ae366
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Databasreplikering

{{ee-only}}

{{deprecate-split-db}}

Att konfigurera databasreplikering ger följande fördelar:

- Ger säkerhetskopiering av data
- Aktiverar dataanalys utan att masterdatabasen påverkas
- Skalbarhet

MySQL-databaser replikeras asynkront, vilket innebär att slavar inte behöver anslutas permanent för att kunna ta emot uppdateringar från huvudservern.

## Konfigurera databasreplikering

En fördjupad diskussion om databasreplikering ligger utanför den här handbokens räckvidd. Om du vill konfigurera den kan du läsa en resurs som:

- [MySQL-dokumentation](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [Så här konfigurerar du Master Slave-replikering i MySQL (digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce tillhandahåller exempelkonfigurationer för MySQL för dina slavdatabaser. En enkel konfiguration tillhandahålls med klassen `ResourceConnections` `README.md`.

Följande är mer avancerat och finns endast i din information:

```php
   return array (
      //...
      'db' =>
         array (
            'connection' =>
               array (
                  'indexer' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                        'persistent' => NULL,
                     ),
                  'default' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-master-host',
                        'dbname' => 'checkout',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-master-host',
                        'dbname' => 'sales',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
               ),
            'slave_connection' =>
               array (
                  'default' =>
                     array (
                        'host' => 'default-slave-host',
                        'dbname' => 'magento',
                        'username' => 'read_only',
                        'password' => 'password',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-slave-host',
                        'dbname' => 'checkout',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-slave-host',
                        'dbname' => 'sales',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  ),
               'table_prefix' => '',
   ),
   //.......
```

## Prestandaförbättring

Om du vill förbättra prestanda för replikering av masterslav kan du filtrera vissa tabeller på slavinstanser. Vi rekommenderar att du filtrerar alla temporära tabeller med namnmönstret `search\_tmp\_%` som används för katalogsökning.

Om du vill göra det lägger du till följande rad i din `my.cnf`-fil på dina slavförekomster:

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
