---
title: Migrera data
description: Lär dig hur du börjar migrera data från Magento 1 till Magento 2 med  [!DNL Data Migration Tool].
exl-id: f4ea8f6a-21f8-4db6-b598-c5efecec254f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Migrera data

Innan du börjar utför du följande steg:

1. Logga in på programservern som [ägare av filsystemet](../../../installation/prerequisites/file-system/overview.md).
1. Ändra till programinstallationskatalogen eller se till att den har lagts till i systemet `PATH`.

Mer information finns i avsnittet om [de första stegen](overview.md#first-steps).

## Kör datamigreringskommandot

Kör följande för att börja migrera data:

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Var:

* `[-a|--auto]` är ett valfritt argument som förhindrar att migreringen stoppas när integritetskontrollfel påträffas.

* `[-r|--reset]` är ett valfritt argument som startar migreringen från början. Du kan använda det här argumentet för att testa migrering.

* `{<path to config.xml>}` är den absoluta filsystemsökvägen till `config.xml`. Det här argumentet krävs

I det här steget skapar [!DNL Data Migration Tool] ytterligare tabeller och utlösare för migreringstabellerna i Magento 1-databasen. De används i migreringssteget [inkrementellt/delta](delta.md). Ytterligare tabeller innehåller information om ändrade poster efter den slutliga migreringen. Databasutlösare används för att fylla i dessa extra tabeller, så om en ny åtgärd utförs för den aktuella tabellen (en post läggs till/ändras/tas bort), sparar databasutlösaren information om den här åtgärden i den extra tabellen. När vi kör en deltamigreringsprocess kontrollerar [!DNL Data Migration Tool] om det finns obearbetade poster i tabellerna och migrerar nödvändigt innehåll till Magento 2-databasen.

Varje ny tabell innehåller:

* `m2_cl`-prefix
* `INSERT`, `UPDATE`, `DELETE` händelseutlösare.

För `sales_flat_order` skapar till exempel [!DNL Data Migration Tool]:

* `m2_cl_sales_flat_order`-tabell:

  ```sql
  CREATE TABLE `m2_cl_sales_flat_order` (
    `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
    `operation` text COMMENT 'Operation',
    `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
    PRIMARY KEY (`entity_id`)
  ) COMMENT='m2_cl_sales_flat_order';
  ```

* `trg_sales_flat_order_after_insert`, `trg_sales_flat_order_after_update`, `trg_sales_flat_order_after_delete` utlösare:

  ```sql
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_insert` AFTER INSERT ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'INSERT')ON DUPLICATE KEY UPDATE operation = 'INSERT';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_update` AFTER UPDATE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'UPDATE') ON DUPLICATE KEY UPDATE operation = 'UPDATE';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_delete` AFTER DELETE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (OLD.entity_id, 'DELETE')ON DUPLICATE KEY UPDATE operation = 'DELETE';
    END
  ;;
  ```

>[!NOTE]
>
>[!DNL Data Migration Tool] sparar det aktuella förloppet när det körs. Om fel eller en användaråtgärd hindrar det från att köras, återupptar verktyget förloppet vid det senast fungerande tillståndet. Använd argumentet `--reset` om du vill tvinga [!DNL Data Migration Tool] att köras från början. I så fall rekommenderar vi att du återställer databassdumpen Magento 2 för att förhindra att tidigare migrerade data dupliceras.


## Möjliga konsekvensfel

Under körning kan [!DNL Data Migration Tool] rapportera inkonsekvenser mellan Magento 1- och Magento 2-databaser och visa meddelanden som följande:

* `Source documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Source document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Destination document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Incompatibility in data. Source document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`
* `Incompatibility in data. Destination document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`

Mer information och rekommendationer finns i avsnittet [Felsökning](https://support.magento.com/hc/en-us/articles/360033020451) i den här guiden.

## Nästa migreringssteg

[Migrera ändringar](delta.md)
