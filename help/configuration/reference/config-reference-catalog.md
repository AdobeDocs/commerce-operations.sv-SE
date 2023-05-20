---
title: Referens för katalogkonfigurationssökvägar
description: Se en lista med katalogkonfigurationsvärden.
exl-id: 19451443-228e-437d-a3eb-7dc968b9fb0d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---

# Referens för katalogkonfigurationssökvägar

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **Lager** > Inställningar > **Konfiguration** > **Katalog**.

The [`magento app:config:dump` kommando](../cli/export-configuration.md) skriver dessa värden i den delade konfigurationsfilen, `app/etc/config.php`, som bör vara i källkontroll. Om du vill åsidosätta konfigurationsinställningar eller ange känsliga inställningar läser du [Använd miljövariabler för att åsidosätta konfigurationsinställningar](override-config-settings.md#environment-variables). Det här avsnittet gör _not_ list [känsliga och systemspecifika värden](config-reference-sens.md).

## Katalogsökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Katalog** > **Katalog**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Mask for SKU | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mask for Meta Title | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mask for Meta Keywords | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mask for Meta Description | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Listläge | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produkter per sida på tillåtna värden för stödraster | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produkter per sida på standardvärde för stödraster | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produkter per sida i listan över tillåtna värden | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardvärde för produkter per sida i listan | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produktlista sortera efter | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåt alla produkter per sida | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd platt katalogkategori | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd platt katalogprodukt | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Färgrutor per produkt | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåt gäster att skriva granskningar | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåt avisering när produktpriser ändras | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för prisavisering | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåt avisering när produkten kommer tillbaka i Stock | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för Stock-avisering | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postaviseringsavsändare | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frekvens | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Starttid | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändare med fel | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för fel | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa för aktuell | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Antal senast visade standardprodukter | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Antal senast jämförda standardprodukter | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autostarta basvideo | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa relaterad video | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Starta om video automatiskt | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Katalogprisomfång | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardproduktpris | `catalog/price/default_product_price` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Visa produktantal | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stegberäkning för prisnavigering | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardprisnavigeringssteg | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa prisintervall som ett pris | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximalt antal prisintervall | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervalldivisionsgräns | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximalt djup | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimal frågelängd | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal frågelängd | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sökmotor | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout för Solr-server | `catalog/search/solr_server_timeout` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Indexeringsläge | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera sökförslag | `catalog/search/search_suggestion_enabled` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Antal sökförslag | `catalog/search/search_suggestion_count` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Visa resultatantal för varje förslag | `catalog/search/search_suggestion_count_results_enabled` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktivera sökning i Recommendations | `catalog/search/search_recommendations_enabled` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sök efter Recommendations Count | `catalog/search/search_recommendations_count` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Visa resultatantal för varje rekommendation | `catalog/search/search_recommendations_count_results_enabled` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minimivillkor att matcha | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Generera URL-omskrivningar för&quot;kategori/produkt&quot; | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vanliga sökvillkor | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Produkt-URL-suffix | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kategori-URL-suffix | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd kategorisökväg för produkt-URL:er | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skapa permanent omdirigering för URL:er om URL-nyckeln har ändrats | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sidtitelavgränsare | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd metataggen för kanoniska länkar för kategorier | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd metataggen för kanoniska länkar för produkter | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera | `catalog/magento_catalogpermissions/enabled` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt bläddringskategori | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kundgrupper | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Landningssida | `catalog/magento_catalogpermissions/restricted_landing_page` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Visa produktpriser | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kundgrupper | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt tillägg i kundvagnen | `catalog/magento_catalogpermissions/grant_checkout_items` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kundgrupper | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt inte katalogsökning efter | `catalog/magento_catalogpermissions/deny_catalog_search` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Beställningsstatus för att aktivera nedladdningar | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximalt standardantal hämtningar | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Delningsbart | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardexempeltitel | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardnamn för länk | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Öppna länkar i nytt fönster | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd innehålldisposition | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inaktivera gästutcheckning om kundvagnen innehåller hämtningsbara objekt | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd JavaScript-kalender | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Datumfältordning | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tidsformat | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| År | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera kataloghändelsefunktioner | `catalog/magento_catalogevent/enabled` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktivera widgeten Kataloghändelse på Storefront | `catalog/magento_catalogevent/lister_output` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Antal händelser som ska visas i widgeten för händelsereglage | `catalog/magento_catalogevent/lister_widget_limit` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Händelser som ska rullas per klickning i händelseskjutreglagets widget | `catalog/magento_catalogevent/lister_widget_scroll` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximalt antal produkter i listan över relaterade produkter | `catalog/magento_targetrule/related_position_limit` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Visa relaterade produkter | `catalog/magento_targetrule/related_position_behavior` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Rotationsläge för produkter i relaterad produktlista | `catalog/magento_targetrule/related_rotation_mode` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximalt antal produkter i korsförsäljningsproduktlistan | `catalog/magento_targetrule/crosssell_position_limit` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Visa korsförsäljningsprodukter | `catalog/magento_targetrule/crosssell_position_behavior` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Rotationsläge för produkter i korsförsäljningsproduktlista | `catalog/magento_targetrule/crosssell_rotation_mode` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximalt antal produkter i merförsäljningsproduktlistan | `catalog/magento_targetrule/upsell_position_limit` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Visa merförsäljning | `catalog/magento_targetrule/upsell_position_behavior` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Rotationsläge för produkter i merförsäljningsproduktlista | `catalog/magento_targetrule/upsell_rotation_mode` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Lagersökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Katalog** > **Lager**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Minska lager när beställningen placeras | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ange att objektstatus ska vara i lager när ordern annulleras | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa ej lagrade produkter | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Endast X vänster tröskelvärde | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa produkttillgänglighet i Stock på Storefront | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Synkronisera med katalog | `cataloginventory/options/synchronize_with_catalog` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Hantera Stock | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Restorder | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd fördröjd Stock-uppdatering | `cataloginventory/item_options/use_deferred_stock_update` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Högsta tillåtna antal i kundvagn | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tröskelvärde utanför lagret | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta tillåtna kvantitet i kundvagn | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Meddela om kvantitet nedan | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera ökning av kvantitet | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Antal ökningar | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Returnera automatiskt kreditfakturaartikel till lager | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kör asynkront | `cataloginventory/bulk_operations/async` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Asynkron batchstorlek | `cataloginventory/bulk_operations/batch_size` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Provider | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beräkningsläge | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Värde | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Visual Merchandiser paths

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Katalog** > **Visual Merchandiser**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Synliga attribut för kategoriregler | `visualmerchandiser/options/smart_attributes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minsta lagertröskel | `visualmerchandiser/options/minimum_stock_threshold` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Färgattributkod | `visualmerchandiser/options/color_attribute_code` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Färgordning | `visualmerchandiser/options/color_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Sökvägar för XML-webbplatskartor

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Katalog** > **XML-webbplatskarta**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Frekvens | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prioritet | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frekvens | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prioritet | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lägg till bilder i webbplatskartan | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frekvens | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prioritet | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Starttid | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frekvens | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändare med fel | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för fel | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximalt antal URL:er per fil | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal filstorlek | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera överföring till Robots.txt | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Sökvägar för RSS-flöden

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Katalog** > **RSS-flöden**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Aktivera RSS | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera RSS | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nya produkter | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Specialprodukter | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kuponger/rabatter | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kategori på översta nivån | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Meddelande om kundorderstatus | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## E-post till en vän

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Katalog** > **Skicka e-post till en vän**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Aktiverad | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Välj e-postmall | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåt för gäster | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Max antal mottagare | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Max antal skickade produkter inom 1 timme | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Begränsa sändning med | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
