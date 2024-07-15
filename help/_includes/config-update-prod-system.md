---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# Uppdatera produktionssystem

**Så här uppdaterar du produktionssystemet**:

1. Logga in i produktionssystemet som filsystemsägare.
1. Byt till programroten och aktivera underhållsläge.

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   Ytterligare alternativ, som möjligheten att ange en vitlista för IP-adresser, finns i [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md).

1. Stoppa alla köarbetare som körs genom att ange `cron_run` till `false` i `app/etc/env.php` enligt följande:

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Uppdatera konfigurationen.

   ```bash
   bin/magento app:config:import
   ```

1. Slutligen `kill` alla aktiva konsumentprocesser.

   ```bash
   kill <PID>
   ```

   Där `PID` är process-ID:t som ska dödas, till exempel:

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
