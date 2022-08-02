---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---
# Uppdatera produktionssystem

**Uppdatera produktionssystemet**:

1. Logga in i produktionssystemet som filsystemsägare.
1. Byt till programroten och aktivera underhållsläge.

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   Ytterligare alternativ, som möjligheten att ange en vitlista för IP-adresser, finns i [`magento maintenance:enable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. Stoppa alla köarbetare som körs genom att ange `cron_run` till `false` in `app/etc/env.php` enligt följande:

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Uppdatera konfigurationen.

   ```bash
   bin/magento app:config:import
   ```

1. Äntligen `kill` alla aktiva konsumentprocesser.

   ```bash
   kill <PID>
   ```

   Plats `PID` är det process-ID som ska dödas, till exempel:

   ```bash
   kill 1234
   ```

1. Dra in kod från källkontrollen.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Uppdatera konfigurationen.

   ```bash
   bin/magento app:config:import
   ```

1. Rensa cachen.

   ```bash
   bin/magento cache:clean
   ```

1. Avsluta underhållsläge.

   ```bash
   bin/magento maintenance:disable
   ```
