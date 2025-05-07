---
title: 'ACSD-64523: REST-slutpunkten kan inte validera obligatoriska fält'
description: Använd patchen ACSD-64523 för att åtgärda problemet där REST-slutpunkten `[V1/import/csv]` inte validerar obligatoriska fält, vilket gör det möjligt att skapa produkter utan att tillhandahålla obligatoriska fält.
feature: REST, Products, Admin Workspace
role: Admin, Developer
source-git-commit: 4bf9a5eb2e423f5981ee9234be57230a6dff3913
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# ACSD-64523: REST-slutpunkten kan inte validera obligatoriska fält

Korrigeringen ACSD-64523 åtgärdar ett problem där REST-slutpunkten [V1/import/csv] inte kan validera obligatoriska fält, vilket gör att produkten kan skapas utan nödvändiga data. Du löser detta genom att uppdatera auktoriseringshuvudet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 är installerad. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

REST-slutpunkten `[V1/import/csv]` kan inte validera obligatoriska fält, vilket gör att produkter kan skapas utan att dessa obligatoriska fält anges.

<u>Steg som ska återskapas</u>:

1. Kör följande nyttolast (uppdatera auktoriseringshuvudet):

   ```
   curl --location 'http://<domain>/rest/default/V1/import/json' \
   --header 'Content-Type: application/json' \
   --header 'Authorization: Bearer xxxxx' \
   --data '{
       "source": {
           "locale": "en_AU",
           "entity": "catalog_product",
           "behavior": "append",
           "validation_strategy": "validation-stop-on-errors",
           "allowed_error_count": 0,
           "items": [
               {
                   "sku": "product_sku",
                   "product_online": "no",
                   "attribute_set_code": "Default",
                   "product_type": "configurable",
                   "product_websites": "base",
                   "store_view_code": "default",
                   "name": null,
                   "description": null,
                   "short_description": null,
                   "weight": null,
                   "tax_class_name": null,
                   "visibility": null,
                   "price": null,
                   "url_key": null,
                   "cost": null,
                   "additional_attributes": {
                       "special_price": "",
                       "retail_price": ""
                   },
                   "configurable_variations": []
               }
           ]
       }
   }'
   ```

<u>Förväntade resultat</u>:

Programmet bör förhindra att en produkt sparas utan obligatoriska fält.

<u>Faktiska resultat</u>:

Produkten sparades utan att produktnamnet angavs, vilket är ett obligatoriskt attribut. Därför kan vi inte komma åt serverdelens produktrutnät och det ger följande fel.

`Warning: Undefined array key "name" in /app/code/Magento/Catalog/Ui/Component/Listing/Columns/Thumbnail.php on line 91`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
