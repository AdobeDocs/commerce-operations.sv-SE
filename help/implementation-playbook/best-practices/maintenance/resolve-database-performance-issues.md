---
title: Bästa tillvägagångssätt för att lösa databasprestandaproblem
description: Lär dig hur du åtgärdar databasproblem som försämrar prestandan på Adobe Commerce webbplatser som distribueras i molninfrastrukturen.
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# Bästa tillvägagångssätt för att lösa databasprestandaproblem

I den här artikeln beskrivs hur du åtgärdar databasproblem som negativt påverkar databasprestanda på Adobe Commerce-webbplatser i molnet.

## Berörda versioner

Adobe Commerce i molninfrastruktur

## Identifiera och lösa frågor som körs länge

Avgör om MySQL-frågor körs långsamt. Beroende på din Adobe Commerce-plan för molninfrastruktur och därmed på tillgängligheten för verktyg kan du göra följande.

### Analysera databasfrågor med MySQL

Du kan använda MySQL för att identifiera och lösa frågor som körs länge i Adobe Commerce i molninfrastrukturprojekt.

1. Kör [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) -programsats.
1. Om du ser frågor som körs länge ska du köra [MySQL `EXPLAIN` och `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) för var och en av dem, för att ta reda på vad som får frågan att köras länge.
1. Beroende på vilka problem som hittas kan du åtgärda frågan så att den körs snabbare.

### Analysera frågor med Percona Toolkit (endast för Pro-arkitekturen)

Om ditt Adobe Commerce-projekt används i Pro-arkitekturen kan du använda Percona Toolkit för att analysera frågor.

1. Kör `pt-query-digest --type=slowlog` kommandot mot långsamma MySQL-frågeloggar.
   * Information om var de långsamma frågeloggarna finns i **[!UICONTROL Log locations > Service Logs]**(https://devdocs.magento.com/cloud/project/log-locations.html#service-logs) i vår utvecklardokumentation.
   * Se [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) dokumentation.
1. Beroende på vilka problem som hittas kan du åtgärda frågan så att den körs snabbare.

## Verifiera att alla tabeller har en primärnyckel

Att definiera primärnycklar är ett krav för bra databas- och tabelldesign. Med primärnycklar kan du unikt identifiera en rad i en tabell.

Om du har tabeller utan en primärnyckel använder standarddatabasmotorn för Adobe Commerce (InnoDB) den första unika nyckeln som inte är null som primärnyckel. Om ingen unik nyckel är tillgänglig skapar InnoDB en dold primärnyckel (6 byte). Problemet med en indirekt definierad primärnyckel är att du inte har kontroll över den. Dessutom tilldelas det implicita värdet globalt för alla tabeller utan primärnycklar. Den här konfigurationen kan orsaka problem om du utför samtidiga skrivningar av de här tabellerna. Detta kan leda till prestandaproblem eftersom tabellerna också delar den globala indexökningen för dold primärnyckel.

Förebygg dessa problem genom att definiera en primärnyckel för alla tabeller som inte har någon.

### Identifiera och uppdatera tabeller utan en primärnyckel

1. Identifiera tabeller utan en primärnyckel med följande SQL-fråga:

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. För tabeller som saknar en primärnyckel lägger du till en primärnyckel genom att uppdatera `db_schema.xml` (det deklarativa schemat) med en nod som liknar följande:

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   Ersätt `referenceID` och `column name` variabler med anpassade värden.

Mer information finns i [Konfigurera deklarativt schema](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) i vår dokumentation för utvecklare.

## Identifiera och ta bort dubblettindex

Identifiera eventuella dubblettindex i databasen och ta bort dem.

### Kontrollera om det finns dubblettindex

Om du vill söka efter dubblettindex för Pro- eller Starter-molnarkitekturen kör du följande SQL-fråga.

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

Frågan returnerar kolumnnamnen och namnen på eventuella dubblettindex.

Handläggare som arbetar med Pro-arkitektur kan också köra kontrollen med Percona Toolkit  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` -kommando.

### Ta bort dubblettindex

Använd SQL [DROP INDEX-sats](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) om du vill ta bort dubblettindex.

```SQL
DROP INDEX
```

## Ytterligare information

[Bästa praxis för databaskonfiguration för molndistributioner](../planning/database-on-cloud.md)
