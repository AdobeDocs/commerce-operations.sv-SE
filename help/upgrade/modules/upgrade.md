---
title: Uppgraderingsmoduler och tillägg
description: Använd kommandoradsgränssnittet och Composer för att uppgradera moduler och tillägg för Adobe Commerce och Magento Open Source.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Uppgraderingsmoduler och tillägg

Så här uppdaterar eller uppgraderar du en modul eller ett tillägg:

1. Hämta den uppdaterade filen från Marketplace eller någon annan tilläggsutvecklare. Notera modulens namn och version.

1. Exportera innehållet till Adobe Commerce eller Magento Open Source rotinstallationskatalog.

1. Om det finns ett Composer-paket för modulen kör du något av följande.

   Uppdatering per modulnamn:

   ```bash
   composer update vendor/module-name
   ```

   Uppdatering per version:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Kör följande kommandon för att uppgradera, distribuera och rensa cachen.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
