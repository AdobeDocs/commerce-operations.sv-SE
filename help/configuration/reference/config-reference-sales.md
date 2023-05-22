---
title: Referens för försäljningskonfigurationssökvägar
description: Visa en lista med värden för försäljningskonfigurationer.
feature: Configuration, Checkout, Gift, Shipping/Delivery, Taxes
exl-id: 7981f78a-5e5f-422c-9bff-54022e1fb9f3
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '1473'
ht-degree: 0%

---

# Referens för försäljningskonfigurationssökvägar

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **Lager** > Inställningar > **Konfiguration** > **Försäljning**.

The [`magento app:config:dump` kommando](../cli/export-configuration.md) skriver dessa värden i den delade konfigurationsfilen, `app/etc/config.php`, som bör vara i källkontroll. Om du vill åsidosätta konfigurationsinställningar eller ange känsliga inställningar läser du [Använd miljövariabler för att åsidosätta konfigurationsinställningar](override-config-settings.md#environment-variables). Det här avsnittet gör _not_ list [känsliga och systemspecifika värden](config-reference-sens.md).

## Försäljningsvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Försäljning** > **Försäljning**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Dölj Kund-IP | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Delsumma | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rabatt | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverans | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moms | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fast produktskatt | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Summa | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Presentkort | `sales/totals_sort/giftcardaccount` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Butikskrediter | `sales/totals_sort/customerbalance` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt ombeställning | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo for PDF Print-outs (200x50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logotyp för HTML Print View | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adress | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimibelopp | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inkludera moms i belopp | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beskrivningsmeddelande | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fel som visas i kundvagnen | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validera varje adress separat i en utcheckning av flera adresser | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beskrivningsmeddelande för flera adresser | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fleradressfel som ska visas i kundvagnen | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd aggregerade data | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Löptid för väntande betalningsorder (minuter) | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåt presentmeddelanden på ordernivå | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåt presentmeddelanden för orderartiklar | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåt flyttning av presentkort på ordernivå | `sales/gift_options/wrapping_allow_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt Presentbrytning för orderobjekt | `sales/gift_options/wrapping_allow_items` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt presentkvitto | `sales/gift_options/allow_gift_receipt` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt utskrivna kort | `sales/gift_options/allow_printed_card` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Standardpris för utskrivet kort | `sales/gift_options/printed_card_price` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktivera MAP | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa faktiskt pris | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardmeddelande för popup-text | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardtextmeddelande för &quot;What&#39;s This&quot; | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera Beställning efter SKU på Mitt konto i Storefront | `sales/product_sku/my_account_enable` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Knapptext | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kundgrupper | `sales/product_sku/allowed_groups` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktivera arkivering | `sales/magento_salesarchive/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Arkivera inköpsorder | `sales/magento_salesarchive/age` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Orderstatus som ska arkiveras | `sales/magento_salesarchive/order_statuses` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktivera RMA på Storefront | `sales/magento_rma/enabled` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktivera RMA på produktnivå | `sales/magento_rma/enabled_on_product` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Använd butiksadress | `sales/magento_rma/use_store_address` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Sökvägar för e-post

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Försäljning** > **Försäljningsmejl**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Asynkron sändning | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny e-postavsändare för orderbekräftelse | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderbekräftelsemall | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderbekräftelsemall för gäst | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skicka e-postkopia av order | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändare för orderkommentar | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för orderkommentar | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för orderkommentar för gäst | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skicka e-postkopia av orderkommentarer | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Avsändare av fakturameddelande | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för faktura | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för faktura för gäst | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skicka e-postkopieringsmetod för faktura | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändare för fakturakommentar | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för fakturakommentar | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för fakturakommentar för gäst | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skicka e-postkopieringsmetod för fakturakommentarer | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändare för leverans | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för leverans | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för leverans för gäst | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skicka e-postkopieringsmetod för utleverans | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändare för försändelsekommentar | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för försändelsekommentar | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för försändelsekommentar för gäst | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skicka e-postkopieringsmetod för utleveranskommentarer | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändare för kreditnota | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för kreditnota | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för kreditnota för gäst | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skicka e-postkopieringsmetod för kreditnota | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändare för kreditnotskommentar | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för kreditnotkommentar | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för kreditnotkommentar för gäst | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skicka e-postkopieringsmetod för kreditnotkommentarer | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `sales_email/magento_rma/enabled` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| RMA-e-postavsändare | `sales_email/magento_rma/identity` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| RMA-e-postmall | `sales_email/magento_rma/template` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Mall för RMA-e-post för gäst | `sales_email/magento_rma/guest_template` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Skicka RMA-postkopieringsmetod | `sales_email/magento_rma/copy_method` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `sales_email/magento_rma_auth/enabled` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| E-postavsändare för RMA-auktorisering | `sales_email/magento_rma_auth/identity` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| E-postmall för RMA-auktorisering | `sales_email/magento_rma_auth/template` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| E-postmall för RMA-auktorisering för gäst | `sales_email/magento_rma_auth/guest_template` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Skicka e-postkopieringsmetod för RMA-auktorisering | `sales_email/magento_rma_auth/copy_method` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `sales_email/magento_rma_comment/enabled` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| E-postavsändare för RMA-kommentar | `sales_email/magento_rma_comment/identity` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| E-postmall för RMA-kommentar | `sales_email/magento_rma_comment/template` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| E-postmall för RMA-kommentar för gäst | `sales_email/magento_rma_comment/guest_template` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Skicka RMA-postkopieringsmetod | `sales_email/magento_rma_comment/copy_method` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `sales_email/magento_rma_customer_comment/enabled` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| E-postavsändare för RMA-kommentar | `sales_email/magento_rma_customer_comment/identity` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| E-postmottagare för RMA-kommentar | `sales_email/magento_rma_customer_comment/recipient` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| E-postmall för RMA-kommentar | `sales_email/magento_rma_customer_comment/template` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Skicka RMA-postkopieringsmetod | `sales_email/magento_rma_customer_comment/copy_method` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Visa order-ID i sidhuvud | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa order-ID i sidhuvud | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa order-ID i sidhuvud | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Skattevägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Försäljning** > **Moms**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Skatteklass för leverans | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skatteklass för presentalternativ | `tax/classes/wrapping_tax_class` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Standardskatteklass för produkt | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardskatteklass för kund | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Momsberäkningsmetod baserad på | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skatteberäkning baserad på | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Katalogpriser | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leveranspriser | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd kundskatt | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd rabatt på priser | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd skatt på | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera gränsöverskridande handel | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardland | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardläge | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardpostnummer | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa produktpriser i katalog | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa leveranspriser | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visningspriser | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa delsumma | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa leveransbelopp | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa presentpriser | `tax/cart_display/gift_wrapping` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Visa utskrivna kortpriser | `tax/cart_display/printed_card` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Inkludera moms i ordersumma | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa fullständig momssammanfattning | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa delsumma för nollskatt | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visningspriser | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa delsumma | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa leveransbelopp | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa presentpriser | `tax/sales_display/gift_wrapping` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Visa utskrivna kortpriser | `tax/sales_display/printed_card` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Inkludera moms i ordersumma | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa fullständig momssammanfattning | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa delsumma för nollskatt | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera FPT | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa priser i produktlistor | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa priser på produktvisningssidan | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa priser i försäljningsmoduler | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa priser i e-post | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillämpa skatt på FPT | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inkludera FPT i delsumma | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Utcheckningsbanor

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Försäljning** > **Utcheckning**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Aktivera OnePage-utcheckning | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåt gästutcheckning | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa faktureringsadress på | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera villkor | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Offertens livstid (dagar) | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Efter att en produktomdirigering lagts till i kundvagnen | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupperad produktbild | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konfigurerbar produktbild | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Livstid för förhandsgranskning av offert (minuter) | `checkout/cart/preview_quota_lifetime` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Visa kundvagnssammanfattning | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa kundvagn, sidopanel | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximalt antal senast tillagda objekt | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändaren kunde inte betala | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmottagare för betalning misslyckades | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mall för misslyckad betalning | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skicka betalning misslyckades med e-postkopieringsmetod | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Banor för leveransinställningar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Försäljning** > **Leveransinställningar**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Använd anpassad leveranspolicy | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leveranspolicy | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Banor för multileveransinställningar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Försäljning** > **Inställningar för flera leveranser**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Tillåt leverans till flera adresser | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Högsta tillåtna antal för leverans till flera adresser | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Sökvägar för leveransmetoder

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Försäljning** > **Leveransmetoder**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Aktiverad | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodnamn | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typ | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pris | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beräkna hanteringsavgift | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hanteringsavgift | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felmeddelande som visas | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till tillämpliga länder | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till specifika länder | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa metod om den inte är tillämplig | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodnamn | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta orderbelopp | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felmeddelande som visas | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till tillämpliga länder | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till specifika länder | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa metod om den inte är tillämplig | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodnamn | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Villkor | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inkludera virtuella produkter i prisberäkning | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exportera | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Importera | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beräkna hanteringsavgift | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hanteringsavgift | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felmeddelande som visas | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till tillämpliga länder | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till specifika länder | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa metod om den inte är tillämplig | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad för utcheckning | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverat för RMA | `carriers/ups/active_rma` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| UPS-typ | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Läge | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leveransens ursprung | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gateway-URL | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera förhandlade hastigheter | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typ av paketbegäran | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Behållare | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Viktenhet | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Måltyp | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal paketvikt (kontakta din fraktfirma för att få information om högsta möjliga fraktvikt) | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hämtningsmetod | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta paketvikt (kontakta din fraktfirma för att få information om minsta möjliga fraktvikt) | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beräkna hanteringsavgift | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hantering används | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hanteringsavgift | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåtna metoder | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ledig metod | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera tröskelvärde för kostnadsfri leverans | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tröskelvärde för kostnadsfritt leveransbelopp | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felmeddelande som visas | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till tillämpliga länder | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till specifika länder | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa metod om den inte är tillämplig | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad för utcheckning | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverat för RMA | `carriers/usps/active_rma` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Läge | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typ av paketbegäran | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Behållare | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storlek | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Längd | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bredd | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Höjd | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Girth | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maskinvara | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal paketvikt (kontakta din fraktfirma för att få information om högsta möjliga fraktvikt) | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beräkna hanteringsavgift | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hantering används | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hanteringsavgift | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåtna metoder | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ledig metod | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera tröskelvärde för kostnadsfri leverans | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tröskelvärde för kostnadsfritt leveransbelopp | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felmeddelande som visas | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till tillämpliga länder | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till specifika länder | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa metod om den inte är tillämplig | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad för utcheckning | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverat för RMA | `carriers/fedex/active_rma` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Webbtjänst-URL (produktion) | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Webbtjänst-URL (sandlåda) | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typ av paketbegäran | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paketering | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dropoff | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Viktenhet | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal paketvikt (kontakta din fraktfirma för att få information om högsta möjliga fraktvikt) | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beräkna hanteringsavgift | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hantering används | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hanteringsavgift | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bostadsleverans | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåtna metoder | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hub-ID | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ledig metod | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera tröskelvärde för kostnadsfri leverans | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tröskelvärde för kostnadsfritt leveransbelopp | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felmeddelande som visas | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till tillämpliga länder | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till specifika länder | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa metod om den inte är tillämplig | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad för utcheckning | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverat för RMA | `carriers/dhl/active_rma` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Innehållstyp | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beräkna hanteringsavgift | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hantering används | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hanteringsavgift | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dela upp orderbredd | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Viktenhet | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storlek | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Höjd | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Djup | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bredd | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåtna metoder | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåtna metoder | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Klar tid | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felmeddelande som visas | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ledig metod | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ledig metod | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera tröskelvärde för kostnadsfri leverans | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tröskelvärde för kostnadsfritt leveransbelopp | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till tillämpliga länder | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverera till specifika länder | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa metod om den inte är tillämplig | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Google API-sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Försäljning** > **Google API**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Aktivera | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kontotyp | `google/analytics/type` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktivera innehållsexperiment | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| List-egenskap för katalogsidan | `google/analytics/catalog_page_list_value` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| List-egenskap för korsförsäljningsblocket | `google/analytics/crosssell_block_list_value` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| List-egenskap för merförsäljningsblocket | `google/analytics/upsell_block_list_value` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| List-egenskap för det relaterade produktblocket | `google/analytics/related_block_list_value` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Listegenskap för sökresultatsidan | `google/analytics/search_page_list_value` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| &quot;Internal Promotion&quot; för kampanjfältet &quot;Label&quot;. | `google/analytics/promotions_list_value` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktivera | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konverterings-ID | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konverteringsspråk | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konverteringsformat | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konverteringsfärg | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konverteringsetikett | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typ av konverteringsvärde | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Konverteringsvärde | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Presentkortsbanor

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Försäljning** > **Presentkort**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| E-postavsändare för presentkortsmeddelande | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för presentkortsmeddelanden | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inlösbar | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Livstid (dagar) | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåt presentmeddelande | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal längd för presentmeddelande | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Generera presentkortskonto när orderartikeln är | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Presentkortets e-postavsändare | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Presentkortsmall | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kodlängd | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kodformat | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kodprefix | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kodsuffix | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Streck var X tecken | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny poolstorlek | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pooltröskel med låg kod | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
