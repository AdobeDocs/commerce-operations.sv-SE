---
title: '"Den [!UICONTROL Indexing] tab"'
description: Läs mer om [!UICONTROL Indexing] flik för [!DNL Observation for Adobe Commerce].
source-git-commit: 1f334f329b72b715afa7f3617b1ce2fb8004f816
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# The [!UICONTROL Indexing] tab

The **[!UICONTROL Indexing]** försöker förklara problem med indexering och identifiera potentiella orsaker.

## [!UICONTROL Core index invalidated]

![Core index ogiltigt](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

The **[!UICONTROL Core index invalidated]** bildrutan läser vid indexering av ogiltigförklaring över en vald tidsram. Om indexering sker samtidigt som andra resurskrävande crons, kommer det att innebära en stor belastning för webbplatsens resurser.

* %Catalog Product Rule indexer har gjorts ogiltig%) som catalog_product_rule_idx_reset
* &#39;%Catalog Rule Product indexer has invalidated%&#39;) as &#39;catalog_rule_product_idx_reset&#39;
* %Catalog Search-indexeraren har ogiltigförklarats%) som catalog_search_idx_reset
* &#39;%Category Products indexer has invalidated%&#39;) as &#39;category_products_idx_reset&#39;
* %Customer Grid indexer har ogiltigförklarats%) som customer_grid_idx_reset
* &#39;%Design Config Grid indexer har ogiltigförklarats%&#39;) som &#39;design_config_grid_idx_
* &#39;%Product Categories indexer has been invalidated%&#39;) as &#39;product_categories_idx_reset&#39;
* &#39;%Product EAV indexer har gjorts ogiltig%&#39;) som &#39;product_eav_idx_reset&#39;
* &#39;%Product Price indexer has been invalidated%&#39;) as &#39;product_price_idx_reset&#39;
* &#39;%Stock-indexeraren har ogiltigförklarats%&#39;) som &#39;stock_idx_reset&#39;
* %Inventory indexer har ogiltigförklarats%) som &#39;layer_idx_reset&#39;
* %Inventory indexer har ogiltigförklarats%) som &#39;layer_idx_reset&#39;
* %Sales Rule indexer has invalidated%) as &#39;sales_rule_idx_reset&#39;

## [!UICONTROL Core index rebuilds]

![Baskunskaper](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

The **[!UICONTROL Core index rebuilds]** tittar på kärnindexet som återskapas under en vald tidsram. Här är strängarna som tolkas från loggarna för att ange att indexet har återskapats.

* %Catalog Product Rule index has been rebuilt%) as &#39;catalog_product_rule_idx&#39;
* %Catalog Rule Product index has been rebuilt%) as &#39;catalog_rule_product_idx&#39;
* %Catalog Search-indexet har återskapats%) som catalog_search_idx
* %Category Products index has rebuilt%) as &#39;category_products_idx&#39;
* %Customer Grid index has been rebuilt%) as &#39;customer_grid_idx&#39;
* %Design Config Grid-index har återskapats%) som design_config_grid_idx
* &#39;%Product Categories index has been rebuilt%&#39;) as &#39;product_categories_idx&#39;
* &#39;%Product EAV index has been rebuilt%&#39;) as &#39;product_eav_idx&#39;
* &#39;%Product Price index has been rebuilt%&#39;) as &#39;product_price_idx&#39;
* %Stock-indexet har återskapats%) som stock_idx
* %Inventory index har återskapats%) som &#39;Inventory_idx&#39;
* %Product/Target-regelindex har återskapats%) som prod_target_rule_idx
* &#39;%Sales Rule index has rebuilt%&#39;) as &#39;sales_rule_idx&#39;


## [!UICONTROL catalogsearch index table(s)]

![katalogsökindextabell(er)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

The **[!UICONTROL catalogsearch index table(s)]** används för att undersöka indextabeller för katalogsökning över en vald tidsram. Den här frågan undersöker varaktigheten för eventuella datalageråtgärder mot tabeller med &quot;%catalogsearch%&quot; i tabellnamnet.

## [!UICONTROL product index table(s)]

![produktindexregister](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

The **[!UICONTROL product index table(s)]** bildrutan tittar på produktindextabeller över en vald tidsram. Den här frågan undersöker varaktigheten för eventuella datalageråtgärder mot tabeller med &quot;%product%&quot; i tabellnamnet.
