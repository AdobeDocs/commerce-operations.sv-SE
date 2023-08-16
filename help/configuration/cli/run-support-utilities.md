---
title: Kör supportverktygen
description: Felsök ditt Commerce-projekt med det inbyggda supportverktyget.
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Kör supportverktygen

{{ee-only}}

{{file-system-owner}}

Adobe Commerce Support-verktygen - även kallade [Datainsamling](https://docs.magento.com/user-guide/system/support-data-collector.html)—gör det möjligt för användare att samla in felsökningsinformation om ditt system som kan användas av vårt supportteam.

Adobe Commerce använder dessa säkerhetskopior, som också kallas _dumpar_, för att analysera problem som kräver åtkomst till din kod. Ett typiskt scenario följer:

1. Du har problem med din Commerce Store och du kontaktar Adobe Commerce Support.
1. Supporten avgör om de behöver se koden eller databasen för att återskapa problemet.
1. Du säkerhetskopierar koden till en `.tar.gz` -fil.

   Den här säkerhetskopian _exkluderar dina mediefiler för att snabba upp processen och resultera i en mycket mindre fil.

1. Du säkerhetskopierar databasen till en `.tar.gz` -fil.

   Som standard kraschar känsliga data när säkerhetskopieringen görs.

1. Du överför dina säkerhetskopior till en fildelningstjänst.
1. Support analyserar era problem utan att påverka utvecklingen eller produktionsmiljön.

Verktygen kan ta flera minuter att slutföra.

## Skapa en säkerhetskopia av koden

Det här kommandot säkerhetskopierar kod och komprimerar den i `tar.gz` format.

{{tip-backup-command}}

Kommandoalternativ:

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

Var:

- **`--name`** anger dumpfilens namn (valfritt). Om du utelämnar den här parametern är dumpfilen tids- och datumstämplad.
- **`-o|--output=<path>`** är den absoluta filsystemsökvägen för lagring av säkerhetskopian (krävs).
- **`-l|--logs`** innehåller loggfiler (valfritt).

Om du till exempel vill skapa en säkerhetskopia med namnet `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

När kommandot har slutförts kan du säkerhetskopiera koden till Adobe Commerce Support.

## Skapa en säkerhetskopia av en databas

Det här kommandot säkerhetskopierar Commerce-databasen och komprimerar den i `tar.gz` format.

{{tip-backup-command}}

Kommandoalternativ:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Var:

- **`--name`** anger dumpfilens namn (valfritt). Om du utelämnar den här parametern är dumpfilen tids- och datumstämplad.
- **`-o|--output=<path>` är den absoluta filsystemsökvägen för lagring av säkerhetskopian (krävs).
- **`-l|--logs`** innehåller loggfiler (valfritt).
- **`-i|--ignore-sanitize`** betyder att data bevaras. Utelämna flaggan för att hash-koda känsliga data som lagras i databasen när du skapar säkerhetskopian (valfritt).

Känsliga data innehåller kundinformation från följande databastabeller:

```terminal
'customer_entity',
'customer_entity_varchar',
'customer_address_entity',
'customer_address_entity_varchar',
'customer_grid_flat',
'quote',
'quote_address',
'sales_order',
'sales_order_address',
'sales_order_grid'
```

När kommandot har slutförts kan du säkerhetskopiera databasen till Adobe Commerce Support.

## Felsökning: visningsverktyg och sökvägar

Vi tillhandahåller kommandon som visar sökvägar till verktyg som krävs av datainsamlaren och kommandoraden. Du kan till exempel använda dessa kommandon om fel som följande visas i Admin eller på kommandoraden:

```terminal
Utility lsof not found
```

Kör följande kommandon i den ordning som visas för att visa sökvägarna till de program som används av supportverktygen och datainsamlaren:

1. Ändra till installationskatalogen för Commerce.

   Exempel: `cd /var/www/magento2`

   >[!INFO]
   >
   >Kommandona fungerar korrekt _endast_ från installationskatalogen.

1. `bin/magento support:utility:paths` skapar `<magento_root>/var/support/Paths.php`, som listar sökvägarna till alla program som används av verktyget.
1. `bin/magento support:utility:check` visar sökvägarna till filsystemet.

Ett exempel följer:

```terminal
   gzip => /bin/gzip
   lsof => /usr/sbin/lsof
   mysqldump => /usr/bin/mysqldump
   nice => /bin/nice
   php => /usr/bin/php
   tar => /bin/tar
   sed => /bin/sed
   bash => /bin/bash
   mysql => /usr/bin/mysql
```

För att lösa problem med att köra verktygen kontrollerar du att programmen är installerade och finns i webbserveranvändarens `$PATH` miljövariabel.
