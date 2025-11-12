---
title: Aktivera loggning
description: Lär dig hur du aktiverar och inaktiverar olika typer av loggning i Adobe Commerce. Upptäck teknik för loggningskonfiguration och hantering.
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: aff705cefcd4de38d17cad41628bc8dbd6d630cb
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Aktivera loggning

{{file-system-owner}}

## Felsökningsloggning

Som standard skriver Commerce till felsökningsloggen (`<install_directory>/var/log/debug.log`) när den är i standardläge eller utvecklingsläge, men inte när den är i produktionsläge. Använd kommandot `bin/magento setup:config:set --enable-debug-logging` om du vill ändra standardvärdet.

>[!INFO]
>
>Från och med Commerce 2.3.1 kan du inte längre använda kommandot `bin/magento config:set dev/debug/debug_logging` för att aktivera eller inaktivera felsökningsloggning för det aktuella läget.

### Aktivera felsökningsloggning

1. Använd kommandot `setup:config:set` för att aktivera felsökningsloggning för det aktuella läget.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Töm cacheminnet.

   ```bash
   bin/magento cache:flush
   ```

### Så här inaktiverar du felsökningsloggning

1. Använd kommandot `setup:config:set` för att inaktivera felsökningsloggning för det aktuella läget.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Töm cacheminnet.

   ```bash
   bin/magento cache:flush
   ```

## Databasloggning

Som standard skriver Commerce databasaktivitetsloggar till filen `<install-dir>/var/debug/db.log`.

### Sökloggningslagringsplats

När databasloggning är aktiverat lagrar Commerce frågeloggar på följande plats:

- **Frågoggfil**: `<install-directory>/var/debug/db.log`
- **Loggkatalog**: `<install-directory>/var/debug/`

Frågeloggen innehåller:
- SQL-frågor som körs av programmet
- Frågekörningstider
- Frågeparametrar och bindningar
- Databasanslutningsinformation

>[!NOTE]
>
>Frågeloggfilen kan snabbt bli stor i trafikmiljöer. Övervaka diskutrymmet och överväg att implementera loggrotation eller att regelbundet rensa frågeloggfilen.

### Aktivera databasloggning

1. Använd kommandot `dev:query-log` för att aktivera eller inaktivera databasloggning.

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. Töm cacheminnet.

   ```bash
   bin/magento cache:flush
   ```

### Visa frågeloggar

Du kan visa frågeloggarna med standardkommandon för filvisning:

```bash
# View the entire query log
cat var/debug/db.log

# View the last 100 lines of the query log
tail -n 100 var/debug/db.log

# Monitor the query log in real-time
tail -f var/debug/db.log

# Search for specific queries
grep "SELECT" var/debug/db.log
```

## Cron-loggning

I och med version 2.3.1 skapar Commerce nu en separat `cron`-logg. \
Commerce utförde nyligen seriös inloggning, vilket gav mer information men förlängde `system.log` avsevärt.
Genom att flytta `cron`-information till en dedikerad logg blir båda loggarna enklare att läsa.

Som standard skriver Commerce `cron`-information till filen `<install-directory>/var/log/cron.log`.

## Loggning av Syslog

Som standard skriver Commerce _syslog_-loggar till operativsystemfilen `syslog`.
Från och med Commerce 2.3.1 måste du använda kommandot `magento` för att aktivera eller inaktivera syslog.
Inställningen i Admin har tagits bort.

### Så här aktiverar du synkroniseringsloggning

Loggning till `syslog` är inaktiverat som standard.

1. Använd kommandot `setup:config:set` om du vill ändra databasvärdet `dev/syslog/syslog_logging` till `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Töm cacheminnet.

   ```bash
   bin/magento cache:flush
   ```

### Så här inaktiverar du synkroniseringsloggning

1. Använd kommandot `setup:config:set` om du vill ändra databasvärdet `dev/syslog/syslog_logging` till `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Töm cacheminnet.

   ```bash
   bin/magento cache:flush
   ```
