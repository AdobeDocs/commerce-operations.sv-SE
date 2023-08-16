---
title: Loggdatabasaktivitet
description: Konfigurera Commerce för att logga databasaktivitet med loggningsgränssnittet.
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# Loggdatabasaktivitet

I följande exempel visas hur du loggar databasaktivitet med [`Magento\Framework\DB\LoggerInterface`][interface], som har två implementeringar:

- Inget loggas (standard): [`Magento\Framework\DB\Logger\Quiet`][quiet]
- Loggar till `var/log` katalog: [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>Du kan använda Commerce CLI för att [aktivera och inaktivera databasloggning](../cli/enable-logging.md#database-logging).

Så här ändrar du standardkonfigurationen för `\Magento\Framework\DB\Logger\LoggerProxy`, redigera `app/etc/di.xml`.

Ändra först standardvärdena för `loggerAlias` och `logCallStack` argument till:

```xml
<type name="Magento\Framework\DB\Logger\LoggerProxy">
    <arguments>
        <argument name="loggerAlias" xsi:type="const">Magento\Framework\DB\Logger\LoggerProxy::LOGGER_ALIAS_FILE</argument>
        <argument name="logAllQueries" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_LOG_EVERYTHING</argument>
        <argument name="logQueryTime" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_QUERY_TIME_THRESHOLD</argument>
        <argument name="logCallStack" xsi:type="boolean">false</argument>
    </arguments>
</type>
```

Sedan anger du filsökvägen för `Magento\Framework\DB\Logger\File`:

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

Slutligen kompilerar du koden med:

```bash
bin/magento setup:di:compile
```

Och rensa cachen med:

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
