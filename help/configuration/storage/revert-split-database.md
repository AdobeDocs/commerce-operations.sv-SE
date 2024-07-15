---
title: Återställ delad databas
description: Återgå från en borttagen implementering av delade databaser till en enda databasimplementering.
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Återgå från delad databas

{{ee-only}}

För Adobe Commerce-kunder som har implementerat [Delad databas](multi-master.md) beskrivs i följande avsnitt hur du återställer eller migrerar tillbaka till en enskild databas. Vi rekommenderar att Adobe Commerce handlare som för närvarande använder Delad databas och planerar att uppgradera till 2.4.2 och senare granska dessa steg, samt vår [kungörelse](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) om den planerade borttagningen av Delad databas.

När du återgår från en delad databas till en enskild databas skapar du säkerhetskopior av `magento_quote`- och `magento_sales`-databaserna innan de läses in i den enskilda `magento_main`-databasen.

I det här exemplet loggar vi in på alla tre databaser som är installerade på samma värd (`magento2-mysql`) som &quot;root&quot;-användaren. Du måste ersätta dessa värden med rätt värden för databaserna.

1. Skapa en säkerhetskopia av databasen `magento_quote`:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Skapa en säkerhetskopia av databasen `magento_sales`:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Läs in databasen `magento_quote` i databasen `magento_main`:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Läs in databasen `magento_sales` i databasen `magento_main`:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Släpp databasen `magento_sales`:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Släpp databasen `magento_quote`:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Ta bort distributionskonfigurationen för `checkout` och `sales` i avsnitten `connections` och `resources` i filen `env.php`.
1. Återställ sekundärnycklar:

   ```bash
   bin/magento setup:upgrade
   ```

## Verifiera ditt arbete

För att verifiera att implementeringen av en databas fungerar som den ska, utför du följande åtgärder och kontrollerar att data har lagts till i databastabellerna i `magento_main` med ett databasverktyg som [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. Kontrollera att externa nycklar har återställts. Nyckeln `QUOTE_STORE_ID_STORE_STORE_ID` i databastabellen `quote`.
1. Verifiera att kunderna kan lägga order från butiken.
1. Kontrollera att order som skapats innan den delade databasen återställs till en enda databas är tillgängliga i Admin.
