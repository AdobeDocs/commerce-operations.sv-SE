---
title: Development Environment Recommendations
description: Lär dig mer om prestandarekommendationer för att konfigurera din lokala Adobe Commerce- eller Magento Open Source-utvecklingsmiljö.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Rekommendationer för utvecklingsmiljö

Den här sidan innehåller rekommendationer för Commerce-utvecklingsmiljöer.

## Rensa cacheminnen i stället för att inaktivera

Många utvecklare tenderar att inaktivera alla cacheminnen på sina utvecklarinstanser. Vi rekommenderar att du bara städar cacheminnen, utan att inaktivera alla cacheminnen. [!DNL Commerce] blir effektivare när du [rengöra cacheminnen] i stället för att inaktivera dem helt. De flesta typer av cacher blir sällan ogiltiga under utvecklingen.

Om du [inaktivera caches]rekommenderar vi att du bara inaktiverar Page- och Block-cacher i utvecklingsinstanser. Kom ihåg att aktivera alla cacheminnen under testningen.

## Kommandon som ska undvikas i utvecklingsläget

I utvecklingsläget ska du inte köra kommandon för kompilering, kodgenerering och statisk innehållsdistribution. Dessa kommandon har skapats för användning endast i produktionsläge.

**Kör inte** produktionskommandon i utvecklingsläge:

* `setup:di:compile` genererar automatiskt genererade klasser och optimerade konfigurationscache.

   ```bash
   bin/magento setup:di:compile
   ```

   I utvecklingsläget utför Magento produktionen on demand. du inte behöver köra den. Om du har ändrat en signatur för en klass och behöver återskapa dess automatiskt genererade `factories/proxies/interceptors`, tar bort dessa klasser eller _genererad_ mapp.

* `setup:static-content:deploy` distribuerar statiskt innehåll för en butik.

   ```bash
   bin/magento setup:static-content:deploy
   ```

   I utvecklingsläget utför Magento detta på begäran. du inte behöver köra den.

## Normal sidinläsningstid på en virtuell dator

Om du utvecklar på en virtuell dator och det tar längre tid än två sekunder att läsa in en Magento-sida, ska du granska dina miljöinställningar.

<!-- Link definitions -->

[rengöra cacheminnen]: ../configuration/cli/manage-cache.md#clean-and-flush-cache-types
[inaktivera caches]: ../configuration/cli/manage-cache.md#enable-or-disable-cache-types
