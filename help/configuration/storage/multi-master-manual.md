---
title: Konfigurera överordnad databaser manuellt
description: Mer information om hur du konfigurerar lösningen för delad databas manuellt.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1388'
ht-degree: 0%

---


# Konfigurera överordnad databaser manuellt

{{ee-only}}

{{deprecate-split-db}}

Om Commerce-programmet redan är i produktion eller om du redan har installerat anpassad kod eller komponenter kan du behöva konfigurera delade databaser manuellt. Innan du fortsätter kontaktar du Adobe Commerce Support för att se om det är nödvändigt.

Manuell delning av databaser innefattar:

- Skapa [utcheckning](https://glossary.magento.com/checkout) OMS-databaser (Order Management System)
- Kör en serie SQL-skript som:

   - Släpp sekundärnycklar
   - Säkerhetskopiera försäljnings- och offertdatabastabeller
   - Flytta tabeller från huvuddatabasen till försäljnings- och offertdatabaserna

>[!WARNING]
>
>Om någon anpassad kod använder JOIN-koder med tabeller i försäljnings- och offertdatabaserna, _inte_ använda delade databaser. Om du är osäker kan du kontakta författarna till en anpassad kod eller tillägg för att kontrollera att deras kod inte använder JOIN-koder.

I det här avsnittet används följande namnkonventioner:

- Huvuddatabasnamnet är `magento` och dess användarnamn och lösenord är båda `magento`
- Namnet på offertdatabasen är `magento_quote` och dess användarnamn och lösenord är båda `magento_quote`

   Offertdatabasen kallas även _utcheckning_ databas.

- Försäljningsdatabasens namn är `magento_sales` och dess användarnamn och lösenord är båda `magento_sales`

   Försäljningsdatabasen kallas också OMS-databasen.

>[!INFO]
>
>I den här guiden antas att alla tre databaserna finns på samma värd som Commerce-programmet. Det är dock upp till dig att välja var databaserna ska hittas och vad de ska namnges. Vi hoppas att våra exempel gör instruktionerna enklare att följa.

## Säkerhetskopiera handelssystemet

Adobe rekommenderar starkt att du säkerhetskopierar din aktuella databas och ditt filsystem så att du kan återställa den om du får problem under processen.

**Säkerhetskopiera systemet**:

1. Logga in på din Commerce-server som eller växla till [ägare av filsystem](../../installation/prerequisites/file-system/overview.md).
1. Ange följande kommandon:

   ```bash
   magento setup:backup --code --media --db
   ```

1. Fortsätt med nästa avsnitt.

## Ställ in ytterligare överordnad databaser

I det här avsnittet beskrivs hur du skapar databasinstanser för försäljning och [citat](https://glossary.magento.com/quote) tabeller.

**Skapa offertdatabaser för försäljning och OMS**:

1. Logga in på databasservern som vilken användare som helst.
1. Ange följande kommando för att komma till en MySQL-kommandotolk:

   ```bash
   mysql -u root -p
   ```

1. Ange MySQL `root` användarens lösenord när du uppmanas till det.
1. Ange följande kommandon i den ordning som visas för att skapa databasinstanser med namnet `magento_quote` och `magento_sales` med samma användarnamn och lösenord:

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Retur `exit` för att avsluta kommandotolken.

1. Verifiera databaserna, en åt gången:

   offertdatabas:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   ```bash
   mysql -u magento_quote -p
   ```

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Om MySQL-övervakaren visas har du skapat databasen på rätt sätt. Om ett fel visas upprepar du de föregående kommandona.

1. Fortsätt med nästa avsnitt.

## Konfigurera försäljningsdatabasen

I det här avsnittet beskrivs hur du skapar och kör SQL-skript som ändrar databastabeller och säkerhetskopierar data från dessa tabeller.

Tabellnamn för försäljningsdatabas börjar med:

- `salesrule_`
- `sales_`
- `magento_sales_`
- The `magento_customercustomattributes_sales_flat_order` tabellen påverkas också

>[!INFO]
>
>Det här avsnittet innehåller skript med specifika databastabellnamn. Om du har utfört anpassningar eller om du vill se en fullständig lista över tabeller innan du utför åtgärder på dem läser du [Referensskript](#reference-scripts).

Mer information finns i:

- [Skapa SQL-skript för försäljningsdatabas](#create-sales-database-sql-scripts)
- [Säkerhetskopiera säljdata](#back-up-sales-data)

### Skapa SQL-skript för försäljningsdatabas

Skapa följande SQL-skript på en plats som är tillgänglig för den användare som du loggar in på din Commerce-server. Om du till exempel loggar in eller kör kommandon som `root`kan du skapa skripten i `/root/sql-scripts` katalog.

#### Ta bort sekundärnycklar

Det här skriptet tar bort sekundärnycklar som refererar till icke-försäljningsregister från försäljningsdatabasen.

Skapa följande skript och ge det ett namn som `1_foreign-sales.sql`. Ersätt `<your main DB name>` med namnet på databasen.

```sql
use <your main DB name>;
ALTER TABLE salesrule_coupon_aggregated_order DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated_updated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_usage DROP FOREIGN KEY SALESRULE_COUPON_USAGE_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_customer_group DROP FOREIGN KEY SALESRULE_CSTR_GROUP_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_customer DROP FOREIGN KEY SALESRULE_CUSTOMER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_label DROP FOREIGN KEY SALESRULE_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_ATTR_ID_EAV_ATTR_ATTR_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRODUCT_ATTRIBUTE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE salesrule_website DROP FOREIGN KEY SALESRULE_WEBSITE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_DAILY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_MONTHLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_YEARLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_DAILY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_MONTHLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_YEARLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo_grid DROP FOREIGN KEY SALES_CREDITMEMO_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo DROP FOREIGN KEY SALES_CREDITMEMO_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated_order DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice_grid DROP FOREIGN KEY SALES_INVOICE_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice DROP FOREIGN KEY SALES_INVOICE_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_created DROP FOREIGN KEY SALES_ORDER_AGGREGATED_CREATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_updated DROP FOREIGN KEY SALES_ORDER_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_item DROP FOREIGN KEY SALES_ORDER_ITEM_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_status_label DROP FOREIGN KEY SALES_ORDER_STATUS_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated_order DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment_grid DROP FOREIGN KEY SALES_SHIPMENT_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment DROP FOREIGN KEY SALES_SHIPMENT_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated_order DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_creditmemo_grid_archive DROP FOREIGN KEY MAGENTO_SALES_CREDITMEMO_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_invoice_grid_archive DROP FOREIGN KEY MAGENTO_SALES_INVOICE_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_CSTR_ID_CSTR_ENTT_ENTT_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_shipment_grid_archive DROP FOREIGN KEY MAGENTO_SALES_SHIPMENT_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE downloadable_link_purchased_item DROP FOREIGN KEY DL_LNK_PURCHASED_ITEM_ORDER_ITEM_ID_SALES_ORDER_ITEM_ITEM_ID;
ALTER TABLE downloadable_link_purchased DROP FOREIGN KEY DOWNLOADABLE_LINK_PURCHASED_ORDER_ID_SALES_ORDER_ENTITY_ID;
ALTER TABLE paypal_billing_agreement_order DROP FOREIGN KEY PAYPAL_BILLING_AGREEMENT_ORDER_ORDER_ID_SALES_ORDER_ENTITY_ID;
```

### Konfigurera försäljningsdatabasen

Kör föregående skript:

1. Logga in i MySQL-databasen som `root` eller administrativ användare:

   ```bash
   mysql -u root -p
   ```

1. På `mysql>` kör du skriptet enligt följande:

   ```shell
   source <path>/<script>.sql
   ```

   Exempel:

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. När skriptet har körts anger du `exit`.

### Säkerhetskopiera säljdata

I det här avsnittet beskrivs hur du säkerhetskopierar försäljningstabeller från den huvudsakliga Commerce-databasen så att du kan återställa dem i den separata försäljningsdatabasen.

Om du är vid `mysql>` prompt, enter `exit` för att återgå till kommandoskalet.

Kör följande `mysqldump` kommandon, en åt gången, från kommandoskalet. Ersätt följande i varje exempel:

- `<your database root username>` med namnet på databasens rotanvändare
- `<your database root user password>` med användarens lösenord
- `<your main Commerce DB name>` med namnet på din Commerce-databas
- `<path>` med en skrivbar filsystemsökväg

#### Skript 1

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sales_bestsellers_aggregated_daily sales_bestsellers_aggregated_monthly sales_bestsellers_aggregated_yearly sales_creditmemo sales_creditmemo_comment sales_creditmemo_grid sales_creditmemo_item sales_invoice sales_invoice_comment sales_invoice_grid sales_invoice_item sales_invoiced_aggregated sales_invoiced_aggregated_order sales_order sales_order_address sales_order_aggregated_created sales_order_aggregated_updated sales_order_grid sales_order_item sales_order_payment sales_order_status sales_order_status_history sales_order_status_label sales_order_status_state sales_order_tax sales_order_tax_item sales_payment_transaction sales_refunded_aggregated sales_refunded_aggregated_order sales_sequence_meta sales_sequence_profile sales_shipment sales_shipment_comment sales_shipment_grid sales_shipment_item sales_shipment_track sales_shipping_aggregated sales_shipping_aggregated_order > /<path>/sales.sql
```

#### Skript 2

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_sales_creditmemo_grid_archive magento_sales_invoice_grid_archive magento_sales_order_grid_archive magento_sales_shipment_grid_archive > /<path>/salesarchive.sql
```

#### Skript 3

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_order magento_customercustomattributes_sales_flat_order_address > /<path>/customercustomattributes.sql
```

#### Skript 4

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sequence_creditmemo_0 sequence_creditmemo_1 sequence_invoice_0 sequence_invoice_1 sequence_order_0 sequence_order_1 sequence_rma_item_0 sequence_rma_item_1 sequence_shipment_0 sequence_shipment_1 > /<path>/sequence.sql
```

### Återställ försäljningsdata

Det här skriptet återställer försäljningsdata i offertdatabasen.

#### NDB-krav

Om du använder en [Nätverksdatabas (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) kluster:

1. Konvertera tabeller från InnoDb till NDB-typ i dumpfiler:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Ta bort rader med en FULLTEXT-nyckel från dumpar eftersom NDB-tabeller inte har stöd för FULLTEXT.

#### Återställ data

Kör följande kommandon:

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sales.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sequence.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/salesarchive.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/customercustomattributes.sql
```

Plats

- `<your sales DB name>` med namnet på din försäljningsdatabas.

   I det här avsnittet är exempeldatabasens namn `magento_sales`.

- `<root username>` med ditt MySQL-rotanvändarnamn
- `<root user password>` med användarens lösenord
- Verifiera platsen för de säkerhetskopierade filer som du skapade tidigare (till exempel `/var/sales.sql`)

## Konfigurera offertdatabasen

I det här avsnittet behandlas uppgifter som krävs för att ta bort externa nycklar från försäljningsdatabastabeller och flytta tabeller till försäljningsdatabasen.

>[!INFO]
>
>Det här avsnittet innehåller skript med specifika databastabellnamn. Om du har utfört anpassningar eller om du vill se en fullständig lista över tabeller innan du utför åtgärder på dem läser du [Referensskript](#reference-scripts).

Tabellnamn för offertdatabaser börjar med `quote`. The `magento_customercustomattributes_sales_flat_quote` och `magento_customercustomattributes_sales_flat_quote_address` tabeller påverkas också

### Släpp sekundärnycklar från offerttabeller

Det här skriptet tar bort sekundärnycklar som refererar till icke-citattabeller från citattabeller. Ersätt `<your main Commerce DB name>` med namnet på din Commerce-databas.

Skapa följande skript och ge det ett namn som `2_foreign-key-quote.sql`:

```sql
use <your main DB name>;
ALTER TABLE quote DROP FOREIGN KEY QUOTE_STORE_ID_STORE_STORE_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_PRODUCT_ID_CATALOG_PRODUCT_ENTITY_ENTITY_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_STORE_ID_STORE_STORE_ID;
```

Kör skriptet på följande sätt:

1. Logga in i MySQL-databasen som rot- eller administrativ användare:

   ```bash
   mysql -u root -p
   ```

1. På `mysql >` kör du skriptet enligt följande:
   `source <path>/<script>.sql`

   Exempel:

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. När skriptet har körts anger du `exit`.

### Säkerhetskopiera offerttabeller

I det här avsnittet beskrivs hur du säkerhetskopierar offerttabeller från huvuddatabasen och återställer dem i offertdatabasen.

Kör följande kommando från en kommandotolk:

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### NDB-krav

Om du använder en [Nätverksdatabas (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) kluster:

1. Konvertera tabeller från InnoDb till NDB-typ i dumpfiler:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Ta bort rader med en FULLTEXT-nyckel från dumpar eftersom NDB-tabeller inte har stöd för FULLTEXT.

### Återställ tabeller till offertdatabasen

```bash
mysql -u root -p magento_quote < /<path>/quote.sql
```

## Släpp försäljnings- och offerttabeller från databasen

Det här skriptet säljer- och offerttabeller från Commerce-databasen. Ersätt `<your main DB name>` med namnet på din Commerce-databas.

Skapa följande skript och ge det ett namn som `3_drop-tables.sql`:

```sql
use <your main DB name>;
SET foreign_key_checks = 0;
DROP TABLE magento_customercustomattributes_sales_flat_quote;
DROP TABLE magento_customercustomattributes_sales_flat_quote_address;
DROP TABLE quote;
DROP TABLE quote_address;
DROP TABLE quote_address_item;
DROP TABLE quote_item;
DROP TABLE quote_item_option;
DROP TABLE quote_payment;
DROP TABLE quote_shipping_rate;
DROP TABLE quote_id_mask;
DROP TABLE sales_bestsellers_aggregated_daily;
DROP TABLE sales_bestsellers_aggregated_monthly;
DROP TABLE sales_bestsellers_aggregated_yearly;
DROP TABLE sales_creditmemo;
DROP TABLE sales_creditmemo_comment;
DROP TABLE sales_creditmemo_grid;
DROP TABLE sales_creditmemo_item;
DROP TABLE sales_invoice;
DROP TABLE sales_invoice_comment;
DROP TABLE sales_invoice_grid;
DROP TABLE sales_invoice_item;
DROP TABLE sales_invoiced_aggregated;
DROP TABLE sales_invoiced_aggregated_order;
DROP TABLE sales_order;
DROP TABLE sales_order_address;
DROP TABLE sales_order_aggregated_created;
DROP TABLE sales_order_aggregated_updated;
DROP TABLE sales_order_grid;
DROP TABLE sales_order_item;
DROP TABLE sales_order_payment;
DROP TABLE sales_order_status;
DROP TABLE sales_order_status_history;
DROP TABLE sales_order_status_label;
DROP TABLE sales_order_status_state;
DROP TABLE sales_order_tax;
DROP TABLE sales_order_tax_item;
DROP TABLE sales_payment_transaction;
DROP TABLE sales_refunded_aggregated;
DROP TABLE sales_refunded_aggregated_order;
DROP TABLE sales_sequence_meta;
DROP TABLE sales_sequence_profile;
DROP TABLE sales_shipment;
DROP TABLE sales_shipment_comment;
DROP TABLE sales_shipment_grid;
DROP TABLE sales_shipment_item;
DROP TABLE sales_shipment_track;
DROP TABLE sales_shipping_aggregated;
DROP TABLE sales_shipping_aggregated_order;
DROP TABLE magento_sales_creditmemo_grid_archive;
DROP TABLE magento_sales_invoice_grid_archive;
DROP TABLE magento_sales_order_grid_archive;
DROP TABLE magento_sales_shipment_grid_archive;
DROP TABLE magento_customercustomattributes_sales_flat_order;
DROP TABLE magento_customercustomattributes_sales_flat_order_address;
DROP TABLE sequence_creditmemo_0;
DROP TABLE sequence_creditmemo_1;
DROP TABLE sequence_invoice_0;
DROP TABLE sequence_invoice_1;
DROP TABLE sequence_order_0;
DROP TABLE sequence_order_1;
DROP TABLE sequence_rma_item_0;
DROP TABLE sequence_rma_item_1;
DROP TABLE sequence_shipment_0;
DROP TABLE sequence_shipment_1;
SET foreign_key_checks = 1;
```

Kör skriptet på följande sätt:

1. Logga in i MySQL-databasen som rot- eller administrativ användare:

   ```bash
   mysql -u root -p
   ```

1. På `mysql>` kör du skriptet enligt följande:

   ```shell
   source <path>/<script>.sql
   ```

   Exempel:

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. När skriptet har körts anger du `exit`.

## Uppdatera din distributionskonfiguration

Det sista steget i att dela databaser manuellt är att lägga till anslutnings- och resursinformation i Commerce distributionskonfiguration. `env.php`.

Så här uppdaterar du distributionskonfigurationen:

1. Logga in på din Commerce-server som eller växla till [ägare av filsystem](../../installation/prerequisites/file-system/overview.md).
1. Säkerhetskopiera din distributionskonfiguration:

   ```bash
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. Öppna `<magento_root>/app/etc/env.php` i en textredigerare och uppdatera den med hjälp av de riktlinjer som beskrivs i följande avsnitt.

### Uppdatera databasanslutningar

Leta reda på blocket som börjar med `'default'` (under `'connection'`) och lägga till `'checkout'` och `'sales'` -avsnitt. Ersätt exempelvärden med värden som passar din plats.

```php
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
      ),
      'checkout' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_quote',
'username' => 'magento_quote',
'password' => 'magento_quote',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'sales' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_sales',
'username' => 'magento_sales',
'password' => 'magento_sales',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
    ),
```

### Uppdatera resurser

Leta reda på blocket som börjar med `'resource'` och lägga till `'checkout'` och `'sales'` enligt följande:

```php
'resource' =>
  array (
    'default_setup' =>
    array (
      'connection' => 'default',
    ),
    'checkout' =>
    array (
      'connection' => 'checkout',
    ),
    'sales' =>
    array (
      'connection' => 'sales',
    ),
```

## Referensskript

I det här avsnittet finns skript som du kan köra för att skriva ut en fullständig lista över tabeller som påverkas utan att utföra några åtgärder på dem. Du kan använda dem för att se vilka tabeller som påverkas innan du delar databaser manuellt, vilket kan vara användbart om du använder tillägg som anpassar [databasschema](https://glossary.magento.com/database-schema).

Så här använder du dessa skript:

1. Skapa ett SQL-skript med innehållet i varje skript i det här avsnittet.
1. Ersätt `<your main DB name>` med namnet på din Commerce-databas.

   I det här avsnittet är exempeldatabasens namn `magento`.

1. Kör varje skript från `mysql>` prompt as `source <script name>`
1. Granska utdata.
1. Kopiera resultatet av varje skript till ett annat SQL-skript och ta bort lodstreck (`|`).
1. Kör varje skript från `mysql>` prompt as `source <script name>`.

   När du kör det här andra skriptet utförs åtgärderna i din huvudCommerce-databas.

### Ta bort sekundärnycklar (försäljningstabeller)

Det här skriptet tar bort sekundärnycklar som refererar till icke-försäljningsregister från försäljningsdatabasen.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|sales_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales_%' escape '|'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|magento_sales|_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales|_%' escape '|'
;
```

### Ta bort sekundärnycklar (offerttabeller)

Det här skriptet tar bort sekundärnycklar som refererar till icke-citattabeller från citattabeller.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_customercustomattributes\_%'
;
```

### Släpp försäljningsregister

Det här skriptet släpper säljtabeller från Commerce-databasen.

```sql
use <your main DB name>;
select ' SET foreign_key_checks = 0;' as querytext
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_customercustomattributes_sales_flat_order%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sequence/_%' escape '/'
union all
select 'SET foreign_key_checks = 1;';
```

### Släpp offerttabeller

Släpp alla tabeller som börjar med `quote_`.
