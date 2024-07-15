---
title: Development Environment Recommendations
description: Lär dig mer om prestandarekommendationer för att konfigurera din lokala Adobe Commerce-utvecklingsmiljö.
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Rekommendationer för utvecklingsmiljö

Den här sidan innehåller rekommendationer för Commerce utvecklingsmiljöer.

## Rensa cacheminnen i stället för att inaktivera

Många utvecklare tenderar att inaktivera alla cacheminnen på sina utvecklarinstanser. Vi rekommenderar att du bara städar cacher, utan att inaktivera alla cacheminnen. [!DNL Commerce] körs mer effektivt när du [rensar cacheminnen](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) i stället för att inaktivera dem helt. De flesta typer av cacher blir sällan ogiltiga under utvecklingen.

Om du [inaktiverar cacheminnen](../configuration/cli/manage-cache.md#enable-or-disable-cache-types) rekommenderar vi endast att du inaktiverar cacheminnen för sidor och block i utvecklingsinstanser. Kom ihåg att aktivera alla cacheminnen under testningen.

## Kommandon som ska undvikas i utvecklingsläget

I utvecklingsläget ska du inte köra kommandon för kompilering, kodgenerering och statisk innehållsdistribution. Dessa kommandon har skapats för användning endast i produktionsläge.

**Kör inte**-produktionskommandon i utvecklingsläge:

* `setup:di:compile` genererar automatiskt genererade klasser och optimerade konfigurationscache.

  ```bash
  bin/magento setup:di:compile
  ```

  I utvecklingsläget utför Magento genereringen on-demand, du behöver inte köra den. Om du har ändrat en signatur för en klass och behöver återskapa dess automatiskt genererade `factories/proxies/interceptors` tar du bort dessa klasser eller mappen _generated_.

* `setup:static-content:deploy` distribuerar statiskt innehåll för en butik.

  ```bash
  bin/magento setup:static-content:deploy
  ```

  I utvecklingsläget utför Magento det on-demand, du behöver inte köra det.

## Normal sidinläsningstid på en virtuell dator

Om du utvecklar på en virtuell dator och det tar längre tid än två sekunder att läsa in en Magento-sida, ska du granska dina miljöinställningar.
