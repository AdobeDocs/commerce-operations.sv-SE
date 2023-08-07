---
title: Bästa sättet att konfigurera MySQL-slavanslutningen
description: Lär dig hur du konfigurerar MySQL-slavanslutningen för Adobe Commerce-webbplatser som distribueras i molninfrastrukturen.
role: Developer
feature: Best Practices
exl-id: d65bc80a-c4ec-4ea4-aff1-110592838201
source-git-commit: 3532480e2172c39ceb4ec55c9819d5271fd1fcdb
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Bästa sättet att konfigurera MySQL-slavanslutningen

>[!NOTE]
>
>Den här artikeln innehåller programtermer som är branschstandard och som vissa kan finna rasistiska, sexistiska eller förtryckande och som kan få läsaren att känna sig sårad, traumatiserad eller ovälkommen. Adobe arbetar med att ta bort dessa villkor från kod, dokumentation och användarupplevelser.

Adobe Commerce kan läsa flera databaser asynkront. Om du förväntar dig en hög belastning för MySQL-databasen för en Commerce-plats som distribuerats på en molninfrastruktur, rekommenderar Adobe att du aktiverar MYSQL-slavanslutningen.

När du aktiverar MYSQL-slavanslutningen använder Adobe Commerce en skrivskyddad anslutning till databasen för att ta emot skrivskyddad trafik på en icke-överordnad nod. Prestandan förbättras genom lastbalansering när bara en nod hanterar läs- och skrivtrafik.

## Berörda versioner

Adobe Commerce på molninfrastruktur, endast Pro-arkitektur

## Konfigurera MySQL-slavanslutning

I Adobe Commerce om molninfrastruktur kan du åsidosätta standardkonfigurationen för MYSQL-slavanslutningen genom att ange [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) variabel. Ange variabeln till `true` för att automatiskt använda en skrivskyddad anslutning till databasen.

**Aktivera MySQL-slavanslutningen**:

1. Byt till din projektkatalog på din lokala arbetsstation.

1. I `.magento.env.yaml` -fil, ange `MYSQL_USE_SLAVE_CONNECTION` till true.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Verkställ `.magento.env.yaml` och skickas till fjärrmiljön.

   När distributionen har slutförts aktiveras MySQL-slavanslutningen för molnmiljön.

## Ytterligare information

Läs mer om hur du anpassar molnmiljön genom att åsidosätta din befintliga Commerce-konfiguration med [Miljövariabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) i _Adobe Commerce i molninfrastrukturguide_.

Se [MySQL-flaskhalsar med hög belastning i Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html) artikel i _Support Knowledge Base_.
