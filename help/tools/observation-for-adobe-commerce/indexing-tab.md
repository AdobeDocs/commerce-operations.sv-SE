---
title: Fliken [!UICONTROL Indexing]
description: Läs mer om fliken [!UICONTROL Indexing] i  [!DNL Observation for Adobe Commerce].
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Fliken [!UICONTROL Indexing]

Fliken **[!UICONTROL Indexing]** försöker förklara problem med indexering och identifiera potentiella orsaker.

## [!UICONTROL Core index invalidated]

![Kärnindexet har ogiltigförklarats](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

Bildrutan **[!UICONTROL Core index invalidated]** tittar på indexering av ogiltigförklaring över en vald tidsram. Om indexering sker samtidigt som andra resurskrävande [!DNL crons], kommer det att innebära en stor belastning på webbplatsresurserna.

* `%Catalog Product Rule indexer has been invalidated%`) som `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`) som `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`) som `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`) som `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`) som `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`) som `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`) som `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`) som `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`) som `product_price_idx_reset`
* `%Stock indexer has been invalidated%`) som `stock_idx_reset`
* `%Inventory indexer has been invalidated%`) som `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`) som `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`) som `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![Core index rebuilds](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

Ramen **[!UICONTROL Core index rebuilds]** tittar på kärnindexet som återskapas under en vald tidsram. Här är strängarna som tolkas från loggarna för att ange att indexet har återskapats.

* `%Catalog Product Rule index has been rebuilt%`) som `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`) som `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`) som `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`) som `category_products_idx`
* `%Customer Grid index has been rebuilt%`) som `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`) som `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`) som `product_categories_idx`
* `%Product EAV index has been rebuilt%`) som `product_eav_idx`
* `%Product Price index has been rebuilt%`) som `product_price_idx`
* `%Stock index has been rebuilt%`) som `stock_idx`
* `%Inventory index has been rebuilt successfully%`) som `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`) som `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`) som `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![katalogsökindextabell(er)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

Ramen **[!UICONTROL catalogsearch index table(s)]** tittar på indextabeller för katalogsökning över en vald tidsram. Den här frågan undersöker varaktigheten för eventuella datalageråtgärder mot tabeller med `%catalogsearch%` i tabellnamnet.

## [!UICONTROL product index table(s)]

![produktindextabell(er)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

Bildrutan **[!UICONTROL product index table(s)]** tittar på produktindextabeller över en vald tidsram. Den här frågan undersöker varaktigheten för eventuella datalageråtgärder mot tabeller med `%product%` i tabellnamnet.
