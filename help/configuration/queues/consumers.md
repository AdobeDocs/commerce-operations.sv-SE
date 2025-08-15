---
title: Konsumenter i meddelandekön
description: Läs om användare av Adobe Commerce meddelandekö, inklusive funktioner och systemkonfigurationsinställningar som är kopplade till dem.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# Konsumenter i meddelandekön

I följande tabell visas alla meddelandeköanvändare, vad de gör och vilka konfigurationsinställningar för administratörssystemet som är kopplade till dem:

| Konsument och beskrivning | Adobe Commerce | Adobe Commerce med B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Skapar meddelanden för varje enskild åtgärd i en [gruppåtgärd](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), till exempel import eller export av artiklar, ändring av priser i en massskala och tilldelning av produkter till ett lagerställe. Krävs när alternativet [**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) är inställt på&#x200B;**[!UICONTROL Run asynchronously]**i konfigurationsinställningarna för administratörssystemet. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Genererar automatiskt kuponger i bakgrunden. Krävs för att använda funktionen [batchkuponggenerering](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons). |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Söker efter händelser som har registrerats som prioritet i [Adobe I/O Events för Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Förhindrar timeout för anslutningen vid [export](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) av stora datauppsättningar (till exempel 200 000 produkter). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Asynkront korrigerar aktieindexet efter att en order har placerats eller en produkt har tagits bort. Krävs när alternativet [**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#product-stock-options) är aktiverat i inställningarna för Admin-konfigurationen. Se [Bästa praxis för prestanda](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Tar asynkront bort källobjekt efter produkt-SKU när en produkt tas bort. Krävs när Stock-alternativet [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) är aktiverat i Admin-systemets konfigurationsinställningar. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Bearbetar tidigare artiklar i lager asynkront, uppdaterar gamla artiklar i lager, uppdaterar standardkällartiklar och indexerar om lager för specifika produkter. Krävs när gruppåtgärden [**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) är aktiverad i konfigurationsinställningarna för administratörssystemet. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Tar asynkront bort reservationer efter produkt-SKU när en produkt har tagits bort. Krävs när Stock-alternativet [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) är aktiverat i Admin-systemets konfigurationsinställningar. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Uppdaterar automatiskt reservationer per produkt-SKU när en produkt har tagits bort. Krävs när Stock-alternativet [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) är aktiverat i Admin-systemets konfigurationsinställningar. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Asynkront uppdaterar den försäljningsbara kvantiteten för varje produkt som tilldelats ett lager. Den här konsumenten ska alltid vara igång om du använder [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Indexerar om källobjekt asynkront. Krävs när [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) är inställd på [!UICONTROL asynchronous] i konfigurationsinställningarna för administratörssystemet. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Indexerar om lager asynkront. Krävs när [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) är inställd på [!UICONTROL asynchronous] i konfigurationsinställningarna för administratörssystemet. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Skapar en temporär databastabell, flyttar varje [kundsegment](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments) till det, tar bort alla segment som matchar segment-ID:t och kopierar dem till kundsegmenten med segment-ID som indikator. Detta görs i en transaktion så att om något misslyckas, återställs transaktionen till vad den var innan den utfördes. Efter en transaktion släpper konsumenten det tillfälliga registret. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Ser till att länkar till tilldelade medier för produkter, kategorier, CMS-block och CMS-sidor tilldelas till resursen på rätt sätt. Tar bort gamla resurser som inte längre används. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Skapar och validerar sökvägar för medieresurser. Den absoluta sökvägen till en resurs bestäms av var den finns på servern från mediekatalogen. Bildernas storlek ändras (om det behövs) och kopieras till mediekatalogen i den genererade sökvägen. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importerar bildfiler till databastabellen `media_gallery_asset`. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| [ändrar storlek på katalogbilder asynkront](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images). |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Uppdaterar priser för överlåtbara offerter. Krävs när alternativet [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) är aktiverat i konfigurationsinställningarna för administratörssystemet. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| [bearbetar beställningar](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) asynkront, vilket markerar beställningar som mottagna, placerar dem i meddelandekön och bearbetar dem först-i-först-ut-baserat. Betraktades som [bästa praxis](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) för att förbättra antalet order som kan bearbetas eftersom kunderna inte behöver vänta på att backend-processerna ska slutföras innan ett meddelande om att de lyckades visas. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| Skriver ändringar av produktattribut i databasen asynkront efter att Admin har använts för att [göra uppdateringar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Skriver ändringar av produktattribut asynkront för en viss butiksvy i databasen efter att Admin har använts för att [göra uppdateringar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_alert` | + | + | + |
| Skickar e-postmeddelanden till kunderna om produktpriser och lagerförändringar. Obligatoriskt när alternativet Obligatoriskt när alternativet [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) är aktiverat i inställningarna för administratörssystemkonfiguration. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Konverterar inköpsorder till [order](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules). Krävs när alternativet [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) är aktiverat i konfigurationsinställningarna för administratörssystemet. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Skickar e-postmeddelanden om inköpsorder. Krävs när alternativet [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) är aktiverat i konfigurationsinställningarna för administratörssystemet. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Validerar inköpsorder mot relevanta [godkännanderegler](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules). Krävs när alternativet [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) är aktiverat i konfigurationsinställningarna för administratörssystemet. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| Sparar ändringar i lagringskonfigurationen asynkront genom att placera sparade jobb i en meddelandekö, vilket kan förbättra prestanda för distributioner som innehåller ett stort antal konfigurationer på butiksnivå. Krävs för att använda modulen [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save). |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Förhindrar ett problem där engångskuponger kan användas flera gånger. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Uppdaterar kategorier som tilldelats en delad katalogkategori. Krävs när alternativet [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) är aktiverat i konfigurationsinställningarna för administratörssystemet. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Uppdateringspris för varje produkt i en delad katalog. Krävs när alternativet [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) är aktiverat i konfigurationsinställningarna för administratörssystemet. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Tar bort ogiltiga eller inaktiva prisnoteringar när en produkt tas bort från katalogen eller tas bort från kundvagnen. Krävs när alternativet [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) är aktiverat i konfigurationsinställningarna för administratörssystemet. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Uppdaterar aktiva kundvagnar för att återspegla ändringarna i kundvagnsprisregeln. Krävs vid uppdatering av [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
