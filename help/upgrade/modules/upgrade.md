---
title: Uppgraderingsmoduler och tillägg
description: Använd kommandoradsgränssnittet och Composer för att uppgradera Adobe Commerce-moduler och tillägg.
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Uppgraderingsmoduler och tillägg

Så här uppdaterar eller uppgraderar du en modul eller ett tillägg:

1. Hämta den uppdaterade filen från Marketplace eller någon annan tilläggsutvecklare. Notera modulens namn och version.

1. Exportera innehållet till Adobe Commerce rotinstallationskatalog.

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

Adobe tog bort alla [VBE](https://experienceleague.adobe.com/sv/docs/commerce-operations/upgrade-guide/modules/upgrade) i 2.4.4. Leverantörer fortsätter att ha stöd för dessa tillägg på Adobe Commerce Marketplace.

Om du vill fortsätta använda dessa tillägg med Adobe Commerce 2.4.4 och senare måste du uppdatera motsvarande paketberoenden i `composer.json`-filen _innan_ uppgraderar till 2.4.4. Kontakta leverantören för det paketnamn och den version som ska användas.

Mer information finns i följande Adobe Commerce Marketplace-listor:

- [Amazon Pay](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)
- [Hörn](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [Yotpo](https://marketplace.magento.com/yotpo-module-yotpo.html)
