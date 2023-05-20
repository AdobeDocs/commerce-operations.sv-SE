---
title: Aktivera loggning
description: Lär dig hur du aktiverar och inaktiverar loggningstyper.
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Aktivera loggning

{{file-system-owner}}

## Felsökningsloggning

Som standard skriver Commerce till felsökningsloggen (`<install_directory>/var/log/debug.log`) när det är i standardläge eller framkallningsläge, men inte när det är i produktionsläge. Använd `bin/magento setup:config:set --enable-debug-logging` om du vill ändra standardvärdet.

>[!INFO]
>
>Från och med Commerce 2.3.1 kan du inte längre använda `bin/magento config:set dev/debug/debug_logging` om du vill aktivera eller inaktivera felsökningsloggning för det aktuella läget.

### Aktivera felsökningsloggning

1. Använd `setup:config:set` om du vill aktivera felsökningsloggning för det aktuella läget.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Töm cacheminnet.

   ```bash
   bin/magento cache:flush
   ```

### Så här inaktiverar du felsökningsloggning

1. Använd `setup:config:set` om du vill inaktivera felsökningsloggning för det aktuella läget.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Töm cacheminnet.

   ```bash
   bin/magento cache:flush
   ```

## Databasloggning

Som standard skriver Commerce databasaktivitetsloggar till `<install-dir>/var/debug/db.log` -fil.

### Aktivera databasloggning

1. Använd `dev:query-log` för att aktivera eller inaktivera databasloggning.

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

## Cron-loggning

I och med version 2.3.1 skapar nu Commerce en separat `cron` log. \
Handeln gjorde nyligen kronloggning mer utförlig, vilket gav mer information men förlängde `system.log` väsentligt.
Flyttar `cron` information i en dedikerad logg gör båda loggarna enklare att läsa.

Som standard skriver Commerce `cron` information till `<install-directory>/var/log/cron.log` -fil.

## Loggning av Syslog

Som standard skriver Commerce _syslog_ loggar till operativsystemet `syslog` -fil.
Från och med Commerce 2.3.1 måste du använda `magento` för att aktivera eller inaktivera syslog.
Inställningen i Admin har tagits bort.

### Aktivera loggning av syslog

Loggar till `syslog` är inaktiverat som standard.

1. Använd `setup:config:set` för att ändra `dev/syslog/syslog_logging` databasvärde till `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Töm cacheminnet.

   ```bash
   bin/magento cache:flush
   ```

### Så här inaktiverar du synkroniseringsloggning

1. Använd `setup:config:set` för att ändra `dev/syslog/syslog_logging` databasvärde till `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Töm cacheminnet.

   ```bash
   bin/magento cache:flush
   ```
