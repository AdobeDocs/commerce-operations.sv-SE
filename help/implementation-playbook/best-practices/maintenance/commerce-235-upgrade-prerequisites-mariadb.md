---
title: Adobe Commerce uppgraderingskrav för MariaDB
description: Lär dig hur du förbereder din Adobe Commerce-databas för att uppgradera MariaDB från en tidigare version.
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: 73663659dd1b3305bf8c9a167852b24dc1016e7d
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Krav för uppgradering av MariaDB

Uppgradera MariaDB-tjänsten i molninfrastrukturen från version 10.0 eller 10.2 till version 10.3, 10.4 eller 10.5. MariaDB version 10.3 och senare kräver att databasen använder det dynamiska tabellradformatet och Adobe Commerce kräver att du använder InnoDB-lagringsmotorn för tabeller. I den här artikeln beskrivs hur du uppdaterar din databas så att den uppfyller dessa MariaDB-krav.

När du har förberett databasen skickar du en Adobe Commerce supportanmälan för att uppdatera MariaDB-tjänstversionen i din molninfrastruktur innan du fortsätter med uppgraderingsprocessen för Adobe Commerce.

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur med MariaDB version 10.3 eller tidigare.

## Förbered databasen för uppgraderingen

Innan Adobe Commerce supportteam börjar uppgraderingsprocessen förbereder du databasen genom att konvertera databastabellerna:

- Konvertera radformatet från `COMPACT` till `DYNAMIC`
- Ändra lagringsmotorn från `MyISAM` till `InnoDB`

Tänk på följande när du planerar och schemalägger konverteringen:

- Konverterar från `COMPACT` till `DYNAMIC` tabeller kan ta flera timmar med en stor databas.

- För att förhindra att data skadas ska du inte slutföra konverteringsarbetet på en aktiv webbplats.

- Slutför konverteringsarbetet under en begränsad trafikperiod på webbplatsen.

- Byt till [underhållsläge](../../../installation/tutorials/maintenance-mode.md) innan du kör kommandona för att konvertera databastabeller.

### Konvertera radformat för databastabell

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

### Konvertera lagringsformat för databastabell

Du kan konvertera tabeller på en nod i klustret. Ändringarna replikeras automatiskt till de andra tjänstnoderna.

Processen att konvertera lagringsformatet skiljer sig åt för Adobe Commerce Starter- och Adobe Commerce Pro-projekt.

- För Starter-arkitekturen använder du MySQL `ALTER` för att konvertera formatet.
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

### Verifiera databaskonverteringen

Dagen före den schemalagda uppgraderingen till MariaDB version 10.3, 10.4 eller 10.6 kontrollerar du att alla tabeller har rätt radformat och lagringsmotor. Verifiering krävs eftersom koddistributioner som görs efter att du har slutfört konverteringen kan göra att vissa tabeller återställs till den ursprungliga konfigurationen.

1. Logga in i databasen.

1. Kontrollera om det finns tabeller som fortfarande har `COMPACT` radformat.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Kontrollera om det finns tabeller som fortfarande använder `MyISAM` lagringsformat

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Om några tabeller har återställts upprepar du stegen för att ändra tabellradformatet och lagringsmotorn.

## Ändra lagringsmotorn

Se [Konvertera MyISAM-tabeller till InnoDB](../planning/database-on-cloud.md).

## Ytterligare information

- [Bästa databaspraxis för Adobe Commerce om molninfrastruktur](../planning/database-on-cloud.md)
- [Uppdaterar MariaDB från 10.0 till 12.0 för Adobe Commerce i molnet](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10.0-to-10.2-for-magento-commerce-cloud.html)
