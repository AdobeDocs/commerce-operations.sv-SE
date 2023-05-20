---
title: Bästa praxis för databaskonfiguration för molndistributioner
description: Lär dig hur du konfigurerar databas- och programinställningar för att förbättra prestandan när du distribuerar Adobe Commerce i molninfrastrukturen.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 0%

---

# Bästa tillvägagångssätt för databaskonfiguration

Lär dig mer om de bästa sätten att förbättra databasprestanda och arbeta effektivt med databasen när du distribuerar Adobe Commerce i molninfrastruktur.

## Berörda produkter

Adobe Commerce i molninfrastruktur

## Konvertera alla MyISAM-tabeller till InnoDB

Adobe rekommenderar att du använder InnoDB-databasmotorn. I en standardinstallation av Adobe Commerce lagras alla tabeller i databasen med InnoDB-motorn. Vissa tredjepartsmoduler (tillägg) kan emellertid presentera tabeller i MyISAM-format. När du har installerat en modul från tredje part bör du kontrollera databasen för att identifiera tabeller i `myisam` formatera och konvertera dem till `innodb` format.

### Kontrollera om en modul innehåller MyISAM-tabeller

Du kan analysera tredjepartsmodulkoden innan du installerar den för att avgöra om den använder MyISAM-tabeller.

Om du redan har installerat ett tillägg kör du följande fråga för att avgöra om databasen har några MyISAM-tabeller:

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### Ändra lagringsmotorn till InnoDB

I `db_schema.xml` som deklarerar tabellen, ange `engine` attributvärde för motsvarande `table` nod till `innodb`. Mer information finns i [Konfigurera deklarativt schema > tabellnod](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) i vår dokumentation för utvecklare.

Det deklarativa systemet infördes i Adobe Commerce för molninfrastruktur version 2.3.

## Konfigurera den rekommenderade sökmotorn för intern MySQL-sökning

Adobe rekommenderar att du alltid ställer in Elasticsearch eller OpenSearch för ditt Adobe Commerce i molninfrastrukturprojekt, även om du tänker konfigurera ett tredjepartssökverktyg för ditt Adobe Commerce-program. Den här konfigurationen innehåller ett reservalternativ om tredjepartssökverktyget misslyckas.

Vilken sökmotor du använder beror på vilken version av Adobe Commerce som är installerad i molnet:

- För Adobe Commerce 2.4.4 och senare använder du OpenSearch-tjänsten för intern MySQL-sökning.

- För tidigare Adobe Commerce-versioner använder du Elasticsearch.

Kör följande kommando för att avgöra vilken sökmotor som används för närvarande:

```bash
./bin/magento config:show catalog/search/engine
```

Konfigurationsanvisningar finns i Utvecklarhandbok för Adobe Commerce i molnet:

- [Konfigurera OpenSearch-tjänsten](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [Konfigurera tjänsten Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html)

## Undvik anpassade utlösare

Undvik om möjligt att använda anpassade utlösare.

Utlösare används för att logga ändringar i granskningstabeller. Adobe rekommenderar att programmet konfigureras så att det skriver direkt till granskningstabellerna i stället för att utlösarfunktionen används av följande skäl:

- Utlösare tolkas som kod och MySQL förkompilerar dem inte. Som en del av frågans transaktionsutrymme lägger de till overheadset i en tolk och tolk för varje fråga som utförs med tabellen.
- Utlösarna delar samma transaktionsutrymme som de ursprungliga frågorna, och även om dessa frågor konkurrerar om lås i tabellen konkurrerar utlösarna oberoende av lås i ett annat register.

Mer information om alternativ till att använda anpassade utlösare finns i [Använd MySQL-utlösare effektivt](mysql-triggers-usage.md) i vår kunskapsbas.

## Uppgradera [!DNL ECE-Tools] till version 2002.0.21 eller senare {#ece-tools-version}

Uppgradera ECE-Tools till version 2002.0.21 eller senare för att undvika eventuella problem med kroniska lås. Instruktioner finns i [Uppdatera `ece-tools` version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) i vår dokumentation för utvecklare.

## Växla indexeringsläge på ett säkert sätt

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

Om du byter indexerare genereras [!DNL data definition language] (DDL)-satser för att skapa utlösare som kan orsaka databaslås. Du kan förhindra det här problemet genom att försätta webbplatsen i underhållsläge och inaktivera cron-jobb innan du ändrar konfigurationen.
Instruktioner finns i [Konfigurera indexerare](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) i *Adobe Commerce Configuration Guide*.

## Kör inte DDL-satser i produktionen

Undvik att köra DDL-satser i produktionsmiljön för att förhindra konflikter (som tabelländringar och skapande). The `setup:upgrade` -processen är ett undantag.

Om du behöver köra en DDL-sats placerar du webbplatsen i underhållsläge och inaktiverar cron (se instruktionerna för att växla index på ett säkert sätt i föregående avsnitt).

## Aktivera arkivering av order

Aktivera arkivering av order från administratören för att minska utrymmet som krävs för försäljningstabeller när orderdata växer. Arkivering sparar diskutrymme för MySQL och förbättrar utcheckningsprestanda.

Se [Aktivera arkivering](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) i Adobe Commerce Merchant-dokumentationen.

## Ytterligare information

- [MySQL-lagringsmotorer](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Adobe Commerce 2.3.5 - uppgraderingskrav för MariaDB](../maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [Bästa tillvägagångssätt för att lösa databasprestandaproblem](../maintenance/resolve-database-performance-issues.md)
