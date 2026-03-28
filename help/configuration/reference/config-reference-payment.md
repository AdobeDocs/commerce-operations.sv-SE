---
title: Referens för sökvägar för betalningskonfiguration
description: Lär dig mer om sökvägar för betalningskonfiguration och metodvärden i Adobe Commerce Admin. Upptäck konfigurationsalternativ för PayPal, kreditkort och betalgateway.
feature: Configuration, Payments
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '5833'
ht-degree: 0%

---

# Referens för sökvägar för betalningskonfiguration

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Försäljning** > **Betalningsmetoder**.

[`magento app:config:dump`-kommandot ](../cli/export-configuration.md) skriver dessa värden till den delade konfigurationsfilen `app/etc/config.php` som ska finnas i källkontrollen. Om du vill åsidosätta konfigurationsinställningar eller ange känsliga inställningar läser du [Använda miljövariabler för att åsidosätta konfigurationsinställningar](override-config-settings.md#environment-variables). Det här avsnittet innehåller _ALT_ [känsliga och systemspecifika värden](config-reference-sens.md).

Inställningarna ordnas ytterligare efter betalningsmetod.

## PayPal-banor

| Namn | Konfigurationssökväg | Stöd för Commerce-versioner? |
|--------------|--------------|--------------|
| Aktivera den här lösningen | `payment/payflowpro/active` | Alla |
| Aktivera sammanhangsbaserad utcheckning | `payment/paypal_express/in_context` | Alla |
| Aktivera PayPal-kredit | `payment/payflow_express_bml/active` | Alla |
| Aktivera PayPal-kredit | `payment/paypal_express_bml/active` | Alla |
| Visa | `payment/paypal_express_bml/homepage_display` | Alla |
| Position | `payment/paypal_express_bml/homepage_position` | Alla |
| Storlek | `payment/paypal_express_bml/homepage_size` | Alla |
| Visa | `payment/paypal_express_bml/categorypage_display` | Alla |
| Position | `payment/paypal_express_bml/categorypage_position` | Alla |
| Storlek | `payment/paypal_express_bml/categorypage_size` | Alla |
| Visa | `payment/paypal_express_bml/productpage_display` | Alla |
| Position | `payment/paypal_express_bml/productpage_position` | Alla |
| Storlek | `payment/paypal_express_bml/productpage_size` | Alla |
| Visa | `payment/paypal_express_bml/checkout_display` | Alla |
| Position | `payment/paypal_express_bml/checkout_position` | Alla |
| Storlek | `payment/paypal_express_bml/checkout_size` | Alla |
| Visa på sidan Produktinformation | `payment/payflow_express/visible_on_product` | Alla |
| Visa på kundvagn | `payment/payflow_express/visible_on_cart` | Alla |
| Betalning från | `payment/payflow_express/allowspecific` | Alla |
| Betalning från länder | `payment/payflow_express/specificcountry` | Alla |
| Aktivera SSL-verifiering | `payment/payflow_express/verify_peer` | Alla |
| Överför kundvagnsartiklar | `payment/payflow_express/line_items_enabled` | Alla |
| Hoppa över ordergranskningssteget | `payment/paypal_express/skip_order_review_step` | Alla |
| Överför kundvagnsartiklar | `payment/paypal_express/line_items_enabled` | Alla |
| Överför leveransalternativ | `payment/paypal_express/transfer_shipping_options` | Alla |
| Kortkommandoknappsflagga | `paypal/wpp/button_flavor` | Alla |
| Aktivera PayPal-gästutcheckning | `payment/paypal_express/solution_type` | Alla |
| Kräv kundens faktureringsadress | `payment/paypal_express/require_billing_address` | Alla |
| Registrering av faktureringsavtal | `payment/paypal_express/allow_ba_signup` | Alla |
| Aktiverad | `payment/paypal_billing_agreement/active` | Alla |
| Titel | `payment/paypal_billing_agreement/title` | Alla |
| Sorteringsordning | `payment/paypal_billing_agreement/sort_order` | Alla |
| Betalningsåtgärd | `payment/paypal_billing_agreement/payment_action` | Alla |
| Betalning från | `payment/paypal_billing_agreement/allowspecific` | Alla |
| Betalning från länder | `payment/paypal_billing_agreement/specificcountry` | Alla |
| Aktivera SSL-verifiering | `payment/paypal_billing_agreement/verify_peer` | Alla |
| Överför kundvagnsartiklar | `payment/paypal_billing_agreement/line_items_enabled` | Alla |
| Guiden Tillåt i faktureringsavtal | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | Alla |
| Aktivera automatisk hämtning | `paypal/fetch_reports/active` | Alla |
| Schema | `paypal/fetch_reports/schedule` | Alla |
| Tid på dagen | `paypal/fetch_reports/time` | Alla |
| PayPal - produktlogotyp | `paypal/style/logo` | Alla |
| Sidformat | `paypal/style/page_style` | Alla |
| URL för rubrikbild | `paypal/style/paypal_hdrimg` | Alla |
| Bakgrundsfärg för huvud | `paypal/style/paypal_hdrbackcolor` | Alla |
| Kantfärg för sidhuvud | `paypal/style/paypal_hdrbordercolor` | Alla |
| Sidbakgrundsfärg | `paypal/style/paypal_payflowcolor` | Alla |
| Aktivera den här lösningen | `payment/paypal_express/active` | Alla |
| Sortera beställ PayPal-kredit | `payment/paypal_express_bml/sort_order` | Alla |
| Titel | `payment/paypal_express/title` | Alla |
| Sorteringsordning | `payment/paypal_express/sort_order` | Alla |
| Betalningsåtgärd | `payment/paypal_express/payment_action` | Alla |
| Visa på sidan Produktinformation | `payment/paypal_express/visible_on_product` | Alla |
| Godkännandeperiod (dagar) | `payment/paypal_express/authorization_hoAllr_period` | Alla |
| Giltig orderperiod (dagar) | `payment/paypal_express/order_valid_period` | Alla |
| Antal underordnade auktoriseringar | `payment/paypal_express/child_authorization_number` | Alla |
| Visa på kundvagn | `payment/paypal_express/visible_on_cart` | Alla |
| Antal underordnade auktoriseringar | `payment/paypal_express/child_authorization_number` | Alla |
| Betalning från | `payment/paypal_express/allowspecific` | Alla |
| Antal underordnade auktoriseringar | `payment/paypal_express/child_authorization_number` | Alla |
| Betalning från länder | `payment/paypal_express/specificcountry` | Alla |
| Antal underordnade auktoriseringar | `payment/paypal_express/child_authorization_number` | Alla |
| Aktivera SSL-verifiering | `payment/paypal_express/verify_peer` | Alla |
| Antal underordnade auktoriseringar | `payment/paypal_express/child_authorization_number` | Alla |
| Schemalagd hämtning | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |

{style="table-layout:auto"}

## PayPal Payments Pro

| Namn | Konfigurationssökväg | Stöd för Commerce-versioner? |
|--------------|--------------|--------------|
| API-autentiseringsmetoder | `paypal/wpp/api_authentication` | Alla |
| API använder proxy | `paypal/wpp/use_proxy` | Alla |
| Schemalagd hämtning | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alla |
| Schemalagd hämtning | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alla |

{style="table-layout:auto"}

## Payments Pro Hosted Solution (Storbritannien)

De här alternativen är bara tillgängliga om du har valt Storbritannien som [handelsland](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Namn | Konfigurationssökväg | Stöd för Commerce-versioner? |
|--------------|--------------|--------------|
| Aktivera den här lösningen | `payment/hosted_pro/active` | Alla |
| Titel | `payment/hosted_pro/title` | Alla |
| Sorteringsordning | `payment/hosted_pro/sort_order` | Alla |
| Betalningsåtgärd | `payment/hosted_pro/payment_action` | Alla |
| Visa Express Checkout i steget Betalningsinformation | `payment/hosted_pro/display_ec` | Alla |
| Betalning från | `payment/hosted_pro/allowspecific` | Alla |
| Betalning från länder | `payment/hosted_pro/specificcountry` | Alla |
| Aktivera SSL-verifiering | `payment/hosted_pro/verify_peer` | Alla |

{style="table-layout:auto"}

## PayPal Payflow Pro

| Namn | Konfigurationssökväg | Stöd för Commerce-versioner? |
|--------------|--------------|--------------|
| Valv aktiverat | `payment/payflowpro_cc_vault/active` | Alla |
| Titel | `payment/payflowpro/title` | Alla |
| Valvtitel | `payment/payflowpro_cc_vault/title` | Alla |
| Sorteringsordning | `payment/payflowpro/sort_order` | Alla |
| Betalningsåtgärd | `payment/payflowpro/payment_action` | Alla |
| Tillåtna kreditkortstyper | `payment/payflowpro/cctypes` | Alla |
| Betalning från | `payment/payflowpro/allowspecific` | Alla |
| Betalning från länder | `payment/payflowpro/specificcountry` | Alla |
| Aktivera SSL-verifiering | `payment/payflowpro/verify_peer` | Alla |
| Kräv CVV-post | `payment/payflowpro/useccv` | Alla |
| Avvisa transaktion om: | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alla |
| AVS Street Does Allch Match | `payment/payflowpro/avs_street` | Alla |
| AVS Zip Matchar alltid | `payment/payflowpro/avs_zip` | Alla |
| Internationell AVS-indikator matchar alltid | `payment/payflowpro/avs_international` | Alla |
| Kortets säkerhetskod matchar alltid | `payment/payflowpro/avs_security_code` | Alla |
| Leverantör | `payment/payflowpro/vendor` | Alla |
| Använd proxy | `payment/payflowpro/use_proxy` | Alla |
| Titel | `payment/payflow_express/title` | Alla |
| Sorteringsordning | `payment/payflow_express/sort_order` | Alla |
| Betalningsåtgärd | `payment/payflow_express/payment_action` | Alla |
| Schemalagd hämtning | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Alla |
| Partner | `payment/payflow_advanced/partner` | Alla |
| Leverantör | `payment/payflow_advanced/vendor` | Alla |
| Använd proxy | `payment/payflow_advanced/use_proxy` | Alla |
| Aktivera den här lösningen | `payment/payflow_advanced/active` | Alla |
| Titel | `payment/payflow_advanced/title` | Alla |
| Sorteringsordning | `payment/payflow_advanced/sort_order` | Alla |
| Betalningsåtgärd | `payment/payflow_advanced/payment_action` | Alla |
| Betalning från | `payment/payflow_advanced/allowspecific` | Alla |
| Betalning från länder | `payment/payflow_advanced/specificcountry` | Alla |
| Aktivera SSL-verifiering | `payment/payflow_advanced/verify_peer` | Alla |
| CVV-posten är redigerbar | `payment/payflow_advanced/csc_editable` | Alla |
| Kräv CVV-post | `payment/payflow_advanced/csc_required` | Alla |
| Bekräftelse på e-post | `payment/payflow_advanced/email_confirmation` | Alla |

{style="table-layout:auto"}

## Länk till PayPal-betalningsflöde

| Namn | Konfigurationssökväg | Stöd för Commerce-versioner? |
|--------------|--------------|--------------|
| Partner | `payment/payflow_link/partner` | Alla |
| Leverantör | `payment/payflow_link/vendor` | Alla |
| Aktivera betalningsflödeslänk | `payment/payflow_link/active` | Alla |
| Aktivera Express Checkout | `payment/payflow_express/active` | Alla |
| Sortera beställ PayPal-kredit | `payment/payflow_express_bml/sort_order` | Alla |
| Betalning från | `payment/payflow_link/allowspecific` | Alla |
| Betalning från länder | `payment/payflow_link/specificcountry` | Alla |
| Aktivera SSL-verifiering | `payment/payflow_link/verify_peer` | Alla |
| CVV-posten är redigerbar | `payment/payflow_link/csc_editable` | Alla |
| Kräv CVV-post | `payment/payflow_link/csc_required` | Alla |
| Bekräftelse på e-post | `payment/payflow_link/email_confirmation` | Alla |
| Schemalagd hämtning | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Alla |
| Titel | `payment/payflow_link/title` | Alla |
| Sorteringsordning | `payment/payflow_link/sort_order` | Alla |
| Betalningsåtgärd | `payment/payflow_link/payment_action` | Alla |

{style="table-layout:auto"}

## Noll delsumma utcheckningsbanor

| Namn | Konfigurationssökväg | Stöd för Commerce-versioner? |
|--------------|--------------|--------------|
| Aktiverad | `payment/free/active` | Alla |
| Titel | `payment/free/title` | Alla |
| Ny orderstatus | `payment/free/order_status` | Alla |
| Fakturera alla artiklar automatiskt | `payment/free/payment_action` | Alla |
| Betalning från tillämpliga länder | `payment/free/allowspecific` | Alla |
| Stöd från särskilda länder | `payment/free/specificcountry` | Alla |
| Sorteringsordning | `payment/free/sort_order` | Alla |

{style="table-layout:auto"}

## Betalningsvägar för kontanter

| Namn | Konfigurationssökväg | Stöd för Commerce-versioner? |
|--------------|--------------|--------------|
| Aktiverad | `payment/cashondelivery/active` | Alla |
| Titel | `payment/cashondelivery/title` | Alla |
| Ny orderstatus | `payment/cashondelivery/order_status` | Alla |
| Betalning från tillämpliga länder | `payment/cashondelivery/allowspecific` | Alla |
| Stöd från särskilda länder | `payment/cashondelivery/specificcountry` | Alla |
| Instruktioner | `payment/cashondelivery/instructions` | Alla |
| Minsta ordersumma | `payment/cashondelivery/min_order_total` | Alla |
| Maximal ordersumma | `payment/cashondelivery/max_order_total` | Alla |
| Sorteringsordning | `payment/cashondelivery/sort_order` | Alla |

{style="table-layout:auto"}

## Betalningsvägar för banköverföring

| Namn | Konfigurationssökväg | Stöd för Commerce-versioner? |
|--------------|--------------|--------------|
| Aktiverad | `payment/banktransfer/active` | Alla |
| Titel | `payment/banktransfer/title` | Alla |
| Ny orderstatus | `payment/banktransfer/order_status` | Alla |
| Betalning från tillämpliga länder | `payment/banktransfer/allowspecific` | Alla |
| Stöd från särskilda länder | `payment/banktransfer/specificcountry` | Alla |
| Instruktioner | `payment/banktransfer/instructions` | Alla |
| Minsta ordersumma | `payment/banktransfer/min_order_total` | Alla |
| Maximal ordersumma | `payment/banktransfer/max_order_total` | Alla |
| Sorteringsordning | `payment/banktransfer/sort_order` | Alla |

{style="table-layout:auto"}

## Kontrollera och beställa pengar

| Namn | Konfigurationssökväg | Stöd för Commerce-versioner? |
|--------------|--------------|--------------|
| Aktiverad | `payment/checkmo/active` | Alla |
| Titel | `payment/checkmo/title` | Alla |
| Ny orderstatus | `payment/checkmo/order_status` | Alla |
| Betalning från tillämpliga länder | `payment/checkmo/allowspecific` | Alla |
| Stöd från särskilda länder | `payment/checkmo/specificcountry` | Alla |
| Gör kontrollen betalbar till | `payment/checkmo/payable_to` | Alla |
| Minsta ordersumma | `payment/checkmo/min_order_total` | Alla |
| Maximal ordersumma | `payment/checkmo/max_order_total` | Alla |
| Sorteringsordning | `payment/checkmo/sort_order` | Alla |

{style="table-layout:auto"}

## Sökvägar för inköpsorder

| Namn | Konfigurationssökväg | Stöd för Commerce-versioner? |
|--------------|--------------|--------------|
| Aktiverad | `payment/purchaseorder/active` | Alla |
| Titel | `payment/purchaseorder/title` | Alla |
| Ny orderstatus | `payment/purchaseorder/order_status` | Alla |
| Betalning från tillämpliga länder | `payment/purchaseorder/allowspecific` | Alla |
| Stöd från särskilda länder | `payment/purchaseorder/specificcountry` | Alla |
| Minsta ordersumma | `payment/purchaseorder/min_order_total` | Alla |
| Maximal ordersumma | `payment/purchaseorder/max_order_total` | Alla |
| Sorteringsordning | `payment/purchaseorder/sort_order` | Alla |

{style="table-layout:auto"}

## Internationella sökvägar

>[!INFO]
>
>Vilka sökvägar som är tillgängliga beror på ditt val av [handelsland](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Namn | Konfigurationssökväg | Stöd för Commerce-versioner? |
|--------------|--------------|--------------|
| SFTP-autentiseringsuppgifter | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | Alla |
| Schemalagd hämtning | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Aktivera den här lösningen | `payment/wps_express/active` | Alla |
| Schemalagd hämtning | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Kreditkortsinställningar | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | Alla |
| Avvisa transaktion om: | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alla |
| Schemalagd hämtning | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alla |
| Aktiverad | `payment_nz/free/active` | Alla |
| Titel | `payment_nz/free/title` | Alla |
| Ny orderstatus | `payment_nz/free/order_status` | Alla |
| Fakturera alla artiklar automatiskt | `payment_nz/free/payment_action` | Alla |
| Betalning från tillämpliga länder | `payment_nz/free/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_nz/free/specificcountry` | Alla |
| Sorteringsordning | `payment_nz/free/sort_order` | Alla |
| Aktiverad | `payment_nz/cashondelivery/active` | Alla |
| Titel | `payment_nz/cashondelivery/title` | Alla |
| Ny orderstatus | `payment_nz/cashondelivery/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_nz/cashondelivery/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_nz/cashondelivery/specificcountry` | Alla |
| Instruktioner | `payment_nz/cashondelivery/instructions` | Alla |
| Minsta ordersumma | `payment_nz/cashondelivery/min_order_total` | Alla |
| Maximal ordersumma | `payment_nz/cashondelivery/max_order_total` | Alla |
| Sorteringsordning | `payment_nz/cashondelivery/sort_order` | Alla |
| Aktiverad | `payment_nz/banktransfer/active` | Alla |
| Titel | `payment_nz/banktransfer/title` | Alla |
| Ny orderstatus | `payment_nz/banktransfer/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_nz/banktransfer/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_nz/banktransfer/specificcountry` | Alla |
| Instruktioner | `payment_nz/banktransfer/instructions` | Alla |
| Minsta ordersumma | `payment_nz/banktransfer/min_order_total` | Alla |
| Maximal ordersumma | `payment_nz/banktransfer/max_order_total` | Alla |
| Sorteringsordning | `payment_nz/banktransfer/sort_order` | Alla |
| Aktiverad | `payment_nz/checkmo/active` | Alla |
| Titel | `payment_nz/checkmo/title` | Alla |
| Ny orderstatus | `payment_nz/checkmo/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_nz/checkmo/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_nz/checkmo/specificcountry` | Alla |
| Gör kontrollen betalbar till | `payment_nz/checkmo/payable_to` | Alla |
| Skicka kontroll till | `payment_nz/checkmo/mailing_address` | Alla |
| Minsta ordersumma | `payment_nz/checkmo/min_order_total` | Alla |
| Maximal ordersumma | `payment_nz/checkmo/max_order_total` | Alla |
| Sorteringsordning | `payment_nz/checkmo/sort_order` | Alla |
| Aktiverad | `payment_nz/purchaseorder/active` | Alla |
| Titel | `payment_nz/purchaseorder/title` | Alla |
| Ny orderstatus | `payment_nz/purchaseorder/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_nz/purchaseorder/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_nz/purchaseorder/specificcountry` | Alla |
| Minsta ordersumma | `payment_nz/purchaseorder/min_order_total` | Alla |
| Maximal ordersumma | `payment_nz/purchaseorder/max_order_total` | Alla |
| Sorteringsordning | `payment_nz/purchaseorder/sort_order` | Alla |
| Aktiverad | `payment_nz/authorizenet_directpost/active` | Alla |
| Betalningsåtgärd | `payment_nz/authorizenet_directpost/payment_action` | Alla |
| Titel | `payment_nz/authorizenet_directpost/title` | Alla |
| Ny orderstatus | `payment_nz/authorizenet_directpost/order_status` | Alla |
| Godkänd valuta | `payment_nz/authorizenet_directpost/currency` | Alla |
| Felsök | `payment_nz/authorizenet_directpost/debug` | Alla |
| Kreditkortstyper | `payment_nz/authorizenet_directpost/cctypes` | Alla |
| Kreditkortsverifiering | `payment_nz/authorizenet_directpost/useccv` | Alla |
| Betalning från tillämpliga länder | `payment_nz/authorizenet_directpost/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_nz/authorizenet_directpost/specificcountry` | Alla |
| Minsta ordersumma | `payment_nz/authorizenet_directpost/min_order_total` | Alla |
| Maximal ordersumma | `payment_nz/authorizenet_directpost/max_order_total` | Alla |
| Sorteringsordning | `payment_nz/authorizenet_directpost/sort_order` | Alla |
| Aktiverad | `payment_nz/cybersource/active` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_nz/cybersource/payment_action` | Endast Commerce Enterprise |
| Titel | `payment_nz/cybersource/title` | Endast Commerce Enterprise |
| Ny orderstatus | `payment_nz/cybersource/order_status` | Endast Commerce Enterprise |
| Felsök | `payment_nz/cybersource/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_nz/cybersource/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_nz/cybersource/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_nz/cybersource/specificcountry` | Endast Commerce Enterprise |
| Minsta ordersumma | `payment_nz/cybersource/min_order_total` | Endast Commerce Enterprise |
| Maximal ordersumma | `payment_nz/cybersource/max_order_total` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_nz/cybersource/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_nz/worldpay/active` | Endast Commerce Enterprise |
| Titel | `payment_nz/worldpay/title` | Endast Commerce Enterprise |
| Tillåt redigering av kontaktinformation | `payment_nz/worldpay/fix_contact` | Endast Commerce Enterprise |
| Dölj kontaktinformation | `payment_nz/worldpay/hide_contact` | Endast Commerce Enterprise |
| Signaturfält | `payment_nz/worldpay/signature_fields` | Endast Commerce Enterprise |
| Felsök | `payment_nz/worldpay/debug` | Endast Commerce Enterprise |
| Betalningsåtgärd för test | `payment_nz/worldpay/test_action` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_nz/worldpay/payment_action` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_nz/worldpay/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_nz/worldpay/specificcountry` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_nz/worldpay/cvv_fraud_case` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_nz/worldpay/avs_fraud_case` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_nz/worldpay/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_nz/eway/active` | Endast Commerce Enterprise |
| Anslutningstyp | `payment_nz/eway/connection_type` | Endast Commerce Enterprise |
| Titel | `payment_nz/eway/title` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_nz/eway/payment_action` | Endast Commerce Enterprise |
| Felsök | `payment_nz/eway/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_nz/eway/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_nz/eway/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_nz/eway/specificcountry` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_nz/eway/sort_order` | Endast Commerce Enterprise |
| Schemalagd hämtning | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Schemalagd hämtning | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alla |
| Schemalagd hämtning | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Aktiverad | `payment_hk/free/active` | Alla |
| Titel | `payment_hk/free/title` | Alla |
| Ny orderstatus | `payment_hk/free/order_status` | Alla |
| Fakturera alla artiklar automatiskt | `payment_hk/free/payment_action` | Alla |
| Betalning från tillämpliga länder | `payment_hk/free/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_hk/free/specificcountry` | Alla |
| Sorteringsordning | `payment_hk/free/sort_order` | Alla |
| Aktiverad | `payment_hk/cashondelivery/active` | Alla |
| Titel | `payment_hk/cashondelivery/title` | Alla |
| Ny orderstatus | `payment_hk/cashondelivery/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_hk/cashondelivery/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_hk/cashondelivery/specificcountry` | Alla |
| Instruktioner | `payment_hk/cashondelivery/instructions` | Alla |
| Minsta ordersumma | `payment_hk/cashondelivery/min_order_total` | Alla |
| Maximal ordersumma | `payment_hk/cashondelivery/max_order_total` | Alla |
| Sorteringsordning | `payment_hk/cashondelivery/sort_order` | Alla |
| Aktiverad | `payment_hk/banktransfer/active` | Alla |
| Titel | `payment_hk/banktransfer/title` | Alla |
| Ny orderstatus | `payment_hk/banktransfer/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_hk/banktransfer/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_hk/banktransfer/specificcountry` | Alla |
| Instruktioner | `payment_hk/banktransfer/instructions` | Alla |
| Minsta ordersumma | `payment_hk/banktransfer/min_order_total` | Alla |
| Maximal ordersumma | `payment_hk/banktransfer/max_order_total` | Alla |
| Sorteringsordning | `payment_hk/banktransfer/sort_order` | Alla |
| Aktiverad | `payment_hk/checkmo/active` | Alla |
| Titel | `payment_hk/checkmo/title` | Alla |
| Ny orderstatus | `payment_hk/checkmo/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_hk/checkmo/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_hk/checkmo/specificcountry` | Alla |
| Minsta ordersumma | `payment_hk/checkmo/min_order_total` | Alla |
| Maximal ordersumma | `payment_hk/checkmo/max_order_total` | Alla |
| Sorteringsordning | `payment_hk/checkmo/sort_order` | Alla |
| Aktiverad | `payment_hk/purchaseorder/active` | Alla |
| Titel | `payment_hk/purchaseorder/title` | Alla |
| Ny orderstatus | `payment_hk/purchaseorder/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_hk/purchaseorder/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_hk/purchaseorder/specificcountry` | Alla |
| Minsta ordersumma | `payment_hk/purchaseorder/min_order_total` | Alla |
| Maximal ordersumma | `payment_hk/purchaseorder/max_order_total` | Alla |
| Sorteringsordning | `payment_hk/purchaseorder/sort_order` | Alla |
| Aktiverad | `payment_hk/authorizenet_directpost/active` | Alla |
| Betalningsåtgärd | `payment_hk/authorizenet_directpost/payment_action` | Alla |
| Titel | `payment_hk/authorizenet_directpost/title` | Alla |
| Ny orderstatus | `payment_hk/authorizenet_directpost/order_status` | Alla |
| Godkänd valuta | `payment_hk/authorizenet_directpost/currency` | Alla |
| Felsök | `payment_hk/authorizenet_directpost/debug` | Alla |
| Kreditkortstyper | `payment_hk/authorizenet_directpost/cctypes` | Alla |
| Kreditkortsverifiering | `payment_hk/authorizenet_directpost/useccv` | Alla |
| Betalning från tillämpliga länder | `payment_hk/authorizenet_directpost/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_hk/authorizenet_directpost/specificcountry` | Alla |
| Minsta ordersumma | `payment_hk/authorizenet_directpost/min_order_total` | Alla |
| Maximal ordersumma | `payment_hk/authorizenet_directpost/max_order_total` | Alla |
| Sorteringsordning | `payment_hk/authorizenet_directpost/sort_order` | Alla |
| Aktiverad | `payment_hk/cybersource/active` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_hk/cybersource/payment_action` | Endast Commerce Enterprise |
| Titel | `payment_hk/cybersource/title` | Endast Commerce Enterprise |
| Ny orderstatus | `payment_hk/cybersource/order_status` | Endast Commerce Enterprise |
| Felsök | `payment_hk/cybersource/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_hk/cybersource/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_hk/cybersource/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_hk/cybersource/specificcountry` | Endast Commerce Enterprise |
| Minsta ordersumma | `payment_hk/cybersource/min_order_total` | Endast Commerce Enterprise |
| Maximal ordersumma | `payment_hk/cybersource/max_order_total` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_hk/cybersource/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_hk/worldpay/active` | Endast Commerce Enterprise |
| Titel | `payment_hk/worldpay/title` | Endast Commerce Enterprise |
| Tillåt redigering av kontaktinformation | `payment_hk/worldpay/fix_contact` | Endast Commerce Enterprise |
| Dölj kontaktinformation | `payment_hk/worldpay/hide_contact` | Endast Commerce Enterprise |
| Felsök | `payment_hk/worldpay/debug` | Endast Commerce Enterprise |
| Betalningsåtgärd för test | `payment_hk/worldpay/test_action` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_hk/worldpay/payment_action` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_hk/worldpay/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_hk/worldpay/specificcountry` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_hk/worldpay/cvv_fraud_case` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_hk/worldpay/avs_fraud_case` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_hk/worldpay/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_hk/eway/active` | Endast Commerce Enterprise |
| Anslutningstyp | `payment_hk/eway/connection_type` | Endast Commerce Enterprise |
| Titel | `payment_hk/eway/title` | Endast Commerce Enterprise |
| Sandlådeläge | `payment_hk/eway/sandbox_flag` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_hk/eway/payment_action` | Endast Commerce Enterprise |
| Felsök | `payment_hk/eway/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_hk/eway/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_hk/eway/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_hk/eway/specificcountry` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_hk/eway/sort_order` | Endast Commerce Enterprise |
| Schemalagd hämtning | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Schemalagd hämtning | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alla |
| Schemalagd hämtning | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Aktiverad | `payment_es/free/active` | Alla |
| Titel | `payment_es/free/title` | Alla |
| Ny orderstatus | `payment_es/free/order_status` | Alla |
| Fakturera alla artiklar automatiskt | `payment_es/free/payment_action` | Alla |
| Betalning från tillämpliga länder | `payment_es/free/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_es/free/specificcountry` | Alla |
| Sorteringsordning | `payment_es/free/sort_order` | Alla |
| Aktiverad | `payment_es/cashondelivery/active` | Alla |
| Titel | `payment_es/cashondelivery/title` | Alla |
| Ny orderstatus | `payment_es/cashondelivery/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_es/cashondelivery/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_es/cashondelivery/specificcountry` | Alla |
| Instruktioner | `payment_es/cashondelivery/instructions` | Alla |
| Minsta ordersumma | `payment_es/cashondelivery/min_order_total` | Alla |
| Maximal ordersumma | `payment_es/cashondelivery/max_order_total` | Alla |
| Sorteringsordning | `payment_es/cashondelivery/sort_order` | Alla |
| Aktiverad | `payment_es/banktransfer/active` | Alla |
| Titel | `payment_es/banktransfer/title` | Alla |
| Ny orderstatus | `payment_es/banktransfer/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_es/banktransfer/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_es/banktransfer/specificcountry` | Alla |
| Instruktioner | `payment_es/banktransfer/instructions` | Alla |
| Minsta ordersumma | `payment_es/banktransfer/min_order_total` | Alla |
| Maximal ordersumma | `payment_es/banktransfer/max_order_total` | Alla |
| Sorteringsordning | `payment_es/banktransfer/sort_order` | Alla |
| Aktiverad | `payment_es/checkmo/active` | Alla |
| Titel | `payment_es/checkmo/title` | Alla |
| Ny orderstatus | `payment_es/checkmo/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_es/checkmo/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_es/checkmo/specificcountry` | Alla |
| Gör kontrollen betalbar till | `payment_es/checkmo/payable_to` | Alla |
| Minsta ordersumma | `payment_es/checkmo/min_order_total` | Alla |
| Maximal ordersumma | `payment_es/checkmo/max_order_total` | Alla |
| Sorteringsordning | `payment_es/checkmo/sort_order` | Alla |
| Aktiverad | `payment_es/purchaseorder/active` | Alla |
| Titel | `payment_es/purchaseorder/title` | Alla |
| Ny orderstatus | `payment_es/purchaseorder/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_es/purchaseorder/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_es/purchaseorder/specificcountry` | Alla |
| Minsta ordersumma | `payment_es/purchaseorder/min_order_total` | Alla |
| Maximal ordersumma | `payment_es/purchaseorder/max_order_total` | Alla |
| Sorteringsordning | `payment_es/purchaseorder/sort_order` | Alla |
| Aktiverad | `payment_es/authorizenet_directpost/active` | Alla |
| Betalningsåtgärd | `payment_es/authorizenet_directpost/payment_action` | Alla |
| Titel | `payment_es/authorizenet_directpost/title` | Alla |
| Ny orderstatus | `payment_es/authorizenet_directpost/order_status` | Alla |
| Godkänd valuta | `payment_es/authorizenet_directpost/currency` | Alla |
| Felsök | `payment_es/authorizenet_directpost/debug` | Alla |
| Kreditkortstyper | `payment_es/authorizenet_directpost/cctypes` | Alla |
| Kreditkortsverifiering | `payment_es/authorizenet_directpost/useccv` | Alla |
| Betalning från tillämpliga länder | `payment_es/authorizenet_directpost/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_es/authorizenet_directpost/specificcountry` | Alla |
| Minsta ordersumma | `payment_es/authorizenet_directpost/min_order_total` | Alla |
| Maximal ordersumma | `payment_es/authorizenet_directpost/max_order_total` | Alla |
| Sorteringsordning | `payment_es/authorizenet_directpost/sort_order` | Alla |
| Aktiverad | `payment_es/cybersource/active` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_es/cybersource/payment_action` | Endast Commerce Enterprise |
| Titel | `payment_es/cybersource/title` | Endast Commerce Enterprise |
| Profil-ID | `payment_es/cybersource/profile_id` | Endast Commerce Enterprise\| ![Krypterad](/help/assets/configuration/cloud-enc.png) |
| Ny orderstatus | `payment_es/cybersource/order_status` | Endast Commerce Enterprise |
| Felsök | `payment_es/cybersource/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_es/cybersource/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_es/cybersource/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_es/cybersource/specificcountry` | Endast Commerce Enterprise |
| Minsta ordersumma | `payment_es/cybersource/min_order_total` | Endast Commerce Enterprise |
| Maximal ordersumma | `payment_es/cybersource/max_order_total` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_es/cybersource/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_es/worldpay/active` | Endast Commerce Enterprise |
| Titel | `payment_es/worldpay/title` | Endast Commerce Enterprise |
| Installations-ID | `payment_es/worldpay/installation_id` | Endast Commerce Enterprise |
| Installations-ID för fjärradministratör | `payment_es/worldpay/admin_installation_id` | Endast Commerce Enterprise |
| Tillåt redigering av kontaktinformation | `payment_es/worldpay/fix_contact` | Endast Commerce Enterprise |
| Dölj kontaktinformation | `payment_es/worldpay/hide_contact` | Endast Commerce Enterprise |
| Signaturfält | `payment_es/worldpay/signature_fields` | Endast Commerce Enterprise |
| Testläge | `payment_es/worldpay/sandbox_flag` | Endast Commerce Enterprise |
| Betalningsåtgärd för test | `payment_es/worldpay/test_action` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_es/worldpay/payment_action` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_es/worldpay/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_es/worldpay/specificcountry` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_es/worldpay/cvv_fraud_case` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_es/worldpay/avs_fraud_case` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_es/worldpay/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_es/eway/active` | Endast Commerce Enterprise |
| Anslutningstyp | `payment_es/eway/connection_type` | Endast Commerce Enterprise |
| Titel | `payment_es/eway/title` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_es/eway/payment_action` | Endast Commerce Enterprise |
| Felsök | `payment_es/eway/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_es/eway/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_es/eway/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_es/eway/specificcountry` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_es/eway/sort_order` | Endast Commerce Enterprise |
| Schemalagd hämtning | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Schemalagd hämtning | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alla |
| Schemalagd hämtning | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Aktiverad | `payment_it/free/active` | Alla |
| Titel | `payment_it/free/title` | Alla |
| Ny orderstatus | `payment_it/free/order_status` | Alla |
| Fakturera alla artiklar automatiskt | `payment_it/free/payment_action` | Alla |
| Betalning från tillämpliga länder | `payment_it/free/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_it/free/specificcountry` | Alla |
| Sorteringsordning | `payment_it/free/sort_order` | Alla |
| Aktiverad | `payment_it/cashondelivery/active` | Alla |
| Titel | `payment_it/cashondelivery/title` | Alla |
| Ny orderstatus | `payment_it/cashondelivery/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_it/cashondelivery/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_it/cashondelivery/specificcountry` | Alla |
| Instruktioner | `payment_it/cashondelivery/instructions` | Alla |
| Minsta ordersumma | `payment_it/cashondelivery/min_order_total` | Alla |
| Maximal ordersumma | `payment_it/cashondelivery/max_order_total` | Alla |
| Sorteringsordning | `payment_it/cashondelivery/sort_order` | Alla |
| Aktiverad | `payment_it/banktransfer/active` | Alla |
| Titel | `payment_it/banktransfer/title` | Alla |
| Ny orderstatus | `payment_it/banktransfer/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_it/banktransfer/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_it/banktransfer/specificcountry` | Alla |
| Instruktioner | `payment_it/banktransfer/instructions` | Alla |
| Minsta ordersumma | `payment_it/banktransfer/min_order_total` | Alla |
| Maximal ordersumma | `payment_it/banktransfer/max_order_total` | Alla |
| Sorteringsordning | `payment_it/banktransfer/sort_order` | Alla |
| Aktiverad | `payment_it/checkmo/active` | Alla |
| Titel | `payment_it/checkmo/title` | Alla |
| Ny orderstatus | `payment_it/checkmo/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_it/checkmo/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_it/checkmo/specificcountry` | Alla |
| Minsta ordersumma | `payment_it/checkmo/min_order_total` | Alla |
| Maximal ordersumma | `payment_it/checkmo/max_order_total` | Alla |
| Sorteringsordning | `payment_it/checkmo/sort_order` | Alla |
| Aktiverad | `payment_it/purchaseorder/active` | Alla |
| Titel | `payment_it/purchaseorder/title` | Alla |
| Ny orderstatus | `payment_it/purchaseorder/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_it/purchaseorder/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_it/purchaseorder/specificcountry` | Alla |
| Minsta ordersumma | `payment_it/purchaseorder/min_order_total` | Alla |
| Maximal ordersumma | `payment_it/purchaseorder/max_order_total` | Alla |
| Sorteringsordning | `payment_it/purchaseorder/sort_order` | Alla |
| Aktiverad | `payment_it/authorizenet_directpost/active` | Alla |
| Betalningsåtgärd | `payment_it/authorizenet_directpost/payment_action` | Alla |
| Titel | `payment_it/authorizenet_directpost/title` | Alla |
| Ny orderstatus | `payment_it/authorizenet_directpost/order_status` | Alla |
| Godkänd valuta | `payment_it/authorizenet_directpost/currency` | Alla |
| Felsök | `payment_it/authorizenet_directpost/debug` | Alla |
| Kreditkortstyper | `payment_it/authorizenet_directpost/cctypes` | Alla |
| Kreditkortsverifiering | `payment_it/authorizenet_directpost/useccv` | Alla |
| Betalning från tillämpliga länder | `payment_it/authorizenet_directpost/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_it/authorizenet_directpost/specificcountry` | Alla |
| Minsta ordersumma | `payment_it/authorizenet_directpost/min_order_total` | Alla |
| Maximal ordersumma | `payment_it/authorizenet_directpost/max_order_total` | Alla |
| Sorteringsordning | `payment_it/authorizenet_directpost/sort_order` | Alla |
| Aktiverad | `payment_it/cybersource/active` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_it/cybersource/payment_action` | Endast Commerce Enterprise |
| Titel | `payment_it/cybersource/title` | Endast Commerce Enterprise |
| Ny orderstatus | `payment_it/cybersource/order_status` | Endast Commerce Enterprise |
| Felsök | `payment_it/cybersource/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_it/cybersource/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_it/cybersource/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_it/cybersource/specificcountry` | Endast Commerce Enterprise |
| Minsta ordersumma | `payment_it/cybersource/min_order_total` | Endast Commerce Enterprise |
| Maximal ordersumma | `payment_it/cybersource/max_order_total` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_it/cybersource/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_it/worldpay/active` | Endast Commerce Enterprise |
| Titel | `payment_it/worldpay/title` | Endast Commerce Enterprise |
| Tillåt redigering av kontaktinformation | `payment_it/worldpay/fix_contact` | Endast Commerce Enterprise |
| Dölj kontaktinformation | `payment_it/worldpay/hide_contact` | Endast Commerce Enterprise |
| Signaturfält | `payment_it/worldpay/signature_fields` | Endast Commerce Enterprise |
| Felsök | `payment_it/worldpay/debug` | Endast Commerce Enterprise |
| Betalningsåtgärd för test | `payment_it/worldpay/test_action` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_it/worldpay/payment_action` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_it/worldpay/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_it/worldpay/specificcountry` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_it/worldpay/cvv_fraud_case` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_it/worldpay/avs_fraud_case` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_it/worldpay/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_it/eway/active` | Endast Commerce Enterprise |
| Anslutningstyp | `payment_it/eway/connection_type` | Endast Commerce Enterprise |
| Titel | `payment_it/eway/title` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_it/eway/payment_action` | Endast Commerce Enterprise |
| Felsök | `payment_it/eway/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_it/eway/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_it/eway/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_it/eway/specificcountry` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_it/eway/sort_order` | Endast Commerce Enterprise |
| Schemalagd hämtning | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Schemalagd hämtning | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alla |
| Schemalagd hämtning | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Aktiverad | `payment_fr/free/active` | Alla |
| Titel | `payment_fr/free/title` | Alla |
| Ny orderstatus | `payment_fr/free/order_status` | Alla |
| Fakturera alla artiklar automatiskt | `payment_fr/free/payment_action` | Alla |
| Betalning från tillämpliga länder | `payment_fr/free/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_fr/free/specificcountry` | Alla |
| Sorteringsordning | `payment_fr/free/sort_order` | Alla |
| Aktiverad | `payment_fr/cashondelivery/active` | Alla |
| Titel | `payment_fr/cashondelivery/title` | Alla |
| Ny orderstatus | `payment_fr/cashondelivery/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_fr/cashondelivery/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_fr/cashondelivery/specificcountry` | Alla |
| Instruktioner | `payment_fr/cashondelivery/instructions` | Alla |
| Minsta ordersumma | `payment_fr/cashondelivery/min_order_total` | Alla |
| Maximal ordersumma | `payment_fr/cashondelivery/max_order_total` | Alla |
| Sorteringsordning | `payment_fr/cashondelivery/sort_order` | Alla |
| Aktiverad | `payment_fr/banktransfer/active` | Alla |
| Titel | `payment_fr/banktransfer/title` | Alla |
| Ny orderstatus | `payment_fr/banktransfer/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_fr/banktransfer/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_fr/banktransfer/specificcountry` | Alla |
| Instruktioner | `payment_fr/banktransfer/instructions` | Alla |
| Minsta ordersumma | `payment_fr/banktransfer/min_order_total` | Alla |
| Maximal ordersumma | `payment_fr/banktransfer/max_order_total` | Alla |
| Sorteringsordning | `payment_fr/banktransfer/sort_order` | Alla |
| Aktiverad | `payment_fr/checkmo/active` | Alla |
| Titel | `payment_fr/checkmo/title` | Alla |
| Ny orderstatus | `payment_fr/checkmo/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_fr/checkmo/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_fr/checkmo/specificcountry` | Alla |
| Minsta ordersumma | `payment_fr/checkmo/min_order_total` | Alla |
| Maximal ordersumma | `payment_fr/checkmo/max_order_total` | Alla |
| Sorteringsordning | `payment_fr/checkmo/sort_order` | Alla |
| Aktiverad | `payment_fr/purchaseorder/active` | Alla |
| Titel | `payment_fr/purchaseorder/title` | Alla |
| Ny orderstatus | `payment_fr/purchaseorder/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_fr/purchaseorder/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_fr/purchaseorder/specificcountry` | Alla |
| Minsta ordersumma | `payment_fr/purchaseorder/min_order_total` | Alla |
| Maximal ordersumma | `payment_fr/purchaseorder/max_order_total` | Alla |
| Sorteringsordning | `payment_fr/purchaseorder/sort_order` | Alla |
| Aktiverad | `payment_fr/authorizenet_directpost/active` | Alla |
| Betalningsåtgärd | `payment_fr/authorizenet_directpost/payment_action` | Alla |
| Titel | `payment_fr/authorizenet_directpost/title` | Alla |
| Ny orderstatus | `payment_fr/authorizenet_directpost/order_status` | Alla |
| Godkänd valuta | `payment_fr/authorizenet_directpost/currency` | Alla |
| Felsök | `payment_fr/authorizenet_directpost/debug` | Alla |
| Kreditkortstyper | `payment_fr/authorizenet_directpost/cctypes` | Alla |
| Kreditkortsverifiering | `payment_fr/authorizenet_directpost/useccv` | Alla |
| Betalning från tillämpliga länder | `payment_fr/authorizenet_directpost/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_fr/authorizenet_directpost/specificcountry` | Alla |
| Minsta ordersumma | `payment_fr/authorizenet_directpost/min_order_total` | Alla |
| Maximal ordersumma | `payment_fr/authorizenet_directpost/max_order_total` | Alla |
| Sorteringsordning | `payment_fr/authorizenet_directpost/sort_order` | Alla |
| Aktiverad | `payment_fr/cybersource/active` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_fr/cybersource/payment_action` | Endast Commerce Enterprise |
| Titel | `payment_fr/cybersource/title` | Endast Commerce Enterprise |
| Ny orderstatus | `payment_fr/cybersource/order_status` | Endast Commerce Enterprise |
| Felsök | `payment_fr/cybersource/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_fr/cybersource/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_fr/cybersource/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_fr/cybersource/specificcountry` | Endast Commerce Enterprise |
| Minsta ordersumma | `payment_fr/cybersource/min_order_total` | Endast Commerce Enterprise |
| Maximal ordersumma | `payment_fr/cybersource/max_order_total` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_fr/cybersource/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_fr/worldpay/active` | Endast Commerce Enterprise |
| Titel | `payment_fr/worldpay/title` | Endast Commerce Enterprise |
| Tillåt redigering av kontaktinformation | `payment_fr/worldpay/fix_contact` | Endast Commerce Enterprise |
| Dölj kontaktinformation | `payment_fr/worldpay/hide_contact` | Endast Commerce Enterprise |
| Felsök | `payment_fr/worldpay/debug` | Endast Commerce Enterprise |
| Betalningsåtgärd för test | `payment_fr/worldpay/test_action` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_fr/worldpay/payment_action` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_fr/worldpay/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_fr/worldpay/specificcountry` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_fr/worldpay/cvv_fraud_case` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_fr/worldpay/avs_fraud_case` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_fr/worldpay/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_fr/eway/active` | Endast Commerce Enterprise |
| Anslutningstyp | `payment_fr/eway/connection_type` | Endast Commerce Enterprise |
| Titel | `payment_fr/eway/title` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_fr/eway/payment_action` | Endast Commerce Enterprise |
| Felsök | `payment_fr/eway/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_fr/eway/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_fr/eway/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_fr/eway/specificcountry` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_fr/eway/sort_order` | Endast Commerce Enterprise |
| Schemalagd hämtning | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Schemalagd hämtning | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alla |
| Schemalagd hämtning | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Aktiverad | `payment_jp/free/active` | Alla |
| Titel | `payment_jp/free/title` | Alla |
| Ny orderstatus | `payment_jp/free/order_status` | Alla |
| Fakturera alla artiklar automatiskt | `payment_jp/free/payment_action` | Alla |
| Betalning från tillämpliga länder | `payment_jp/free/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_jp/free/specificcountry` | Alla |
| Sorteringsordning | `payment_jp/free/sort_order` | Alla |
| Aktiverad | `payment_jp/cashondelivery/active` | Alla |
| Titel | `payment_jp/cashondelivery/title` | Alla |
| Ny orderstatus | `payment_jp/cashondelivery/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_jp/cashondelivery/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_jp/cashondelivery/specificcountry` | Alla |
| Instruktioner | `payment_jp/cashondelivery/instructions` | Alla |
| Minsta ordersumma | `payment_jp/cashondelivery/min_order_total` | Alla |
| Maximal ordersumma | `payment_jp/cashondelivery/max_order_total` | Alla |
| Sorteringsordning | `payment_jp/cashondelivery/sort_order` | Alla |
| Aktiverad | `payment_jp/banktransfer/active` | Alla |
| Titel | `payment_jp/banktransfer/title` | Alla |
| Ny orderstatus | `payment_jp/banktransfer/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_jp/banktransfer/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_jp/banktransfer/specificcountry` | Alla |
| Instruktioner | `payment_jp/banktransfer/instructions` | Alla |
| Minsta ordersumma | `payment_jp/banktransfer/min_order_total` | Alla |
| Maximal ordersumma | `payment_jp/banktransfer/max_order_total` | Alla |
| Sorteringsordning | `payment_jp/banktransfer/sort_order` | Alla |
| Aktiverad | `payment_jp/checkmo/active` | Alla |
| Titel | `payment_jp/checkmo/title` | Alla |
| Ny orderstatus | `payment_jp/checkmo/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_jp/checkmo/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_jp/checkmo/specificcountry` | Alla |
| Minsta ordersumma | `payment_jp/checkmo/min_order_total` | Alla |
| Maximal ordersumma | `payment_jp/checkmo/max_order_total` | Alla |
| Sorteringsordning | `payment_jp/checkmo/sort_order` | Alla |
| Aktiverad | `payment_jp/purchaseorder/active` | Alla |
| Titel | `payment_jp/purchaseorder/title` | Alla |
| Ny orderstatus | `payment_jp/purchaseorder/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_jp/purchaseorder/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_jp/purchaseorder/specificcountry` | Alla |
| Minsta ordersumma | `payment_jp/purchaseorder/min_order_total` | Alla |
| Maximal ordersumma | `payment_jp/purchaseorder/max_order_total` | Alla |
| Sorteringsordning | `payment_jp/purchaseorder/sort_order` | Alla |
| Aktiverad | `payment_jp/authorizenet_directpost/active` | Alla |
| Betalningsåtgärd | `payment_jp/authorizenet_directpost/payment_action` | Alla |
| Titel | `payment_jp/authorizenet_directpost/title` | Alla |
| Ny orderstatus | `payment_jp/authorizenet_directpost/order_status` | Alla |
| Godkänd valuta | `payment_jp/authorizenet_directpost/currency` | Alla |
| Felsök | `payment_jp/authorizenet_directpost/debug` | Alla |
| Kreditkortstyper | `payment_jp/authorizenet_directpost/cctypes` | Alla |
| Kreditkortsverifiering | `payment_jp/authorizenet_directpost/useccv` | Alla |
| Betalning från tillämpliga länder | `payment_jp/authorizenet_directpost/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_jp/authorizenet_directpost/specificcountry` | Alla |
| Minsta ordersumma | `payment_jp/authorizenet_directpost/min_order_total` | Alla |
| Maximal ordersumma | `payment_jp/authorizenet_directpost/max_order_total` | Alla |
| Sorteringsordning | `payment_jp/authorizenet_directpost/sort_order` | Alla |
| Aktiverad | `payment_jp/cybersource/active` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_jp/cybersource/payment_action` | Endast Commerce Enterprise |
| Titel | `payment_jp/cybersource/title` | Endast Commerce Enterprise |
| Felsök | `payment_jp/cybersource/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_jp/cybersource/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_jp/cybersource/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_jp/cybersource/specificcountry` | Endast Commerce Enterprise |
| Minsta ordersumma | `payment_jp/cybersource/min_order_total` | Endast Commerce Enterprise |
| Maximal ordersumma | `payment_jp/cybersource/max_order_total` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_jp/cybersource/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_jp/worldpay/active` | Endast Commerce Enterprise |
| Titel | `payment_jp/worldpay/title` | Endast Commerce Enterprise |
| Tillåt redigering av kontaktinformation | `payment_jp/worldpay/fix_contact` | Endast Commerce Enterprise |
| Dölj kontaktinformation | `payment_jp/worldpay/hide_contact` | Endast Commerce Enterprise |
| Felsök | `payment_jp/worldpay/debug` | Endast Commerce Enterprise |
| Betalningsåtgärd för test | `payment_jp/worldpay/test_action` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_jp/worldpay/payment_action` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_jp/worldpay/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_jp/worldpay/specificcountry` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_jp/worldpay/cvv_fraud_case` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_jp/worldpay/avs_fraud_case` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_jp/worldpay/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_jp/eway/active` | Endast Commerce Enterprise |
| Anslutningstyp | `payment_jp/eway/connection_type` | Endast Commerce Enterprise |
| Titel | `payment_jp/eway/title` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_jp/eway/payment_action` | Endast Commerce Enterprise |
| Felsök | `payment_jp/eway/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_jp/eway/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_jp/eway/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_jp/eway/specificcountry` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_jp/eway/sort_order` | Endast Commerce Enterprise |
| Schemalagd hämtning | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Schemalagd hämtning | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alla |
| Schemalagd hämtning | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Kreditkortsinställningar | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | Alla |
| Avvisa transaktion om: | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alla |
| Schemalagd hämtning | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alla |
| Aktiverad | `payment_au/free/active` | Alla |
| Titel | `payment_au/free/title` | Alla |
| Ny orderstatus | `payment_au/free/order_status` | Alla |
| Fakturera alla artiklar automatiskt | `payment_au/free/payment_action` | Alla |
| Betalning från tillämpliga länder | `payment_au/free/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_au/free/specificcountry` | Alla |
| Sorteringsordning | `payment_au/free/sort_order` | Alla |
| Aktiverad | `payment_au/cashondelivery/active` | Alla |
| Titel | `payment_au/cashondelivery/title` | Alla |
| Ny orderstatus | `payment_au/cashondelivery/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_au/cashondelivery/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_au/cashondelivery/specificcountry` | Alla |
| Instruktioner | `payment_au/cashondelivery/instructions` | Alla |
| Minsta ordersumma | `payment_au/cashondelivery/min_order_total` | Alla |
| Maximal ordersumma | `payment_au/cashondelivery/max_order_total` | Alla |
| Sorteringsordning | `payment_au/cashondelivery/sort_order` | Alla |
| Aktiverad | `payment_au/banktransfer/active` | Alla |
| Titel | `payment_au/banktransfer/title` | Alla |
| Ny orderstatus | `payment_au/banktransfer/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_au/banktransfer/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_au/banktransfer/specificcountry` | Alla |
| Instruktioner | `payment_au/banktransfer/instructions` | Alla |
| Minsta ordersumma | `payment_au/banktransfer/min_order_total` | Alla |
| Maximal ordersumma | `payment_au/banktransfer/max_order_total` | Alla |
| Sorteringsordning | `payment_au/banktransfer/sort_order` | Alla |
| Aktiverad | `payment_au/checkmo/active` | Alla |
| Titel | `payment_au/checkmo/title` | Alla |
| Ny orderstatus | `payment_au/checkmo/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_au/checkmo/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_au/checkmo/specificcountry` | Alla |
| Gör kontrollen betalbar till | `payment_au/checkmo/payable_to` | Alla |
| Skicka kontroll till | `payment_au/checkmo/mailing_address` | Alla |
| Minsta ordersumma | `payment_au/checkmo/min_order_total` | Alla |
| Maximal ordersumma | `payment_au/checkmo/max_order_total` | Alla |
| Sorteringsordning | `payment_au/checkmo/sort_order` | Alla |
| Aktiverad | `payment_au/purchaseorder/active` | Alla |
| Titel | `payment_au/purchaseorder/title` | Alla |
| Ny orderstatus | `payment_au/purchaseorder/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_au/purchaseorder/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_au/purchaseorder/specificcountry` | Alla |
| Minsta ordersumma | `payment_au/purchaseorder/min_order_total` | Alla |
| Maximal ordersumma | `payment_au/purchaseorder/max_order_total` | Alla |
| Sorteringsordning | `payment_au/purchaseorder/sort_order` | Alla |
| Aktiverad | `payment_au/authorizenet_directpost/active` | Alla |
| Betalningsåtgärd | `payment_au/authorizenet_directpost/payment_action` | Alla |
| Titel | `payment_au/authorizenet_directpost/title` | Alla |
| Ny orderstatus | `payment_au/authorizenet_directpost/order_status` | Alla |
| Godkänd valuta | `payment_au/authorizenet_directpost/currency` | Alla |
| Felsök | `payment_au/authorizenet_directpost/debug` | Alla |
| Kreditkortstyper | `payment_au/authorizenet_directpost/cctypes` | Alla |
| Kreditkortsverifiering | `payment_au/authorizenet_directpost/useccv` | Alla |
| Betalning från tillämpliga länder | `payment_au/authorizenet_directpost/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_au/authorizenet_directpost/specificcountry` | Alla |
| Minsta ordersumma | `payment_au/authorizenet_directpost/min_order_total` | Alla |
| Maximal ordersumma | `payment_au/authorizenet_directpost/max_order_total` | Alla |
| Sorteringsordning | `payment_au/authorizenet_directpost/sort_order` | Alla |
| Aktiverad | `payment_au/cybersource/active` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_au/cybersource/payment_action` | Endast Commerce Enterprise |
| Titel | `payment_au/cybersource/title` | Endast Commerce Enterprise |
| Affärs-ID | `payment_au/cybersource/merchant_id` | Endast Commerce Enterprise \| ![Krypterad](/help/assets/configuration/cloud-enc.png) |
| Profil-ID | `payment_au/cybersource/profile_id` | Endast Commerce Enterprise \| ![Krypterad](/help/assets/configuration/cloud-enc.png) |
| Ny orderstatus | `payment_au/cybersource/order_status` | Endast Commerce Enterprise |
| Felsök | `payment_au/cybersource/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_au/cybersource/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_au/cybersource/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_au/cybersource/specificcountry` | Endast Commerce Enterprise |
| Minsta ordersumma | `payment_au/cybersource/min_order_total` | Endast Commerce Enterprise |
| Maximal ordersumma | `payment_au/cybersource/max_order_total` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_au/cybersource/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_au/worldpay/active` | Endast Commerce Enterprise |
| Titel | `payment_au/worldpay/title` | Endast Commerce Enterprise |
| Installations-ID | `payment_au/worldpay/installation_id` | Endast Commerce Enterprise |
| Tillåt redigering av kontaktinformation | `payment_au/worldpay/fix_contact` | Endast Commerce Enterprise |
| Dölj kontaktinformation | `payment_au/worldpay/hide_contact` | Endast Commerce Enterprise |
| Signaturfält | `payment_au/worldpay/signature_fields` | Endast Commerce Enterprise |
| Felsök | `payment_au/worldpay/debug` | Endast Commerce Enterprise |
| Testläge | `payment_au/worldpay/sandbox_flag` | Endast Commerce Enterprise |
| Betalningsåtgärd för test | `payment_au/worldpay/test_action` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_au/worldpay/payment_action` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_au/worldpay/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_au/worldpay/specificcountry` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_au/worldpay/cvv_fraud_case` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_au/worldpay/avs_fraud_case` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_au/worldpay/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_au/eway/active` | Endast Commerce Enterprise |
| Anslutningstyp | `payment_au/eway/connection_type` | Endast Commerce Enterprise |
| Titel | `payment_au/eway/title` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_au/eway/payment_action` | Endast Commerce Enterprise |
| Felsök | `payment_au/eway/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_au/eway/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_au/eway/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_au/eway/specificcountry` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_au/eway/sort_order` | Endast Commerce Enterprise |
| Schemalagd hämtning | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Schemalagd hämtning | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Aktivera den här lösningen | `payment/paypal_payment_pro/active` | Alla |
| Kreditkortsinställningar | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | Alla |
| Avvisa transaktion om: | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alla |
| Schemalagd hämtning | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alla |
| Kreditkortsinställningar | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | Alla |
| Avvisa transaktion om: | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alla |
| Schemalagd hämtning | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alla |
| Schemalagd hämtning | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Alla |
| Aktiverad | `payment_ca/free/active` | Alla |
| Titel | `payment_ca/free/title` | Alla |
| Ny orderstatus | `payment_ca/free/order_status` | Alla |
| Fakturera alla artiklar automatiskt | `payment_ca/free/payment_action` | Alla |
| Betalning från tillämpliga länder | `payment_ca/free/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_ca/free/specificcountry` | Alla |
| Sorteringsordning | `payment_ca/free/sort_order` | Alla |
| Aktiverad | `payment_ca/cashondelivery/active` | Alla |
| Titel | `payment_ca/cashondelivery/title` | Alla |
| Ny orderstatus | `payment_ca/cashondelivery/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_ca/cashondelivery/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_ca/cashondelivery/specificcountry` | Alla |
| Instruktioner | `payment_ca/cashondelivery/instructions` | Alla |
| Minsta ordersumma | `payment_ca/cashondelivery/min_order_total` | Alla |
| Maximal ordersumma | `payment_ca/cashondelivery/max_order_total` | Alla |
| Sorteringsordning | `payment_ca/cashondelivery/sort_order` | Alla |
| Aktiverad | `payment_ca/banktransfer/active` | Alla |
| Titel | `payment_ca/banktransfer/title` | Alla |
| Ny orderstatus | `payment_ca/banktransfer/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_ca/banktransfer/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_ca/banktransfer/specificcountry` | Alla |
| Instruktioner | `payment_ca/banktransfer/instructions` | Alla |
| Minsta ordersumma | `payment_ca/banktransfer/min_order_total` | Alla |
| Maximal ordersumma | `payment_ca/banktransfer/max_order_total` | Alla |
| Sorteringsordning | `payment_ca/banktransfer/sort_order` | Alla |
| Aktiverad | `payment_ca/checkmo/active` | Alla |
| Titel | `payment_ca/checkmo/title` | Alla |
| Ny orderstatus | `payment_ca/checkmo/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_ca/checkmo/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_ca/checkmo/specificcountry` | Alla |
| Minsta ordersumma | `payment_ca/checkmo/min_order_total` | Alla |
| Maximal ordersumma | `payment_ca/checkmo/max_order_total` | Alla |
| Sorteringsordning | `payment_ca/checkmo/sort_order` | Alla |
| Aktiverad | `payment_ca/purchaseorder/active` | Alla |
| Titel | `payment_ca/purchaseorder/title` | Alla |
| Ny orderstatus | `payment_ca/purchaseorder/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_ca/purchaseorder/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_ca/purchaseorder/specificcountry` | Alla |
| Minsta ordersumma | `payment_ca/purchaseorder/min_order_total` | Alla |
| Maximal ordersumma | `payment_ca/purchaseorder/max_order_total` | Alla |
| Sorteringsordning | `payment_ca/purchaseorder/sort_order` | Alla |
| Aktiverad | `payment_ca/authorizenet_directpost/active` | Alla |
| Betalningsåtgärd | `payment_ca/authorizenet_directpost/payment_action` | Alla |
| Titel | `payment_ca/authorizenet_directpost/title` | Alla |
| Godkänd valuta | `payment_ca/authorizenet_directpost/currency` | Alla |
| Felsök | `payment_ca/authorizenet_directpost/debug` | Alla |
| Kreditkortstyper | `payment_ca/authorizenet_directpost/cctypes` | Alla |
| Kreditkortsverifiering | `payment_ca/authorizenet_directpost/useccv` | Alla |
| Betalning från tillämpliga länder | `payment_ca/authorizenet_directpost/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_ca/authorizenet_directpost/specificcountry` | Alla |
| Minsta ordersumma | `payment_ca/authorizenet_directpost/min_order_total` | Alla |
| Maximal ordersumma | `payment_ca/authorizenet_directpost/max_order_total` | Alla |
| Sorteringsordning | `payment_ca/authorizenet_directpost/sort_order` | Alla |
| Aktiverad | `payment_ca/cybersource/active` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_ca/cybersource/payment_action` | Endast Commerce Enterprise |
| Titel | `payment_ca/cybersource/title` | Endast Commerce Enterprise |
| Felsök | `payment_ca/cybersource/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_ca/cybersource/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_ca/cybersource/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_ca/cybersource/specificcountry` | Endast Commerce Enterprise |
| Minsta ordersumma | `payment_ca/cybersource/min_order_total` | Endast Commerce Enterprise |
| Maximal ordersumma | `payment_ca/cybersource/max_order_total` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_ca/cybersource/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_ca/worldpay/active` | Endast Commerce Enterprise |
| Titel | `payment_ca/worldpay/title` | Endast Commerce Enterprise |
| Tillåt redigering av kontaktinformation | `payment_ca/worldpay/fix_contact` | Endast Commerce Enterprise |
| Dölj kontaktinformation | `payment_ca/worldpay/hide_contact` | Endast Commerce Enterprise |
| Signaturfält | `payment_ca/worldpay/signature_fields` | Endast Commerce Enterprise |
| Felsök | `payment_ca/worldpay/debug` | Endast Commerce Enterprise |
| Betalningsåtgärd för test | `payment_ca/worldpay/test_action` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_ca/worldpay/payment_action` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_ca/worldpay/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_ca/worldpay/specificcountry` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_ca/worldpay/cvv_fraud_case` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_ca/worldpay/avs_fraud_case` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_ca/worldpay/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_ca/eway/active` | Endast Commerce Enterprise |
| Anslutningstyp | `payment_ca/eway/connection_type` | Endast Commerce Enterprise |
| Titel | `payment_ca/eway/title` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_ca/eway/payment_action` | Endast Commerce Enterprise |
| Felsök | `payment_ca/eway/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_ca/eway/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_ca/eway/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_ca/eway/specificcountry` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_ca/eway/sort_order` | Endast Commerce Enterprise |
| Schemalagd hämtning | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Schemalagd hämtning | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Aktiverad | `payment_other/free/active` | Alla |
| Titel | `payment_other/free/title` | Alla |
| Ny orderstatus | `payment_other/free/order_status` | Alla |
| Fakturera alla artiklar automatiskt | `payment_other/free/payment_action` | Alla |
| Betalning från tillämpliga länder | `payment_other/free/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_other/free/specificcountry` | Alla |
| Sorteringsordning | `payment_other/free/sort_order` | Alla |
| Aktiverad | `payment_other/cashondelivery/active` | Alla |
| Titel | `payment_other/cashondelivery/title` | Alla |
| Ny orderstatus | `payment_other/cashondelivery/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_other/cashondelivery/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_other/cashondelivery/specificcountry` | Alla |
| Instruktioner | `payment_other/cashondelivery/instructions` | Alla |
| Minsta ordersumma | `payment_other/cashondelivery/min_order_total` | Alla |
| Maximal ordersumma | `payment_other/cashondelivery/max_order_total` | Alla |
| Sorteringsordning | `payment_other/cashondelivery/sort_order` | Alla |
| Aktiverad | `payment_other/banktransfer/active` | Alla |
| Titel | `payment_other/banktransfer/title` | Alla |
| Ny orderstatus | `payment_other/banktransfer/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_other/banktransfer/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_other/banktransfer/specificcountry` | Alla |
| Instruktioner | `payment_other/banktransfer/instructions` | Alla |
| Minsta ordersumma | `payment_other/banktransfer/min_order_total` | Alla |
| Maximal ordersumma | `payment_other/banktransfer/max_order_total` | Alla |
| Sorteringsordning | `payment_other/banktransfer/sort_order` | Alla |
| Aktiverad | `payment_other/checkmo/active` | Alla |
| Titel | `payment_other/checkmo/title` | Alla |
| Ny orderstatus | `payment_other/checkmo/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_other/checkmo/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_other/checkmo/specificcountry` | Alla |
| Minsta ordersumma | `payment_other/checkmo/min_order_total` | Alla |
| Maximal ordersumma | `payment_other/checkmo/max_order_total` | Alla |
| Sorteringsordning | `payment_other/checkmo/sort_order` | Alla |
| Aktiverad | `payment_other/purchaseorder/active` | Alla |
| Titel | `payment_other/purchaseorder/title` | Alla |
| Ny orderstatus | `payment_other/purchaseorder/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_other/purchaseorder/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_other/purchaseorder/specificcountry` | Alla |
| Minsta ordersumma | `payment_other/purchaseorder/min_order_total` | Alla |
| Maximal ordersumma | `payment_other/purchaseorder/max_order_total` | Alla |
| Sorteringsordning | `payment_other/purchaseorder/sort_order` | Alla |
| Aktiverad | `payment_other/authorizenet_directpost/active` | Alla |
| Betalningsåtgärd | `payment_other/authorizenet_directpost/payment_action` | Alla |
| Titel | `payment_other/authorizenet_directpost/title` | Alla |
| Godkänd valuta | `payment_other/authorizenet_directpost/currency` | Alla |
| Felsök | `payment_other/authorizenet_directpost/debug` | Alla |
| E-postkund | `payment_other/authorizenet_directpost/email_customer` | Alla |
| Kreditkortstyper | `payment_other/authorizenet_directpost/cctypes` | Alla |
| Kreditkortsverifiering | `payment_other/authorizenet_directpost/useccv` | Alla |
| Betalning från tillämpliga länder | `payment_other/authorizenet_directpost/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_other/authorizenet_directpost/specificcountry` | Alla |
| Minsta ordersumma | `payment_other/authorizenet_directpost/min_order_total` | Alla |
| Maximal ordersumma | `payment_other/authorizenet_directpost/max_order_total` | Alla |
| Sorteringsordning | `payment_other/authorizenet_directpost/sort_order` | Alla |
| Aktiverad | `payment_other/cybersource/active` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_other/cybersource/payment_action` | Endast Commerce Enterprise |
| Titel | `payment_other/cybersource/title` | Endast Commerce Enterprise |
| Felsök | `payment_other/cybersource/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_other/cybersource/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_other/cybersource/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_other/cybersource/specificcountry` | Endast Commerce Enterprise |
| Minsta ordersumma | `payment_other/cybersource/min_order_total` | Endast Commerce Enterprise |
| Maximal ordersumma | `payment_other/cybersource/max_order_total` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_other/cybersource/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_other/worldpay/active` | Endast Commerce Enterprise |
| Titel | `payment_other/worldpay/title` | Endast Commerce Enterprise |
| Tillåt redigering av kontaktinformation | `payment_other/worldpay/fix_contact` | Endast Commerce Enterprise |
| Dölj kontaktinformation | `payment_other/worldpay/hide_contact` | Endast Commerce Enterprise |
| Signaturfält | `payment_other/worldpay/signature_fields` | Endast Commerce Enterprise |
| Felsök | `payment_other/worldpay/debug` | Endast Commerce Enterprise |
| Betalningsåtgärd för test | `payment_other/worldpay/test_action` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_other/worldpay/payment_action` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_other/worldpay/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_other/worldpay/specificcountry` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_other/worldpay/cvv_fraud_case` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_other/worldpay/avs_fraud_case` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_other/worldpay/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_other/eway/active` | Endast Commerce Enterprise |
| Anslutningstyp | `payment_other/eway/connection_type` | Endast Commerce Enterprise |
| Titel | `payment_other/eway/title` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_other/eway/payment_action` | Endast Commerce Enterprise |
| Felsök | `payment_other/eway/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_other/eway/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_other/eway/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_other/eway/specificcountry` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_other/eway/sort_order` | Endast Commerce Enterprise |
| Schemalagd hämtning | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Aktiverad | `payment_de/checkmo/active` | Alla |
| Titel | `payment_de/checkmo/title` | Alla |
| Ny orderstatus | `payment_de/checkmo/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_de/checkmo/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_de/checkmo/specificcountry` | Alla |
| Minsta ordersumma | `payment_de/checkmo/min_order_total` | Alla |
| Maximal ordersumma | `payment_de/checkmo/max_order_total` | Alla |
| Sorteringsordning | `payment_de/checkmo/sort_order` | Alla |
| Aktiverad | `payment_de/banktransfer/active` | Alla |
| Titel | `payment_de/banktransfer/title` | Alla |
| Ny orderstatus | `payment_de/banktransfer/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_de/banktransfer/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_de/banktransfer/specificcountry` | Alla |
| Instruktioner | `payment_de/banktransfer/instructions` | Alla |
| Minsta ordersumma | `payment_de/banktransfer/min_order_total` | Alla |
| Maximal ordersumma | `payment_de/banktransfer/max_order_total` | Alla |
| Sorteringsordning | `payment_de/banktransfer/sort_order` | Alla |
| Aktiverad | `payment_de/cashondelivery/active` | Alla |
| Titel | `payment_de/cashondelivery/title` | Alla |
| Ny orderstatus | `payment_de/cashondelivery/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_de/cashondelivery/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_de/cashondelivery/specificcountry` | Alla |
| Instruktioner | `payment_de/cashondelivery/instructions` | Alla |
| Minsta ordersumma | `payment_de/cashondelivery/min_order_total` | Alla |
| Maximal ordersumma | `payment_de/cashondelivery/max_order_total` | Alla |
| Sorteringsordning | `payment_de/cashondelivery/sort_order` | Alla |
| Aktiverad | `payment_de/free/active` | Alla |
| Titel | `payment_de/free/title` | Alla |
| Ny orderstatus | `payment_de/free/order_status` | Alla |
| Fakturera alla artiklar automatiskt | `payment_de/free/payment_action` | Alla |
| Betalning från tillämpliga länder | `payment_de/free/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_de/free/specificcountry` | Alla |
| Sorteringsordning | `payment_de/free/sort_order` | Alla |
| Aktiverad | `payment_de/purchaseorder/active` | Alla |
| Titel | `payment_de/purchaseorder/title` | Alla |
| Ny orderstatus | `payment_de/purchaseorder/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_de/purchaseorder/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_de/purchaseorder/specificcountry` | Alla |
| Minsta ordersumma | `payment_de/purchaseorder/min_order_total` | Alla |
| Maximal ordersumma | `payment_de/purchaseorder/max_order_total` | Alla |
| Sorteringsordning | `payment_de/purchaseorder/sort_order` | Alla |
| Aktiverad | `payment_de/cybersource/active` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_de/cybersource/payment_action` | Endast Commerce Enterprise |
| Titel | `payment_de/cybersource/title` | Endast Commerce Enterprise |
| Ny orderstatus | `payment_de/cybersource/order_status` | Endast Commerce Enterprise |
| Felsök | `payment_de/cybersource/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_de/cybersource/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_de/cybersource/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_de/cybersource/specificcountry` | Endast Commerce Enterprise |
| Minsta ordersumma | `payment_de/cybersource/min_order_total` | Endast Commerce Enterprise |
| Maximal ordersumma | `payment_de/cybersource/max_order_total` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_de/cybersource/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_de/authorizenet_directpost/active` | Alla |
| Betalningsåtgärd | `payment_de/authorizenet_directpost/payment_action` | Alla |
| Titel | `payment_de/authorizenet_directpost/title` | Alla |
| Ny orderstatus | `payment_de/authorizenet_directpost/order_status` | Alla |
| Godkänd valuta | `payment_de/authorizenet_directpost/currency` | Alla |
| Felsök | `payment_de/authorizenet_directpost/debug` | Alla |
| Kreditkortstyper | `payment_de/authorizenet_directpost/cctypes` | Alla |
| Kreditkortsverifiering | `payment_de/authorizenet_directpost/useccv` | Alla |
| Betalning från tillämpliga länder | `payment_de/authorizenet_directpost/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_de/authorizenet_directpost/specificcountry` | Alla |
| Minsta ordersumma | `payment_de/authorizenet_directpost/min_order_total` | Alla |
| Maximal ordersumma | `payment_de/authorizenet_directpost/max_order_total` | Alla |
| Sorteringsordning | `payment_de/authorizenet_directpost/sort_order` | Alla |
| Aktiverad | `payment_de/worldpay/active` | Endast Commerce Enterprise |
| Titel | `payment_de/worldpay/title` | Endast Commerce Enterprise |
| Tillåt redigering av kontaktinformation | `payment_de/worldpay/fix_contact` | Endast Commerce Enterprise |
| Dölj kontaktinformation | `payment_de/worldpay/hide_contact` | Endast Commerce Enterprise |
| Signaturfält | `payment_de/worldpay/signature_fields` | Endast Commerce Enterprise |
| Testläge | `payment_de/worldpay/sandbox_flag` | Endast Commerce Enterprise |
| Betalningsåtgärd för test | `payment_de/worldpay/test_action` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_de/worldpay/payment_action` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_de/worldpay/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_de/worldpay/specificcountry` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_de/worldpay/cvv_fraud_case` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_de/worldpay/avs_fraud_case` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_de/worldpay/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_de/eway/active` | Endast Commerce Enterprise |
| Anslutningstyp | `payment_de/eway/connection_type` | Endast Commerce Enterprise |
| Titel | `payment_de/eway/title` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_de/eway/payment_action` | Endast Commerce Enterprise |
| Felsök | `payment_de/eway/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_de/eway/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_de/eway/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_de/eway/specificcountry` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_de/eway/sort_order` | Endast Commerce Enterprise |
| Schemalagd hämtning | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Schemalagd hämtning | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | Alla |
| Schemalagd hämtning | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Aktiverad | `payment_gb/checkmo/active` | Alla |
| Titel | `payment_gb/checkmo/title` | Alla |
| Ny orderstatus | `payment_gb/checkmo/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_gb/checkmo/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_gb/checkmo/specificcountry` | Alla |
| Gör kontrollen betalbar till | `payment_gb/checkmo/payable_to` | Alla |
| Minsta ordersumma | `payment_gb/checkmo/min_order_total` | Alla |
| Maximal ordersumma | `payment_gb/checkmo/max_order_total` | Alla |
| Sorteringsordning | `payment_gb/checkmo/sort_order` | Alla |
| Aktiverad | `payment_gb/banktransfer/active` | Alla |
| Titel | `payment_gb/banktransfer/title` | Alla |
| Ny orderstatus | `payment_gb/banktransfer/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_gb/banktransfer/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_gb/banktransfer/specificcountry` | Alla |
| Instruktioner | `payment_gb/banktransfer/instructions` | Alla |
| Minsta ordersumma | `payment_gb/banktransfer/min_order_total` | Alla |
| Maximal ordersumma | `payment_gb/banktransfer/max_order_total` | Alla |
| Sorteringsordning | `payment_gb/banktransfer/sort_order` | Alla |
| Aktiverad | `payment_gb/cashondelivery/active` | Alla |
| Titel | `payment_gb/cashondelivery/title` | Alla |
| Ny orderstatus | `payment_gb/cashondelivery/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_gb/cashondelivery/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_gb/cashondelivery/specificcountry` | Alla |
| Instruktioner | `payment_gb/cashondelivery/instructions` | Alla |
| Minsta ordersumma | `payment_gb/cashondelivery/min_order_total` | Alla |
| Maximal ordersumma | `payment_gb/cashondelivery/max_order_total` | Alla |
| Sorteringsordning | `payment_gb/cashondelivery/sort_order` | Alla |
| Aktiverad | `payment_gb/free/active` | Alla |
| Titel | `payment_gb/free/title` | Alla |
| Ny orderstatus | `payment_gb/free/order_status` | Alla |
| Fakturera alla artiklar automatiskt | `payment_gb/free/payment_action` | Alla |
| Betalning från tillämpliga länder | `payment_gb/free/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_gb/free/specificcountry` | Alla |
| Sorteringsordning | `payment_gb/free/sort_order` | Alla |
| Aktiverad | `payment_gb/purchaseorder/active` | Alla |
| Titel | `payment_gb/purchaseorder/title` | Alla |
| Ny orderstatus | `payment_gb/purchaseorder/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_gb/purchaseorder/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_gb/purchaseorder/specificcountry` | Alla |
| Minsta ordersumma | `payment_gb/purchaseorder/min_order_total` | Alla |
| Maximal ordersumma | `payment_gb/purchaseorder/max_order_total` | Alla |
| Sorteringsordning | `payment_gb/purchaseorder/sort_order` | Alla |
| Aktiverad | `payment_gb/cybersource/active` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_gb/cybersource/payment_action` | Endast Commerce Enterprise |
| Titel | `payment_gb/cybersource/title` | Endast Commerce Enterprise |
| Ny orderstatus | `payment_gb/cybersource/order_status` | Endast Commerce Enterprise |
| Felsök | `payment_gb/cybersource/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_gb/cybersource/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_gb/cybersource/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_gb/cybersource/specificcountry` | Endast Commerce Enterprise |
| Minsta ordersumma | `payment_gb/cybersource/min_order_total` | Endast Commerce Enterprise |
| Maximal ordersumma | `payment_gb/cybersource/max_order_total` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_gb/cybersource/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_gb/authorizenet_directpost/active` | Alla |
| Betalningsåtgärd | `payment_gb/authorizenet_directpost/payment_action` | Alla |
| Titel | `payment_gb/authorizenet_directpost/title` | Alla |
| Ny orderstatus | `payment_gb/authorizenet_directpost/order_status` | Alla |
| Godkänd valuta | `payment_gb/authorizenet_directpost/currency` | Alla |
| Felsök | `payment_gb/authorizenet_directpost/debug` | Alla |
| Kreditkortstyper | `payment_gb/authorizenet_directpost/cctypes` | Alla |
| Kreditkortsverifiering | `payment_gb/authorizenet_directpost/useccv` | Alla |
| Betalning från tillämpliga länder | `payment_gb/authorizenet_directpost/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_gb/authorizenet_directpost/specificcountry` | Alla |
| Minsta ordersumma | `payment_gb/authorizenet_directpost/min_order_total` | Alla |
| Maximal ordersumma | `payment_gb/authorizenet_directpost/max_order_total` | Alla |
| Sorteringsordning | `payment_gb/authorizenet_directpost/sort_order` | Alla |
| Aktiverad | `payment_gb/worldpay/active` | Endast Commerce Enterprise |
| Titel | `payment_gb/worldpay/title` | Endast Commerce Enterprise |
| MD5-hemlighet för transaktioner | `payment_gb/worldpay/md5_secret` | Endast Commerce Enterprise |
| Tillåt redigering av kontaktinformation | `payment_gb/worldpay/fix_contact` | Endast Commerce Enterprise |
| Dölj kontaktinformation | `payment_gb/worldpay/hide_contact` | Endast Commerce Enterprise |
| Signaturfält | `payment_gb/worldpay/signature_fields` | Endast Commerce Enterprise |
| Felsök | `payment_gb/worldpay/debug` | Endast Commerce Enterprise |
| Betalningsåtgärd för test | `payment_gb/worldpay/test_action` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_gb/worldpay/payment_action` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_gb/worldpay/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_gb/worldpay/specificcountry` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_gb/worldpay/cvv_fraud_case` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_gb/worldpay/avs_fraud_case` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_gb/worldpay/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_gb/eway/active` | Endast Commerce Enterprise |
| Anslutningstyp | `payment_gb/eway/connection_type` | Endast Commerce Enterprise |
| Titel | `payment_gb/eway/title` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_gb/eway/payment_action` | Endast Commerce Enterprise |
| Felsök | `payment_gb/eway/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_gb/eway/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_gb/eway/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_gb/eway/specificcountry` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_gb/eway/sort_order` | Endast Commerce Enterprise |
| Schemalagd hämtning | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Schemalagd hämtning | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | Alla |
| Kreditkortsinställningar | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | Alla |
| Avvisa transaktion om: | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alla |
| Schemalagd hämtning | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | Alla |
| Aktivera PayPal-kredit | `payment/wps_express_bml/active` | Alla |
| Schemalagd hämtning | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alla |
| Kreditkortsinställningar | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | Alla |
| Avvisa transaktion om: | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alla |
| Schemalagd hämtning | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | Alla |
| Schemalagd hämtning | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Alla |
| Format för PayPal Merchant Pages | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Alla |
| Aktiverad | `payment_us/free/active` | Alla |
| Titel | `payment_us/free/title` | Alla |
| Ny orderstatus | `payment_us/free/order_status` | Alla |
| Fakturera alla artiklar automatiskt | `payment_us/free/payment_action` | Alla |
| Betalning från tillämpliga länder | `payment_us/free/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_us/free/specificcountry` | Alla |
| Sorteringsordning | `payment_us/free/sort_order` | Alla |
| Aktiverad | `payment_us/cashondelivery/active` | Alla |
| Titel | `payment_us/cashondelivery/title` | Alla |
| Ny orderstatus | `payment_us/cashondelivery/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_us/cashondelivery/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_us/cashondelivery/specificcountry` | Alla |
| Instruktioner | `payment_us/cashondelivery/instructions` | Alla |
| Minsta ordersumma | `payment_us/cashondelivery/min_order_total` | Alla |
| Maximal ordersumma | `payment_us/cashondelivery/max_order_total` | Alla |
| Sorteringsordning | `payment_us/cashondelivery/sort_order` | Alla |
| Aktiverad | `payment_us/banktransfer/active` | Alla |
| Titel | `payment_us/banktransfer/title` | Alla |
| Ny orderstatus | `payment_us/banktransfer/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_us/banktransfer/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_us/banktransfer/specificcountry` | Alla |
| Instruktioner | `payment_us/banktransfer/instructions` | Alla |
| Minsta ordersumma | `payment_us/banktransfer/min_order_total` | Alla |
| Maximal ordersumma | `payment_us/banktransfer/max_order_total` | Alla |
| Sorteringsordning | `payment_us/banktransfer/sort_order` | Alla |
| Aktiverad | `payment_us/checkmo/active` | Alla |
| Titel | `payment_us/checkmo/title` | Alla |
| Ny orderstatus | `payment_us/checkmo/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_us/checkmo/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_us/checkmo/specificcountry` | Alla |
| Gör kontrollen betalbar till | `payment_us/checkmo/payable_to` | Alla |
| Minsta ordersumma | `payment_us/checkmo/min_order_total` | Alla |
| Maximal ordersumma | `payment_us/checkmo/max_order_total` | Alla |
| Sorteringsordning | `payment_us/checkmo/sort_order` | Alla |
| Aktiverad | `payment_us/purchaseorder/active` | Alla |
| Titel | `payment_us/purchaseorder/title` | Alla |
| Ny orderstatus | `payment_us/purchaseorder/order_status` | Alla |
| Betalning från tillämpliga länder | `payment_us/purchaseorder/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_us/purchaseorder/specificcountry` | Alla |
| Minsta ordersumma | `payment_us/purchaseorder/min_order_total` | Alla |
| Maximal ordersumma | `payment_us/purchaseorder/max_order_total` | Alla |
| Sorteringsordning | `payment_us/purchaseorder/sort_order` | Alla |
| Aktiverad | `payment_us/authorizenet_directpost/active` | Alla |
| Betalningsåtgärd | `payment_us/authorizenet_directpost/payment_action` | Alla |
| Titel | `payment_us/authorizenet_directpost/title` | Alla |
| Ny orderstatus | `payment_us/authorizenet_directpost/order_status` | Alla |
| Godkänd valuta | `payment_us/authorizenet_directpost/currency` | Alla |
| Felsök | `payment_us/authorizenet_directpost/debug` | Alla |
| Kreditkortstyper | `payment_us/authorizenet_directpost/cctypes` | Alla |
| Kreditkortsverifiering | `payment_us/authorizenet_directpost/useccv` | Alla |
| Betalning från tillämpliga länder | `payment_us/authorizenet_directpost/allowspecific` | Alla |
| Stöd från särskilda länder | `payment_us/authorizenet_directpost/specificcountry` | Alla |
| Minsta ordersumma | `payment_us/authorizenet_directpost/min_order_total` | Alla |
| Maximal ordersumma | `payment_us/authorizenet_directpost/max_order_total` | Alla |
| Sorteringsordning | `payment_us/authorizenet_directpost/sort_order` | Alla |
| Aktiverad | `payment_us/cybersource/active` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_us/cybersource/payment_action` | Endast Commerce Enterprise |
| Titel | `payment_us/cybersource/title` | Endast Commerce Enterprise |
| Ny orderstatus | `payment_us/cybersource/order_status` | Endast Commerce Enterprise |
| Felsök | `payment_us/cybersource/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_us/cybersource/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_us/cybersource/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_us/cybersource/specificcountry` | Endast Commerce Enterprise |
| Minsta ordersumma | `payment_us/cybersource/min_order_total` | Endast Commerce Enterprise |
| Maximal ordersumma | `payment_us/cybersource/max_order_total` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_us/cybersource/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_us/worldpay/active` | Endast Commerce Enterprise |
| Titel | `payment_us/worldpay/title` | Endast Commerce Enterprise |
| Tillåt redigering av kontaktinformation | `payment_us/worldpay/fix_contact` | Endast Commerce Enterprise |
| Dölj kontaktinformation | `payment_us/worldpay/hide_contact` | Endast Commerce Enterprise |
| Signaturfält | `payment_us/worldpay/signature_fields` | Endast Commerce Enterprise |
| Felsök | `payment_us/worldpay/debug` | Endast Commerce Enterprise |
| Betalningsåtgärd för test | `payment_us/worldpay/test_action` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_us/worldpay/payment_action` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_us/worldpay/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_us/worldpay/specificcountry` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för CVV | `payment_us/worldpay/cvv_fraud_case` | Endast Commerce Enterprise |
| Ange beställningsstatus till Misstänkt bedrägeri för postnummer AVS | `payment_us/worldpay/avs_fraud_case` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_us/worldpay/sort_order` | Endast Commerce Enterprise |
| Aktiverad | `payment_us/eway/active` | Endast Commerce Enterprise |
| Anslutningstyp | `payment_us/eway/connection_type` | Endast Commerce Enterprise |
| Titel | `payment_us/eway/title` | Endast Commerce Enterprise |
| Betalningsåtgärd | `payment_us/eway/payment_action` | Endast Commerce Enterprise |
| Felsök | `payment_us/eway/debug` | Endast Commerce Enterprise |
| Kreditkortstyper | `payment_us/eway/cctypes` | Endast Commerce Enterprise |
| Betalning från tillämpliga länder | `payment_us/eway/allowspecific` | Endast Commerce Enterprise |
| Stöd från särskilda länder | `payment_us/eway/specificcountry` | Endast Commerce Enterprise |
| Sorteringsordning | `payment_us/eway/sort_order` | |

{style="table-layout:auto"}
