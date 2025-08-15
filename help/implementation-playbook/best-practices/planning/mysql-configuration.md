---
title: Bästa praxis för MySQL-konfiguration
description: Lär dig hur MySQL-utlösare och slavanslutningar påverkar Commerce webbplatsprestanda och hur du använder dem effektivt.
role: Developer
feature: Best Practices
exl-id: 7c2f51fd-9333-4954-bd35-79c2de3cb2ff
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Bästa praxis för MySQL-konfiguration

>[!NOTE]
>
>Det här avsnittet innehåller programtermer som är branschstandard och som vissa kan finna rasistiska, sexistiska eller förtryckande och som kan få läsaren att känna sig sårad, traumatiserad eller ovälkommen. Adobe arbetar med att ta bort dessa villkor från kod, dokumentation och användarupplevelser.

## Utlösare

I den här artikeln beskrivs hur du undviker prestandaproblem när du använder MySQL-utlösare. Utlösare används för att logga ändringar i granskningstabeller.

### Berörda produkter och versioner

- Adobe Commerce lokalt
- Adobe Commerce i molninfrastruktur

>[!WARNING]
>
>För Adobe Commerce i molnprojekt ska du alltid testa konfigurationsändringarna i mellanlagringsmiljön innan du ändrar konfigurationen för produktionsmiljön.

### Prestandaeffekter

Utlösare tolkas som kod vilket innebär att MySQL inte förkompilerar dem.

Utlösarna är kopplade till frågans transaktionsutrymme och lägger till overhead till en tolk och tolk för varje fråga som utförs med tabellen. Utlösarna delar samma transaktionsutrymme som de ursprungliga frågorna, och även om dessa frågor konkurrerar om lås i tabellen konkurrerar utlösarna oberoende av varandra för lås i ett annat register.

Denna extra kostnad kan påverka webbplatsens prestanda negativt om många utlösare används.

>[!WARNING]
>
>Adobe Commerce stöder inte några anpassade utlösare i Adobe Commerce-databasen eftersom anpassade utlösare kan orsaka inkompatibilitet med framtida Adobe Commerce-versioner. Mer information finns i [Allmänna MySQL-riktlinjer](../../../installation/prerequisites/database/mysql.md) i Adobe Commerce-dokumentationen.

### Effektiv användning

Följ de här riktlinjerna för att förhindra prestandaproblem när du använder utlösare:

- Om du har anpassade utlösare som skriver data när utlösaren körs, flyttar du den här logiken så att den skriver direkt till granskningstabellerna i stället. Genom att till exempel lägga till ytterligare en fråga i programkoden efter frågan som du vill skapa utlösaren för.
- Granska befintliga anpassade utlösare och överväg att ta bort dem och skriva direkt till tabellerna från programsidan. Kontrollera om det finns utlösare i databasen med hjälp av [`SHOW TRIGGERS` SQL-sats ](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- [Skicka en Adobe Commerce-supportanmälan](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket) om du vill ha mer hjälp, frågor eller funderingar.

## Slavanslutningar

Adobe Commerce kan läsa flera databaser asynkront. Om du förväntar dig en hög belastning för MySQL-databasen för en Commerce-plats som distribuerats på en molninfrastruktur, rekommenderar Adobe att du aktiverar MYSQL-slavanslutningen.

När du aktiverar MYSQL-slavanslutningen använder Adobe Commerce en skrivskyddad anslutning till databasen för att ta emot skrivskyddad trafik på en icke-huvudnod. Prestandan förbättras genom lastbalansering när bara en nod hanterar läs- och skrivtrafik.

### Berörda versioner

Adobe Commerce på molninfrastruktur, endast Pro-arkitektur

### Konfiguration

I Adobe Commerce i molninfrastrukturen kan du åsidosätta standardkonfigurationen för MYSQL-slavanslutningen genom att ange variabeln [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) . Ange den här variabeln till `true` om du automatiskt vill använda en skrivskyddad anslutning till databasen.

**Så här aktiverar du MySQL-slavanslutningen**:

1. Byt till din projektkatalog på din lokala arbetsstation.

1. Ange `.magento.env.yaml` som true i filen `MYSQL_USE_SLAVE_CONNECTION`.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Genomför ändringarna av filen `.magento.env.yaml` och skicka den till fjärrmiljön.

   När distributionen har slutförts aktiveras MySQL-slavanslutningen för molnmiljön.
