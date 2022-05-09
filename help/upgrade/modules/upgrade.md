---
title: Uppgraderingsmoduler och tillägg
description: Använd kommandoradsgränssnittet och Composer för att uppgradera moduler och tillägg för Adobe Commerce och Magento Open Source.
source-git-commit: c619bff9785d22298bc49e2ac9874480ff7a320b
workflow-type: tm+mt
source-wordcount: '0'
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

Mer information finns i följande Adobe Commerce Marketplace-listor:

- [Amazon Pay](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)
- [Hörn](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [Yotpo](https://marketplace.magento.com/yotpo-module-yotpo.html)

