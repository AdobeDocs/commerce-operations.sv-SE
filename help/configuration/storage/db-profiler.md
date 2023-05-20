---
title: Konfigurera databasprofileraren
description: Se ett exempel på hur du konfigurerar utdata för databasprofileraren.
badge: label="Contributed by Atish Goswami" type="Informative" url="https://github.com/atishgoswami" tooltip="Atish Goswami"
exl-id: 87780db5-6e50-4ebb-9591-0cf22ab39af5
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Konfigurera databasprofileraren

I Commerce-databasprofileraren visas alla frågor som har implementerats på en sida, inklusive tiden för varje fråga och vilka parametrar som har tillämpats.

## Steg 1: Ändra distributionskonfigurationen

Ändra `<magento_root>/app/etc/env.php` för att lägga till följande referens till [databasprofilerarklass](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

Ett exempel följer:

```php?start_inline=1
 'db' =>
  array (
    'table_prefix' => '',
    'connection' =>
    array (
      'default' =>
      array (
        'host' => 'localhost',
        'dbname' => 'magento',
        'username' => 'magento',
        'password' => 'magento',
        'model' => 'mysql4',
        'engine' => 'innodb',
        'initStatements' => 'SET NAMES utf8;',
        'active' => '1',
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
      ),
    ),
  ),
```

## Steg 2: Konfigurera utdata

Konfigurera utdata i Commerce-programmets startfil; det här kan vara `<magento_root>/pub/index.php` eller så finns den i en virtuell värdkonfiguration för webbservern.

I följande exempel visas resultatet i en tabell med tre kolumner:

- Total tid (visar den totala tiden för att köra alla frågor på sidan)
- SQL (visar alla SQL-frågor; radhuvudet visar antalet frågor)
- Frågeparametrar (visar parametrarna för varje SQL-fråga)

Om du vill konfigurera utdata lägger du till följande efter `$bootstrap->run($app);` i din Bootstrap-fil:

```php?start_inline=1
/** @var \Magento\Framework\App\ResourceConnection $res */
$res = \Magento\Framework\App\ObjectManager::getInstance()->get('Magento\Framework\App\ResourceConnection');
/** @var Magento\Framework\DB\Profiler $profiler */
$profiler = $res->getConnection('read')->getProfiler();
echo "<table cellpadding='0' cellspacing='0' border='1'>";
echo "<tr>";
echo "<th>Time <br/>[Total Time: ".$profiler->getTotalElapsedSecs()." secs]</th>";
echo "<th>SQL [Total: ".$profiler->getTotalNumQueries()." queries]</th>";
echo "<th>Query Params</th>";
echo "</tr>";
foreach ($profiler->getQueryProfiles() as $query) {
    /** @var Zend_Db_Profiler_Query $query*/
    echo '<tr>';
    echo '<td>', number_format(1000 * $query->getElapsedSecs(), 2), 'ms', '</td>';
    echo '<td>', $query->getQuery(), '</td>';
    echo '<td>', json_encode($query->getQueryParams()), '</td>';
    echo '</tr>';
}
echo "</table>";
```

## Steg 3: Visa resultaten

Gå till valfri sida i din butik eller Admin för att se resultatet. Ett exempel följer:

![Exempelresultat för databasprofilerare](../../assets/configuration/db-profiler-results.png)
