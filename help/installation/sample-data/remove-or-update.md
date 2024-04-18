---
title: Ta bort eller uppdatera exempeldatamoduler
description: Följ de här stegen för att hantera Adobe Commerce exempeldatamoduler.
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Ta bort eller uppdatera exempeldatamoduler

I det här avsnittet beskrivs hur du:

* [Ta bort exempeldatamoduler](#remove-sample-data-modules) från en Adobe Commerce-installation `composer.json`. Det här alternativet gör det *not* ta bort exempeldata från databasen.

* [Förbered uppdatering av exempeldata](#prepare-to-update-sample-data) (till exempel innan du uppdaterar programmet Magento).

## Ta bort exempeldatamoduler

Ange följande kommando:

```bash
bin/magento sampledata:remove
```

En fullständig lista över exempeldatamoduler följer:

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

## Förbered uppdatering av exempeldata

Med det här kommandot kan du uppdatera exempeldata innan du uppdaterar Adobe Commerce.

Om du vill förbereda exempeldata för uppdatering anger du följande kommando:

```bash
bin/magento sampledata:reset
```

Efter det har [uppdatera programmet](../tutorials/uninstall.md#update-the-application).
