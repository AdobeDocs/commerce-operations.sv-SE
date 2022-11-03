---
title: Adobe Commerce 2.3.5 - uppgraderingskrav för MariaDB
description: Lär dig hur du förbereder din Adobe Commerce-databas för uppgradering från Adobe Commerce 2.3.5.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# Krav för Adobe Commerce 2.3.5-uppgradering

I den här artikeln beskrivs hur du förbereder databasen när du uppgraderar till Adobe Commerce 2.3.5 från version 2.3.4 eller tidigare.

Uppgraderingen kräver att supportteamet uppgraderar MariaDB i molninfrastrukturen från MariaDB 10.0 till 10.2 för att uppfylla kraven för Adobe Commerce. Adobe Commerce version 2.3.5 och senare.

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur med Adobe Commerce version 2.3.4 eller tidigare och MariaDB version 10.0 eller tidigare.

## Förbered databasen för uppgraderingen

Innan Adobe Commerce supportteam börjar uppgraderingsprocessen måste du förbereda databasen genom att konvertera formatet för alla tabeller från `COMPACT` till `DYNAMIC`. Du måste också konvertera lagringsmotortypen från `MyISAM` till `InnoDB`.

Tänk på följande när du skapar en plan och ett schema för att konvertera databasen.

- Konverterar från `COMPACT` till `DYNAMIC` tabeller kan ta flera timmar med en stor databas.

- För att förhindra att data skadas ska du inte göra konverteringen när webbplatsen publiceras.

- Slutför konverteringsarbetet under en begränsad trafikperiod på webbplatsen.

- Byt till [underhållsläge](../../../installation/tutorials/maintenance-mode.md) innan du kör `ALTER` kommandon.

### Konvertera databastabeller

Du kan konvertera tabeller på en nod i klustret. Ändringarna replikeras till de andra kärnnoderna i klustret.

1. Använd SSH för att ansluta till nod 1 från din Adobe Commerce i molninfrastrukturmiljö.

1. Logga in på MariaDB.

1. Konvertera tabellformatet.

   - Identifiera tabeller som ska konverteras från kompakt till dynamiskt format.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
      ```

   - Bestäm tabellstorlekarna så att du kan schemalägga konverteringsarbetet.

      ```mysql
      SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
      ```

      Det tar längre tid att konvertera större tabeller. Du bör planera i enlighet med detta när du övertar platsen i och utanför underhållsläge, vilka grupper av tabeller som ska konverteras i vilken ordning, så att du kan planera tidsangivelserna för de underhållsfönster som behövs

   - Konvertera alla tabeller till ett dynamiskt format i taget.

      ```mysql
      ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
      ```

1. Uppdatera tabelllagringsmotorn.

   - Identifiera tabeller som använder `MyISAM` lagring.

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Konvertera tabeller som använder `MyISAM` lagring till `InnoDB` lagring.

      ```mysql
      ALTER TABLE [ table name here ] ENGINE=InnoDB;
      ```

1. Verifiera konverteringen.

   Det här steget är obligatoriskt eftersom koddistributioner som görs efter att du har slutfört konverteringen kan göra att vissa tabeller återställs till den ursprungliga konfigurationen.

   - Dagen före den schemalagda uppgraderingen till MariaDB version 10.2 loggar du in i databasen och kör frågorna för att kontrollera format och lagringsmotor.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
      ```

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Om några tabeller har återställts upprepar du stegen för att ändra tabellformatet och lagringsmotorn.

## Ytterligare information

[Bästa databaspraxis för Adobe Commerce om molninfrastruktur](../planning/database-on-cloud.md)
