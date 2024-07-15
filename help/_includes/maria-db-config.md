---
source-git-commit: d7926b9150137813b1161581bb1d7884a6fe11e9
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---
# MariaDB-konfigurationsinställningar

Omindexering av MariaDB 10.4 och 10.6 tar längre tid jämfört med tidigare versioner av MariaDB eller MySQL. För att påskynda omindexeringen rekommenderar vi att du ställer in följande konfigurationsparametrar för MariaDB:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

Om prestandaförsämringar inte har att göra med indexering efter uppgradering till MariaDB 10.6 bör du aktivera inställningen [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type). Exempel: `--query-cache-type=ON`.

Innan du uppgraderar Adobe Commerce i molninfrastrukturprojekt kan du behöva uppgradera MariaDB ([se MariaDB upgrade best practices](../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md)).

Exempel:

* Adobe Commerce 2.4.6 med MariaDB version 10.5.1 eller senare
* Adobe Commerce 2.3.5 med MariaDB version 10.3 eller tidigare

Utöver dessa rekommendationer bör du rådfråga databasadministratören om hur du konfigurerar följande parametrar:

>[!NOTE]
>
>De här inställningarna är endast tillgängliga för lokala distributioner. Adobe Commerce på molninfrastrukturkunder har inte tillgång till dessa inställningar.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
