---
title: Bästa sättet att konfigurera MySQL-slavanslutningen
description: Lär dig hur du konfigurerar MySQL-slavanslutningen för Adobe Commerce-webbplatser som distribueras i molninfrastrukturen.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 0866272e02a7a223d35e14842bfb42a827e0468d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---


# Bästa sättet att konfigurera MySQL-slavanslutningen

>!![NOTE]
Vi är medvetna om att den här artikeln fortfarande innehåller programtermer som är branschstandard och som vissa kan finna som rasistiska, sexistiska eller förtryckande och som kan få läsaren att känna sig sårad, traumatiserad eller ovälkommen. Adobe arbetar med att ta bort dessa villkor från vår kod, dokumentation och användarupplevelse.

För Adobe Commerce-webbplatser som distribueras på en molninfrastruktur rekommenderar Adobe att du aktiverar MYSQL-slavanslutningen för databasen som standard.

Adobe Commerce kan läsa flera databaser asynkront.  När du aktiverar MYSQL-slavanslutningen använder Adobe Commerce en skrivskyddad anslutning till databasen för att ta emot skrivskyddad trafik på en icke-överordnad nod. Detta förbättrar prestanda genom lastbalansering eftersom bara en nod behöver hantera trafik med läs- och skrivbehörighet.

## Berörda versioner

Adobe Commerce om molninfrastruktur, Pro-arkitektur

## Konfigurera MySQL-slavanslutning

Konfigurationen för MYSQL-slavanslutningen anges av [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) distribuera variabeln i Adobe Commerce i konfigurationsfilen för molninfrastrukturen, `.magento.env.yaml`. Ange variabeln till `true` för att aktivera anslutningen.

Så här aktiverar du MySQL-slavanslutningen:

1. Redigera `.magento.env.yaml` och verifiera att `MYSQL_USE_SLAVE_CONNECTION` är aktiverat.

   ```
   stage:
      deploy:
      MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Genomför ändringarna och skicka dem sedan till miljögrenen för att distribuera uppdateringen.

   När distributionen har slutförts aktiveras MySQL-slavanslutningen i din molninfrastruktur.

## Ytterligare information

- [Miljövariabler](https://devdocs.magento.com/cloud/env/variables-intro.html)
- [MySQL-flaskhalsar med hög belastning i Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Bästa databaspraxis för Adobe Commerce om molninfrastruktur](database-on-cloud.md)
