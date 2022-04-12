---
title: Uppgraderingsmoduler och tillägg
description: Använd kommandoradsgränssnittet och Composer för att uppgradera moduler och tillägg för Adobe Commerce och Magento Open Source.
source-git-commit: 70f1bda91023526fbc0024b6a6fef93c7633ecc2
workflow-type: tm+mt
source-wordcount: '161'
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

## VBE (Leverantör bundled extensions)

Adobe har tagit bort alla [VBE](https://devdocs.magento.com/extensions/vendor/) i 2.4.4. Leverantörer fortsätter att ha stöd för dessa tillägg på Adobe Commerce Marketplace.

Om du vill fortsätta använda dessa tillägg med Adobe Commerce och Magento Open Source 2.4.4 och senare måste du uppdatera motsvarande paketberoenden i `composer.json` fil _före_ uppgradering till 2.4.4. Kontakta leverantören för det paketnamn och den version som ska användas.
