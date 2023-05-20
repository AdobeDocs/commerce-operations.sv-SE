---
title: Referens för sökvägar för betalningskonfiguration
description: Se en lista över konfigurerbara värden för betalningsmetoder.
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '4100'
ht-degree: 0%

---

# Referens för sökvägar för betalningskonfiguration

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Försäljning** > **Betalningsmetoder**.

The [`magento app:config:dump` kommando](../cli/export-configuration.md) skriver dessa värden i den delade konfigurationsfilen, `app/etc/config.php`, som bör vara i källkontroll. Om du vill åsidosätta konfigurationsinställningar eller ange känsliga inställningar läser du [Använd miljövariabler för att åsidosätta konfigurationsinställningar](override-config-settings.md#environment-variables). Det här avsnittet gör _not_ list [känsliga och systemspecifika värden](config-reference-sens.md).

Inställningarna ordnas ytterligare efter betalningsmetod.

## PayPal-banor

| Namn | Konfigurationssökväg | Endast handel? | Krypterad? |
|--------------|--------------|--------------|--------------|
| Aktivera den här lösningen | `payment/payflowpro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera sammanhangsbaserad utcheckning | `payment/paypal_express/in_context` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera PayPal-kredit | `payment/payflow_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera PayPal-kredit | `payment/paypal_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa | `payment/paypal_express_bml/homepage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/homepage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storlek | `payment/paypal_express_bml/homepage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa | `payment/paypal_express_bml/categorypage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/categorypage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storlek | `payment/paypal_express_bml/categorypage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa | `payment/paypal_express_bml/productpage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/productpage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storlek | `payment/paypal_express_bml/productpage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa | `payment/paypal_express_bml/checkout_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Position | `payment/paypal_express_bml/checkout_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storlek | `payment/paypal_express_bml/checkout_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa på sidan Produktinformation | `payment/payflow_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa på kundvagn | `payment/payflow_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från | `payment/payflow_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från länder | `payment/payflow_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera SSL-verifiering | `payment/payflow_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Överför kundvagnsartiklar | `payment/payflow_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hoppa över ordergranskningssteget | `payment/paypal_express/skip_order_review_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Överför kundvagnsartiklar | `payment/paypal_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Överför leveransalternativ | `payment/paypal_express/transfer_shipping_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kortkommandoknappsflagga | `paypal/wpp/button_flavor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera PayPal-gästutcheckning | `payment/paypal_express/solution_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kräv kundens faktureringsadress | `payment/paypal_express/require_billing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Registrering av faktureringsavtal | `payment/paypal_express/allow_ba_signup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment/paypal_billing_agreement/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/paypal_billing_agreement/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment/paypal_billing_agreement/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment/paypal_billing_agreement/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från | `payment/paypal_billing_agreement/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från länder | `payment/paypal_billing_agreement/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera SSL-verifiering | `payment/paypal_billing_agreement/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Överför kundvagnsartiklar | `payment/paypal_billing_agreement/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Guiden Tillåt i faktureringsavtal | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera automatisk hämtning | `paypal/fetch_reports/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schema | `paypal/fetch_reports/schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tid på dagen | `paypal/fetch_reports/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal - produktlogotyp | `paypal/style/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sidformat | `paypal/style/page_style` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL för rubrikbild | `paypal/style/paypal_hdrimg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bakgrundsfärg för sidhuvud | `paypal/style/paypal_hdrbackcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kantlinjefärg för sidhuvud | `paypal/style/paypal_hdrbordercolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sidbakgrundsfärg | `paypal/style/paypal_payflowcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera den här lösningen | `payment/paypal_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortera beställ PayPal-kredit | `payment/paypal_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/paypal_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment/paypal_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment/paypal_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa på sidan Produktinformation | `payment/paypal_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Godkännandeperiod (dagar) | `payment/paypal_express/authorization_honor_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Giltig orderperiod (dagar) | `payment/paypal_express/order_valid_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Antal underordnade auktoriseringar | `payment/paypal_express/child_authorization_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa på kundvagn | `payment/paypal_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från | `payment/paypal_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från länder | `payment/paypal_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera SSL-verifiering | `payment/paypal_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payments Pro

| Namn | Konfigurationssökväg | Endast handel? | Krypterad? |
|--------------|--------------|--------------|--------------|
| API-autentiseringsmetoder | `paypal/wpp/api_authentication` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| API använder proxy | `paypal/wpp/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Payments Pro Hosted Solution (Storbritannien)

Dessa alternativ är bara tillgängliga om du väljer Storbritannien som [handelsland](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Namn | Konfigurationssökväg | Endast handel? | Krypterad? |
|--------------|--------------|--------------|--------------|
| Aktivera den här lösningen | `payment/hosted_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/hosted_pro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment/hosted_pro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment/hosted_pro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa Express Checkout i steget Betalningsinformation | `payment/hosted_pro/display_ec` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från | `payment/hosted_pro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från länder | `payment/hosted_pro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera SSL-verifiering | `payment/hosted_pro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payflow Pro

| Namn | Konfigurationssökväg | Endast handel? | Krypterad? |
|--------------|--------------|--------------|--------------|
| Vault aktiverat | `payment/payflowpro_cc_vault/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/payflowpro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valvtitel | `payment/payflowpro_cc_vault/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment/payflowpro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment/payflowpro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåtna kreditkortstyper | `payment/payflowpro/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från | `payment/payflowpro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från länder | `payment/payflowpro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera SSL-verifiering | `payment/payflowpro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kräv CVV-post | `payment/payflowpro/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Avvisa transaktion om: | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS Street matchar inte | `payment/payflowpro/avs_street` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS-postnumret matchar inte | `payment/payflowpro/avs_zip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Internationell AVS-indikator matchar inte | `payment/payflowpro/avs_international` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kortets säkerhetskod matchar inte | `payment/payflowpro/avs_security_code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverantör | `payment/payflowpro/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd proxy | `payment/payflowpro/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/payflow_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment/payflow_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment/payflow_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Partner | `payment/payflow_advanced/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverantör | `payment/payflow_advanced/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Använd proxy | `payment/payflow_advanced/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera den här lösningen | `payment/payflow_advanced/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/payflow_advanced/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment/payflow_advanced/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment/payflow_advanced/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från | `payment/payflow_advanced/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från länder | `payment/payflow_advanced/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera SSL-verifiering | `payment/payflow_advanced/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV-posten är redigerbar | `payment/payflow_advanced/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kräv CVV-post | `payment/payflow_advanced/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bekräftelse på e-post | `payment/payflow_advanced/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Länk till PayPal-betalningsflöde

| Namn | Konfigurationssökväg | Endast handel? | Krypterad? |
|--------------|--------------|--------------|--------------|
| Partner | `payment/payflow_link/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverantör | `payment/payflow_link/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera betalningsflödeslänk | `payment/payflow_link/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera Express Checkout | `payment/payflow_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sortera beställ PayPal-kredit | `payment/payflow_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från | `payment/payflow_link/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från länder | `payment/payflow_link/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera SSL-verifiering | `payment/payflow_link/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV-posten är redigerbar | `payment/payflow_link/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kräv CVV-post | `payment/payflow_link/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bekräftelse på e-post | `payment/payflow_link/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/payflow_link/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment/payflow_link/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment/payflow_link/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Noll delsumma utcheckningsbanor

| Namn | Konfigurationssökväg | Endast handel? | Krypterad? |
|--------------|--------------|--------------|--------------|
| Aktiverad | `payment/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fakturera alla artiklar automatiskt | `payment/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Betalningsvägar för kontanter vid leverans

| Namn | Konfigurationssökväg | Endast handel? | Krypterad? |
|--------------|--------------|--------------|--------------|
| Aktiverad | `payment/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Betalningsvägar för banköverföring

| Namn | Konfigurationssökväg | Endast handel? | Krypterad? |
|--------------|--------------|--------------|--------------|
| Aktiverad | `payment/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Kontrollera och beställa pengar

| Namn | Konfigurationssökväg | Endast handel? | Krypterad? |
|--------------|--------------|--------------|--------------|
| Aktiverad | `payment/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gör kontrollen betalbar till | `payment/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Sökvägar för inköpsorder

| Namn | Konfigurationssökväg | Endast handel? | Krypterad? |
|--------------|--------------|--------------|--------------|
| Aktiverad | `payment/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Internationella sökvägar

>[!INFO]
>
>Vilka banor som är tillgängliga beror på vad du väljer [Handelsland](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Namn | Konfigurationssökväg | Endast handel? | Krypterad? |
|--------------|--------------|--------------|--------------|
| SFTP-autentiseringsuppgifter | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera den här lösningen | `payment/wps_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsinställningar | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Avvisa transaktion om: | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_nz/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_nz/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fakturera alla artiklar automatiskt | `payment_nz/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_nz/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_nz/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_nz/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_nz/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_nz/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_nz/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_nz/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_nz/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_nz/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_nz/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_nz/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_nz/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_nz/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_nz/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_nz/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_nz/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_nz/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_nz/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_nz/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_nz/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_nz/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_nz/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_nz/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gör kontrollen betalbar till | `payment_nz/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skicka kontroll till | `payment_nz/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_nz/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_nz/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_nz/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_nz/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_nz/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_nz/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_nz/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_nz/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_nz/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_nz/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_nz/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment_nz/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_nz/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Godkänd valuta | `payment_nz/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `payment_nz/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortstyper | `payment_nz/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsverifiering | `payment_nz/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_nz/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_nz/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_nz/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_nz/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_nz/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_nz/cybersource/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_nz/cybersource/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_nz/cybersource/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ny orderstatus | `payment_nz/cybersource/order_status` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_nz/cybersource/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_nz/cybersource/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_nz/cybersource/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_nz/cybersource/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minsta ordersumma | `payment_nz/cybersource/min_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximal ordersumma | `payment_nz/cybersource/max_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_nz/cybersource/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_nz/worldpay/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_nz/worldpay/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt redigering av kontaktinformation | `payment_nz/worldpay/fix_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Dölj kontaktinformation | `payment_nz/worldpay/hide_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Signaturfält | `payment_nz/worldpay/signature_fields` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_nz/worldpay/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd för test | `payment_nz/worldpay/test_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_nz/worldpay/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_nz/worldpay/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_nz/worldpay/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_nz/worldpay/cvv_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_nz/worldpay/avs_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_nz/worldpay/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_nz/eway/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Anslutningstyp | `payment_nz/eway/connection_type` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_nz/eway/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_nz/eway/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_nz/eway/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_nz/eway/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_nz/eway/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_nz/eway/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_nz/eway/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Schemalagd hämtning | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_hk/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_hk/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fakturera alla artiklar automatiskt | `payment_hk/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_hk/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_hk/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_hk/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_hk/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_hk/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_hk/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_hk/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_hk/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_hk/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_hk/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_hk/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_hk/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_hk/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_hk/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_hk/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_hk/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_hk/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_hk/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_hk/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_hk/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_hk/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_hk/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_hk/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_hk/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_hk/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_hk/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_hk/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_hk/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_hk/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_hk/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_hk/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_hk/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_hk/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_hk/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment_hk/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_hk/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Godkänd valuta | `payment_hk/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `payment_hk/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortstyper | `payment_hk/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsverifiering | `payment_hk/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_hk/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_hk/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_hk/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_hk/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_hk/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_hk/cybersource/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_hk/cybersource/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_hk/cybersource/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ny orderstatus | `payment_hk/cybersource/order_status` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_hk/cybersource/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_hk/cybersource/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_hk/cybersource/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_hk/cybersource/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minsta ordersumma | `payment_hk/cybersource/min_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximal ordersumma | `payment_hk/cybersource/max_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_hk/cybersource/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_hk/worldpay/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_hk/worldpay/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt redigering av kontaktinformation | `payment_hk/worldpay/fix_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Dölj kontaktinformation | `payment_hk/worldpay/hide_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_hk/worldpay/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd för test | `payment_hk/worldpay/test_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_hk/worldpay/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_hk/worldpay/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_hk/worldpay/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_hk/worldpay/cvv_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_hk/worldpay/avs_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_hk/worldpay/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_hk/eway/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Anslutningstyp | `payment_hk/eway/connection_type` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_hk/eway/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sandlådeläge | `payment_hk/eway/sandbox_flag` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_hk/eway/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_hk/eway/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_hk/eway/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_hk/eway/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_hk/eway/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_hk/eway/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Schemalagd hämtning | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_es/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_es/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fakturera alla artiklar automatiskt | `payment_es/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_es/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_es/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_es/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_es/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_es/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_es/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_es/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_es/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_es/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_es/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_es/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_es/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_es/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_es/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_es/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_es/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_es/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_es/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_es/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_es/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_es/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_es/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_es/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gör kontrollen betalbar till | `payment_es/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_es/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_es/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_es/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_es/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_es/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_es/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_es/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_es/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_es/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_es/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_es/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment_es/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_es/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Godkänd valuta | `payment_es/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `payment_es/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortstyper | `payment_es/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsverifiering | `payment_es/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_es/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_es/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_es/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_es/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_es/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_es/cybersource/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_es/cybersource/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_es/cybersource/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Profil-ID | `payment_es/cybersource/profile_id` | ![Endast handel](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) |
| Ny orderstatus | `payment_es/cybersource/order_status` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_es/cybersource/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_es/cybersource/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_es/cybersource/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_es/cybersource/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minsta ordersumma | `payment_es/cybersource/min_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximal ordersumma | `payment_es/cybersource/max_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_es/cybersource/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_es/worldpay/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_es/worldpay/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Installations-ID | `payment_es/worldpay/installation_id` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Installations-ID för fjärradministratör | `payment_es/worldpay/admin_installation_id` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt redigering av kontaktinformation | `payment_es/worldpay/fix_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Dölj kontaktinformation | `payment_es/worldpay/hide_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Signaturfält | `payment_es/worldpay/signature_fields` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Testläge | `payment_es/worldpay/sandbox_flag` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd för test | `payment_es/worldpay/test_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_es/worldpay/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_es/worldpay/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_es/worldpay/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_es/worldpay/cvv_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_es/worldpay/avs_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_es/worldpay/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_es/eway/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Anslutningstyp | `payment_es/eway/connection_type` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_es/eway/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_es/eway/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_es/eway/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_es/eway/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_es/eway/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_es/eway/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_es/eway/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Schemalagd hämtning | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_it/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_it/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fakturera alla artiklar automatiskt | `payment_it/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_it/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_it/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_it/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_it/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_it/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_it/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_it/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_it/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_it/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_it/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_it/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_it/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_it/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_it/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_it/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_it/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_it/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_it/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_it/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_it/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_it/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_it/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_it/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_it/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_it/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_it/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_it/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_it/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_it/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_it/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_it/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_it/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_it/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_it/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment_it/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_it/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Godkänd valuta | `payment_it/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `payment_it/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortstyper | `payment_it/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsverifiering | `payment_it/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_it/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_it/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_it/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_it/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_it/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_it/cybersource/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_it/cybersource/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_it/cybersource/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ny orderstatus | `payment_it/cybersource/order_status` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_it/cybersource/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_it/cybersource/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_it/cybersource/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_it/cybersource/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minsta ordersumma | `payment_it/cybersource/min_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximal ordersumma | `payment_it/cybersource/max_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_it/cybersource/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_it/worldpay/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_it/worldpay/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt redigering av kontaktinformation | `payment_it/worldpay/fix_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Dölj kontaktinformation | `payment_it/worldpay/hide_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Signaturfält | `payment_it/worldpay/signature_fields` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_it/worldpay/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd för test | `payment_it/worldpay/test_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_it/worldpay/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_it/worldpay/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_it/worldpay/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_it/worldpay/cvv_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_it/worldpay/avs_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_it/worldpay/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_it/eway/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Anslutningstyp | `payment_it/eway/connection_type` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_it/eway/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_it/eway/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_it/eway/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_it/eway/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_it/eway/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_it/eway/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_it/eway/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Schemalagd hämtning | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_fr/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_fr/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fakturera alla artiklar automatiskt | `payment_fr/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_fr/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_fr/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_fr/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_fr/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_fr/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_fr/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_fr/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_fr/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_fr/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_fr/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_fr/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_fr/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_fr/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_fr/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_fr/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_fr/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_fr/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_fr/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_fr/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_fr/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_fr/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_fr/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_fr/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_fr/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_fr/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_fr/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_fr/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_fr/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_fr/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_fr/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_fr/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_fr/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_fr/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_fr/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment_fr/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_fr/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Godkänd valuta | `payment_fr/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `payment_fr/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortstyper | `payment_fr/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsverifiering | `payment_fr/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_fr/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_fr/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_fr/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_fr/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_fr/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_fr/cybersource/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_fr/cybersource/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_fr/cybersource/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ny orderstatus | `payment_fr/cybersource/order_status` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_fr/cybersource/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_fr/cybersource/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_fr/cybersource/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_fr/cybersource/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minsta ordersumma | `payment_fr/cybersource/min_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximal ordersumma | `payment_fr/cybersource/max_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_fr/cybersource/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_fr/worldpay/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_fr/worldpay/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt redigering av kontaktinformation | `payment_fr/worldpay/fix_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Dölj kontaktinformation | `payment_fr/worldpay/hide_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_fr/worldpay/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd för test | `payment_fr/worldpay/test_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_fr/worldpay/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_fr/worldpay/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_fr/worldpay/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_fr/worldpay/cvv_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_fr/worldpay/avs_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_fr/worldpay/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_fr/eway/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Anslutningstyp | `payment_fr/eway/connection_type` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_fr/eway/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_fr/eway/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_fr/eway/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_fr/eway/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_fr/eway/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_fr/eway/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_fr/eway/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Schemalagd hämtning | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_jp/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_jp/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fakturera alla artiklar automatiskt | `payment_jp/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_jp/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_jp/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_jp/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_jp/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_jp/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_jp/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_jp/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_jp/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_jp/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_jp/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_jp/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_jp/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_jp/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_jp/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_jp/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_jp/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_jp/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_jp/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_jp/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_jp/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_jp/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_jp/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_jp/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_jp/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_jp/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_jp/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_jp/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_jp/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_jp/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_jp/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_jp/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_jp/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_jp/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_jp/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment_jp/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_jp/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Godkänd valuta | `payment_jp/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `payment_jp/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortstyper | `payment_jp/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsverifiering | `payment_jp/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_jp/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_jp/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_jp/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_jp/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_jp/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_jp/cybersource/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_jp/cybersource/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_jp/cybersource/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_jp/cybersource/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_jp/cybersource/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_jp/cybersource/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_jp/cybersource/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minsta ordersumma | `payment_jp/cybersource/min_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximal ordersumma | `payment_jp/cybersource/max_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_jp/cybersource/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_jp/worldpay/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_jp/worldpay/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt redigering av kontaktinformation | `payment_jp/worldpay/fix_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Dölj kontaktinformation | `payment_jp/worldpay/hide_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_jp/worldpay/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd för test | `payment_jp/worldpay/test_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_jp/worldpay/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_jp/worldpay/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_jp/worldpay/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_jp/worldpay/cvv_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_jp/worldpay/avs_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_jp/worldpay/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_jp/eway/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Anslutningstyp | `payment_jp/eway/connection_type` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_jp/eway/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_jp/eway/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_jp/eway/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_jp/eway/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_jp/eway/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_jp/eway/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_jp/eway/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Schemalagd hämtning | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsinställningar | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Avvisa transaktion om: | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_au/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_au/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fakturera alla artiklar automatiskt | `payment_au/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_au/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_au/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_au/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_au/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_au/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_au/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_au/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_au/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_au/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_au/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_au/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_au/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_au/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_au/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_au/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_au/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_au/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_au/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_au/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_au/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_au/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_au/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_au/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gör kontrollen betalbar till | `payment_au/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skicka kontroll till | `payment_au/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_au/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_au/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_au/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_au/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_au/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_au/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_au/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_au/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_au/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_au/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_au/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment_au/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_au/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Godkänd valuta | `payment_au/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `payment_au/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortstyper | `payment_au/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsverifiering | `payment_au/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_au/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_au/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_au/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_au/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_au/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_au/cybersource/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_au/cybersource/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_au/cybersource/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Affärs-ID | `payment_au/cybersource/merchant_id` | ![Endast handel](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) |
| Profil-ID | `payment_au/cybersource/profile_id` | ![Endast handel](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) |
| Ny orderstatus | `payment_au/cybersource/order_status` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_au/cybersource/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_au/cybersource/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_au/cybersource/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_au/cybersource/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minsta ordersumma | `payment_au/cybersource/min_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximal ordersumma | `payment_au/cybersource/max_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_au/cybersource/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_au/worldpay/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_au/worldpay/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Installations-ID | `payment_au/worldpay/installation_id` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt redigering av kontaktinformation | `payment_au/worldpay/fix_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Dölj kontaktinformation | `payment_au/worldpay/hide_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Signaturfält | `payment_au/worldpay/signature_fields` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_au/worldpay/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Testläge | `payment_au/worldpay/sandbox_flag` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd för test | `payment_au/worldpay/test_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_au/worldpay/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_au/worldpay/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_au/worldpay/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_au/worldpay/cvv_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_au/worldpay/avs_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_au/worldpay/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_au/eway/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Anslutningstyp | `payment_au/eway/connection_type` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_au/eway/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_au/eway/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_au/eway/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_au/eway/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_au/eway/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_au/eway/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_au/eway/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Schemalagd hämtning | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera den här lösningen | `payment/paypal_payment_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsinställningar | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Avvisa transaktion om: | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsinställningar | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Avvisa transaktion om: | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_ca/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_ca/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fakturera alla artiklar automatiskt | `payment_ca/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_ca/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_ca/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_ca/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_ca/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_ca/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_ca/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_ca/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_ca/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_ca/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_ca/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_ca/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_ca/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_ca/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_ca/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_ca/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_ca/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_ca/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_ca/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_ca/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_ca/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_ca/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_ca/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_ca/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_ca/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_ca/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_ca/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_ca/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_ca/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_ca/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_ca/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_ca/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_ca/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_ca/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_ca/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment_ca/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Godkänd valuta | `payment_ca/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `payment_ca/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortstyper | `payment_ca/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsverifiering | `payment_ca/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_ca/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_ca/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_ca/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_ca/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_ca/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_ca/cybersource/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_ca/cybersource/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_ca/cybersource/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_ca/cybersource/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_ca/cybersource/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_ca/cybersource/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_ca/cybersource/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minsta ordersumma | `payment_ca/cybersource/min_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximal ordersumma | `payment_ca/cybersource/max_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_ca/cybersource/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_ca/worldpay/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_ca/worldpay/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt redigering av kontaktinformation | `payment_ca/worldpay/fix_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Dölj kontaktinformation | `payment_ca/worldpay/hide_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Signaturfält | `payment_ca/worldpay/signature_fields` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_ca/worldpay/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd för test | `payment_ca/worldpay/test_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_ca/worldpay/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_ca/worldpay/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_ca/worldpay/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_ca/worldpay/cvv_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_ca/worldpay/avs_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_ca/worldpay/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_ca/eway/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Anslutningstyp | `payment_ca/eway/connection_type` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_ca/eway/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_ca/eway/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_ca/eway/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_ca/eway/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_ca/eway/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_ca/eway/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_ca/eway/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Schemalagd hämtning | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_other/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_other/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fakturera alla artiklar automatiskt | `payment_other/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_other/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_other/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_other/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_other/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_other/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_other/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_other/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_other/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_other/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_other/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_other/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_other/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_other/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_other/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_other/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_other/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_other/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_other/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_other/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_other/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_other/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_other/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_other/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_other/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_other/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_other/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_other/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_other/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_other/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_other/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_other/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_other/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_other/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_other/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment_other/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Godkänd valuta | `payment_other/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `payment_other/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postkund | `payment_other/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortstyper | `payment_other/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsverifiering | `payment_other/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_other/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_other/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_other/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_other/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_other/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_other/cybersource/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_other/cybersource/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_other/cybersource/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_other/cybersource/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_other/cybersource/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_other/cybersource/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_other/cybersource/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minsta ordersumma | `payment_other/cybersource/min_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximal ordersumma | `payment_other/cybersource/max_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_other/cybersource/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_other/worldpay/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_other/worldpay/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt redigering av kontaktinformation | `payment_other/worldpay/fix_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Dölj kontaktinformation | `payment_other/worldpay/hide_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Signaturfält | `payment_other/worldpay/signature_fields` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_other/worldpay/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd för test | `payment_other/worldpay/test_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_other/worldpay/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_other/worldpay/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_other/worldpay/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_other/worldpay/cvv_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_other/worldpay/avs_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_other/worldpay/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_other/eway/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Anslutningstyp | `payment_other/eway/connection_type` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_other/eway/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_other/eway/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_other/eway/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_other/eway/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_other/eway/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_other/eway/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_other/eway/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Schemalagd hämtning | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_de/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_de/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_de/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_de/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_de/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_de/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_de/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_de/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_de/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_de/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_de/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_de/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_de/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_de/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_de/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_de/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_de/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_de/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_de/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_de/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_de/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_de/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_de/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_de/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_de/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fakturera alla artiklar automatiskt | `payment_de/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_de/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_de/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_de/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_de/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_de/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_de/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_de/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_de/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_de/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_de/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_de/cybersource/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_de/cybersource/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_de/cybersource/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ny orderstatus | `payment_de/cybersource/order_status` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_de/cybersource/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_de/cybersource/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_de/cybersource/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_de/cybersource/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minsta ordersumma | `payment_de/cybersource/min_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximal ordersumma | `payment_de/cybersource/max_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_de/cybersource/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_de/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment_de/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_de/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Godkänd valuta | `payment_de/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `payment_de/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortstyper | `payment_de/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsverifiering | `payment_de/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_de/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_de/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_de/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_de/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_de/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_de/worldpay/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_de/worldpay/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt redigering av kontaktinformation | `payment_de/worldpay/fix_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Dölj kontaktinformation | `payment_de/worldpay/hide_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Signaturfält | `payment_de/worldpay/signature_fields` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Testläge | `payment_de/worldpay/sandbox_flag` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd för test | `payment_de/worldpay/test_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_de/worldpay/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_de/worldpay/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_de/worldpay/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_de/worldpay/cvv_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_de/worldpay/avs_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_de/worldpay/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_de/eway/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Anslutningstyp | `payment_de/eway/connection_type` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_de/eway/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_de/eway/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_de/eway/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_de/eway/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_de/eway/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_de/eway/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_de/eway/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Schemalagd hämtning | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_gb/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_gb/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_gb/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_gb/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gör kontrollen betalbar till | `payment_gb/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_gb/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_gb/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_gb/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_gb/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_gb/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_gb/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_gb/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_gb/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_gb/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_gb/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_gb/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_gb/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_gb/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_gb/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_gb/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_gb/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_gb/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_gb/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_gb/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_gb/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_gb/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fakturera alla artiklar automatiskt | `payment_gb/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_gb/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_gb/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_gb/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_gb/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_gb/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_gb/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_gb/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_gb/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_gb/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_gb/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_gb/cybersource/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_gb/cybersource/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_gb/cybersource/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ny orderstatus | `payment_gb/cybersource/order_status` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_gb/cybersource/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_gb/cybersource/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_gb/cybersource/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_gb/cybersource/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minsta ordersumma | `payment_gb/cybersource/min_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximal ordersumma | `payment_gb/cybersource/max_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_gb/cybersource/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_gb/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment_gb/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_gb/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Godkänd valuta | `payment_gb/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `payment_gb/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortstyper | `payment_gb/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsverifiering | `payment_gb/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_gb/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_gb/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_gb/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_gb/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_gb/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_gb/worldpay/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_gb/worldpay/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| MD5-hemlighet för transaktioner | `payment_gb/worldpay/md5_secret` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt redigering av kontaktinformation | `payment_gb/worldpay/fix_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Dölj kontaktinformation | `payment_gb/worldpay/hide_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Signaturfält | `payment_gb/worldpay/signature_fields` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_gb/worldpay/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd för test | `payment_gb/worldpay/test_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_gb/worldpay/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_gb/worldpay/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_gb/worldpay/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_gb/worldpay/cvv_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_gb/worldpay/avs_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_gb/worldpay/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_gb/eway/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Anslutningstyp | `payment_gb/eway/connection_type` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_gb/eway/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_gb/eway/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_gb/eway/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_gb/eway/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_gb/eway/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_gb/eway/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_gb/eway/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Schemalagd hämtning | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsinställningar | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Avvisa transaktion om: | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera PayPal-kredit | `payment/wps_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsinställningar | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Avvisa transaktion om: | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schemalagd hämtning | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Format för PayPal-reklamsidor | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_us/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_us/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fakturera alla artiklar automatiskt | `payment_us/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_us/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_us/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_us/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_us/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_us/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_us/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_us/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_us/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_us/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_us/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_us/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_us/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_us/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_us/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_us/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instruktioner | `payment_us/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_us/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_us/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_us/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_us/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_us/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_us/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_us/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gör kontrollen betalbar till | `payment_us/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_us/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_us/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_us/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_us/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_us/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_us/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_us/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_us/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_us/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_us/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_us/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalningsåtgärd | `payment_us/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ny orderstatus | `payment_us/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Godkänd valuta | `payment_us/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Felsök | `payment_us/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortstyper | `payment_us/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kreditkortsverifiering | `payment_us/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalning från tillämpliga länder | `payment_us/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stöd från särskilda länder | `payment_us/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta ordersumma | `payment_us/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximal ordersumma | `payment_us/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteringsordning | `payment_us/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktiverad | `payment_us/cybersource/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_us/cybersource/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_us/cybersource/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ny orderstatus | `payment_us/cybersource/order_status` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_us/cybersource/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_us/cybersource/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_us/cybersource/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_us/cybersource/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Minsta ordersumma | `payment_us/cybersource/min_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Maximal ordersumma | `payment_us/cybersource/max_order_total` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_us/cybersource/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_us/worldpay/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_us/worldpay/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Tillåt redigering av kontaktinformation | `payment_us/worldpay/fix_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Dölj kontaktinformation | `payment_us/worldpay/hide_contact` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Signaturfält | `payment_us/worldpay/signature_fields` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_us/worldpay/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd för test | `payment_us/worldpay/test_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_us/worldpay/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_us/worldpay/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_us/worldpay/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_us/worldpay/cvv_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_us/worldpay/avs_fraud_case` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_us/worldpay/sort_order` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Aktiverad | `payment_us/eway/active` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Anslutningstyp | `payment_us/eway/connection_type` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_us/eway/title` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalningsåtgärd | `payment_us/eway/payment_action` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Felsök | `payment_us/eway/debug` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Kreditkortstyper | `payment_us/eway/cctypes` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Betalning från tillämpliga länder | `payment_us/eway/allowspecific` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Stöd från särskilda länder | `payment_us/eway/specificcountry` | ![Endast handel](/help/assets/configuration/cloud-ee.png) |
| Sorteringsordning | `payment_us/eway/sort_order` |  |

{style="table-layout:auto"}
