---
title: Ta bort eller uppdatera exempeldatamoduler
description: Följ de här stegen för att hantera exempeldatamoduler för Adobe Commerce och Magento Open Source.
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Ta bort eller uppdatera exempeldatamoduler

I det här avsnittet beskrivs hur du:

* [Ta bort exempeldatamoduler](#remove-sample-data-modules) från en Adobe Commerce- eller Magento Open Source-installation `composer.json`. Det här alternativet gör det *not* ta bort exempeldata från databasen.

* [Förbered uppdatering av exempeldata](#prepare-to-update-sample-data) (till exempel innan du uppdaterar programmet Magento).

## Ta bort exempeldatamoduler

Ange följande kommando:

```bash
bin/magento sampledata:remove
```

En fullständig lista över exempeldatamoduler följer:

Adobe Commerce och Magento Open Source:

* `magento/module-bundle-sample-data`
* `magento/module-catalog-rule-sample-data`
* `magento/module-catalog-sample-data`
* `magento/module-cms-sample-data`
* `magento/module-configurable-sample-data`
* `magento/module-customer-sample-data`
* `magento/module-downloadable-sample-data`
* `magento/module-grouped-product-sample-data`
* `magento/module-msrp-sample-data`
* `magento/module-offline-shipping-sample-data`
* `magento/module-product-links-sample-data`
* `magento/module-review-sample-data`
* `magento/module-sales-rule-sample-data`
* `magento/module-sales-sample-data`
* `magento/module-sample-data`
* `magento/module-swatches-sample-data`
* `magento/module-tax-sample-data`
* `magento/module-theme-sample-data`
* `magento/module-widget-sample-data`
* `magento/module-wishlist-sample-data`
* `magento/sample-data-media`

Endast Adobe Commerce:

* `magento/module-customer-balance-sample-data`
* `magento/module-gift-card-sample-data`
* `magento/module-gift-registry-sample-data`
* `magento/module-multiple-wishlist-sample-data`
* `magento/module-target-rule-sample-data`

## Förbered uppdatering av exempeldata

Med det här kommandot kan du uppdatera exempeldata innan du uppdaterar Adobe Commerce eller Magento Open Source.

Ange följande kommando för att förbereda exempeldata för uppdatering:

```bash
bin/magento sampledata:reset
```

Efter det [uppdatera programmet](../tutorials/uninstall.md#update-the-application).
