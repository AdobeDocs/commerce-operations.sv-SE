---
title: Konfigurera databasprofileraren
description: Se ett exempel på hur du konfigurerar utdata för databasprofileraren.
feature: Configuration, Storage
badge: label="Bidragen av Atish Goswami" type="Informative" url="https://github.com/atishgoswami" tooltip="Brittiska Goswami"
exl-id: 87780db5-6e50-4ebb-9591-0cf22ab39af5
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Konfigurera databasprofileraren

Commerce databasprofilerare visar alla frågor som är implementerade på en sida, inklusive tiden för varje fråga och vilka parametrar som tillämpades.

## Steg 1: Ändra distributionskonfigurationen

Ändra `<magento_root>/app/etc/env.php` om du vill lägga till följande referens till [klassen för databasprofiler](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

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

Konfigurera utdata i startfilen för Commerce-programmet. Detta kan vara `<magento_root>/pub/index.php` eller finnas i en virtuell värdkonfiguration för webbservern.

I följande exempel visas resultatet i en tabell med tre kolumner:

- Total tid (visar den totala tiden för att köra alla frågor på sidan)
- SQL (visar alla SQL-frågor; radhuvudet visar antalet frågor)
- Frågeparametrar (visar parametrarna för varje SQL-fråga)

Om du vill konfigurera utdata lägger du till följande efter raden `$bootstrap->run($app);` i Bootstrap-filen:

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

## Steg 3: Visa resultatet

Gå till valfri sida i din butik eller Admin för att se resultatet. Ett exempel följer:

![Exempelresultat för databasprofileraren](../../assets/configuration/db-profiler-results.png)
