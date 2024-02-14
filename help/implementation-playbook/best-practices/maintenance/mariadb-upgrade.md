---
title: Adobe Commerce uppgraderingskrav för MariaDB
description: Lär dig hur du förbereder din Adobe Commerce-databas för att uppgradera MariaDB från en tidigare version.
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# Krav för uppgradering av MariaDB

Innan du uppgraderar Adobe Commerce på molninfrastruktur kan du behöva uppgradera databasprogramvaran om du använder MariaDB. Exempel:

- Adobe Commerce 2.4.6 med MariaDB version 10.5.1 eller senare
- Adobe Commerce 2.3.5 med MariaDB version 10.3 eller tidigare

## Adobe Commerce 2.4.6

Från och med MariaDB 10.5.1 markeras kolumner med gamla temporala format med en `/* mariadb-5.3 */` -kommentar i utdata från `SHOW CREATE TABLE`, `SHOW COLUMNS`, `DESCRIBE` -programsatser, liksom i `COLUMN_TYPE` kolumn i `INFORMATION_SCHEMA.COLUMNS` tabell. [Se MariaDB-dokumentation](https://mariadb.com/kb/en/datetime/#internal-format).

Adobe Commerce kan inte mappa datumkolumnerna till en korrekt datatyp på grund av MariaDB-kommentaren, som kan orsaka oväntat beteende i anpassad kod.

För att undvika oväntade beteenden när du uppgraderar MariaDB från äldre versioner till version 10.6 rekommenderar Adobe att du migrerar kolumnerna till det nya interna formatet.

### Standardkonfiguration

I MariaDB 10.1.2 introducerades ett nytt tidsformat från MySQL 5.6. The `mysql56_temporal_format` systemvariabeln gör att databasen automatiskt kan konvertera det gamla datumformatet till det nya när en ändringstabell körs eller databasen importeras. Standardkonfigurationen för `mysql56_temporal_format` är alltid aktiverat på Adobe Commerce i molninfrastruktur.

### Migrera datumkolumner

Följande fråga visar tabellen och kolumnerna som påverkas och som måste migreras efter uppgradering av MariaDB till 10.5.1 eller senare:

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

Om du migrerar kolumnerna till det nya interna datumformatet måste du importera databasen på nytt eller utföra ändringar på den identifierade kolumnen med samma kolumndefinition. Följande fråga genererar nödvändiga ändringsfrågor:

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>Det är viktigt att migrera kolumnerna till det nya interna datumformatet _före_ distribuera den nya koden för att undvika oväntade beteenden.

## Adobe Commerce 2.3.5

Uppgradera MariaDB-tjänsten i molninfrastrukturen från version 10.0 eller 10.2 till version 10.3, 10.4 eller 10.5. MariaDB version 10.3 och senare kräver att databasen använder det dynamiska tabellradformatet och Adobe Commerce kräver att du använder InnoDB-lagringsmotorn för tabeller. I den här artikeln beskrivs hur du uppdaterar din databas så att den uppfyller dessa MariaDB-krav.

När du har förberett databasen skickar du en Adobe Commerce supportanmälan för att uppdatera MariaDB-tjänstversionen i din molninfrastruktur innan du fortsätter med uppgraderingsprocessen för Adobe Commerce.

### Förbered databasen för uppgraderingen

Innan Adobe Commerce supportteam börjar uppgraderingsprocessen förbereder du databasen genom att konvertera databastabellerna:

- Konvertera radformatet från `COMPACT` till `DYNAMIC`
- Ändra lagringsmotorn från `MyISAM` till `InnoDB`

Tänk på följande när du planerar och schemalägger konverteringen:

- Konverterar från `COMPACT` till `DYNAMIC` tabeller kan ta flera timmar med en stor databas.

- För att förhindra att data skadas ska du inte slutföra konverteringsarbetet på en publicerad webbplats.

- Slutför konverteringsarbetet under en begränsad trafikperiod på webbplatsen.

- Byt till [underhållsläge](../../../installation/tutorials/maintenance-mode.md) innan du kör kommandona för att konvertera databastabeller.

#### Konvertera radformat för databastabell

Du kan konvertera tabeller på en nod i klustret. Ändringarna replikeras automatiskt till de andra tjänstnoderna.

1. Använd SSH för att ansluta till nod 1 från din Adobe Commerce i molninfrastrukturmiljö.

1. Logga in på MariaDB.

1. Identifiera tabeller som ska konverteras från kompakt till dynamiskt format.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Bestäm tabellstorlekarna så att du kan schemalägga konverteringsarbetet.

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   Det tar längre tid att konvertera större tabeller. Granska tabellerna och batchbearbeta konverteringsarbetet efter prioritet och tabellstorlek för att hjälpa till att planera nödvändiga underhållsperioder.

1. Konvertera alla tabeller till ett dynamiskt format i taget.

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### Konvertera lagringsformat för databastabell

Du kan konvertera tabeller på en nod i klustret. Ändringarna replikeras automatiskt till de andra tjänstnoderna.

Processen att konvertera lagringsformatet skiljer sig åt för Adobe Commerce Starter- och Adobe Commerce Pro-projekt.

- Använd MySQL för startarkitekturen `ALTER` för att konvertera formatet.
- På Pro-arkitekturen använder du MySQL `CREATE` och `SELECT` kommandon för att skapa en databastabell med `InnoDB` lagra och kopiera data från den befintliga tabellen till den nya tabellen. Den här metoden ser till att ändringarna replikeras till alla noder i klustret.

**Konvertera tabelllagringsformat för Adobe Commerce Pro-projekt**

1. Identifiera tabeller som använder `MyISAM` lagring.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Konvertera alla tabeller till `InnoDB` lagringsformat en åt gången.

   - Byt namn på den befintliga tabellen för att förhindra namnkonflikter.

     ```mysql
     RENAME TABLE <existing_table> <table_old>;
     ```

   - Skapa en tabell som använder `InnoDB` lagring med data från den befintliga tabellen.

     ```mysql
     CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
     ```

   - Kontrollera att den nya tabellen har alla nödvändiga data.

   - Ta bort den ursprungliga tabell som du har ändrat namn på.


**Konvertera tabelllagringsformat för Adobe Commerce Starter-projekt**

1. Identifiera tabeller som använder `MyISAM` lagring.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Konvertera tabeller som använder `MyISAM` lagring till `InnoDB` lagring.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### Verifiera databaskonverteringen

Dagen före den schemalagda uppgraderingen till MariaDB version 10.3, 10.4 eller 10.6 kontrollerar du att alla tabeller har rätt radformat och lagringsmotor. Verifiering krävs eftersom koddistributioner som görs efter att du har slutfört konverteringen kan göra att vissa tabeller återställs till den ursprungliga konfigurationen.

1. Logga in i databasen.

1. Kontrollera om det finns tabeller som fortfarande har `COMPACT` radformat.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Sök efter tabeller som fortfarande använder `MyISAM` lagringsformat

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Om några tabeller har återställts upprepar du stegen för att ändra tabellradformatet och lagringsmotorn.

### Ändra lagringsmotorn

Se [Konvertera MyISAM-tabeller till InnoDB](../planning/database-on-cloud.md).
