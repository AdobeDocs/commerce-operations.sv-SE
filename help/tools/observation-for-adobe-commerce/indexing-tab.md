---
title: The [!UICONTROL Indexing] tab
description: Läs mer om [!UICONTROL Indexing] flik för [!DNL Observation for Adobe Commerce].
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# The [!UICONTROL Indexing] tab

The **[!UICONTROL Indexing]** försöker förklara problem med indexering och identifiera potentiella orsaker.

## [!UICONTROL Core index invalidated]

![Core index ogiltigt](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

The **[!UICONTROL Core index invalidated]** bildrutan läser vid indexering av ogiltigförklaring över en vald tidsram. Om indexering sker samtidigt som andra resurskrävande [!DNL crons]blir det en stor belastning på webbplatsens resurser.

* `%Catalog Product Rule indexer has been invalidated%`) as `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`) as `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`) as `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`) as `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`) as `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`) as `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`) as `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`) as `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`) as `product_price_idx_reset`
* `%Stock indexer has been invalidated%`) as `stock_idx_reset`
* `%Inventory indexer has been invalidated%`) as `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`) as `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`) as `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![Baskunskaper](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

The **[!UICONTROL Core index rebuilds]** tittar på kärnindexet som återskapas under en vald tidsram. Här är strängarna som tolkas från loggarna för att ange att indexet har återskapats.

* `%Catalog Product Rule index has been rebuilt%`) as `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`) as `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`) as `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`) as `category_products_idx`
* `%Customer Grid index has been rebuilt%`) as `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`) as `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`) as `product_categories_idx`
* `%Product EAV index has been rebuilt%`) as `product_eav_idx`
* `%Product Price index has been rebuilt%`) as `product_price_idx`
* `%Stock index has been rebuilt%`) as `stock_idx`
* `%Inventory index has been rebuilt successfully%`) as `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`) as `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`) as `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![katalogsökindextabell(er)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

The **[!UICONTROL catalogsearch index table(s)]** används för att undersöka indextabeller för katalogsökning över en vald tidsram. Den här frågan undersöker varaktigheten för eventuella datalageråtgärder mot tabeller med `%catalogsearch%` i tabellnamnet.

## [!UICONTROL product index table(s)]

![produktindextabell(er)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

The **[!UICONTROL product index table(s)]** läser produktindextabeller i en vald tidsram. Den här frågan undersöker varaktigheten för eventuella datalageråtgärder mot tabeller med `%product%` i tabellnamnet.
