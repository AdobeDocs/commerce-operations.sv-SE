---
source-git-commit: 631735eceb3609edd743c682291f373f6b01b399
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---
# MariaDB-konfigurationsinställningar

Omindexering av MariaDB 10.4 och 10.6 tar längre tid jämfört med tidigare versioner av MariaDB eller MySQL. För att påskynda omindexeringen rekommenderar vi att du ställer in följande konfigurationsparametrar för MariaDB:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

Om prestandaförsämringar inte har att göra med indexering efter uppgradering till MariaDB 10.6 bör du överväga att aktivera [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) inställning. Till exempel: `--query-cache-type=ON`.

Utöver dessa rekommendationer bör du rådfråga databasadministratören om hur du konfigurerar följande parametrar:

>[!NOTE]
>
>De här inställningarna är endast tillgängliga för lokala distributioner. Adobe Commerce på molninfrastrukturkunder har inte tillgång till dessa inställningar.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
