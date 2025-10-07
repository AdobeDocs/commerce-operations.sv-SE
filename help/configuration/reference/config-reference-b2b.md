---
title: Referens för konfigurationssökvägar för B2B-tillägg
description: Läs mer om konfigurationssökvägar och värden för B2B-tillägg för Adobe Commerce. Upptäck företag-, betalnings-, offert- och B2B-specifika konfigureringsalternativ.
feature: Configuration, B2B, Companies, Payments, Quotes
exl-id: 3414dea1-17c9-4462-8b8a-51a6045b0bc9
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 0%

---

# Referens för konfigurationssökvägar för B2B-tillägg

_Det här är tillgängligt för instanser där B2B för Adobe Commerce är installerat._

I det här avsnittet visas konfigurationssökvägar för Commerce Enterprise B2B-tillägg. [`magento app:config:dump`-kommandot &#x200B;](../cli/export-configuration.md) skriver dessa värden till den delade konfigurationsfilen `app/etc/config.php` som ska finnas i källkontrollen.

>[!INFO]
>
>Den här referensen visar _endast_ konfigurationssökvägar som är unika för B2B för Adobe Commerce. Det här tillägget innehåller alla konfigurationssökvägar för Adobe Commerce.

Information om dessa konfigurationssökvägar finns i:

- [Sökvägar för betalningskonfiguration](config-reference-payment.md)
- [Referens för känsliga och systemspecifika konfigurationssökvägar](config-reference-sens.md)

Om du vill åsidosätta konfigurationsinställningar eller ange känsliga inställningar läser du [Använda miljövariabler för att åsidosätta konfigurationsinställningar](override-config-settings.md#environment-variables).

## Allmän kategori

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **[!UICONTROL Stores]** > Inställningar > **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### B2B-funktioner

Dessa konfigurationsvärden är tillgängliga i Admin i **[!UICONTROL Stores]** > Inställningar > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| Namn | Konfigurationssökväg | Krypterad? | Systemspecifik? | Känslig? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Aktivera företag | `btob/website_configuration/company_active` | | | |
| Aktivera delad katalog | `btob/website_configuration/sharedcatalog_active` | | | |
| Aktivera B2B-offert | `btob/website_configuration/negotiablequote_active` | | | |
| Aktivera snabbordning | `btob/website_configuration/quickorder_active` | | | |
| Aktivera rekvisitionslista | `btob/website_configuration/requisition_list_active` | | | |
| Tillämpliga betalningsmetoder | `btob/default_b2b_payment_methods/applicable_payment_methods` | | | |
| Betalningsmetoder | `btob/default_b2b_payment_methods/available_payment_methods` | | | |

{style="table-layout:auto"}

## Kategorier

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **[!UICONTROL Stores]** > Inställningar > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### Sökvägar för företagskonfiguration

Dessa konfigurationsvärden är tillgängliga i Admin i **[!UICONTROL Stores]** > Inställningar > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| Namn | Konfigurationssökväg | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|
| Tillåt företagsregistrering från Storefront | `company/general/allow_company_registration` | | | |
| E-postmottagare för företagsregistrering | `company/email/company_registration` | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka företagsregistreringskopia till | `company/email/company_registration_copy` | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka e-postkopieringsmetod | `company/email/company_copy_method` | | | |
| E-postadress för standardföretagsregistrering | `company/email/company_notify_admin_template` | | | |
| Kundrelaterade mejl | `company/email/heading_customer` | | | |
| E-postadress tilldelad som standardsäljare | `company/email/customer_sales_representative_template` | | | |
| Tilldela företag som standard till kundens e-postadress | `company/email/customer_company_customer_assign_template` | | | |
| E-postadress för standardföretagsadministratör | `company/email/customer_assign_super_user_template` | | | |
| Inaktiv e-postadress för standardföretagsadministratör | `company/email/customer_inactivate_super_user_template` | | | |
| Standardföretagsadministratör ändrad till e-postadress för medlem | `company/email/customer_remove_super_user_template` | | | |
| Aktiv e-postadress för standardkundstatus | `company/email/customer_account_activated_template` | | | |
| Inaktiv e-postadress för standardkundstatus | `company/email/customer_account_locked_template` | | | |
| Ändra företagsstatus | `company/email/heading_company_status` | | | |
| E-postmottagare för ändring av företagsstatus | `company/email/company_status_change` | | | |
| Skicka företagsstatus Ändra e-postkopia till | `company/email/company_status_change_copy` | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka e-postkopieringsmetod | `company/email/company_status_copy_method` | | | |
| Standardföretagsstatus Ändra till aktiv 1 e-post | `company/email/company_status_pending_approval_to_active_template` | | | |
| Standardföretagsstatus Ändra till aktiv 2-e-post | `company/email/company_status_rejected_blocked_to_active_template` | | | |
| Standardföretagsstatus Ändra till avvisat e-postmeddelande | `company/email/company_status_rejected_template` | | | |
| Standardföretagsstatus Ändra till blockerad e-post | `company/email/company_status_blocked_template` | | | |
| Standardföretagsstatus ändras till E-post för väntande godkännande | `company/email/company_status_pending_approval_template` | | | |
| Företagskrediter | `company/email/heading_company_credit` | | | |
| Företagskreditändring, e-postavsändare | `company/email/company_credit_change` |  | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka företagets kreditändring E-postkopia till | `company/email/company_credit_change_copy` | | | |
| Skicka e-postkopieringsmetod | `company/email/company_credit_copy_method` | | | |
| Allokerad e-postmall | `company/email/credit_allocated_email_template` | | | |
| Uppdaterad e-postmall | `company/email/credit_updated_email_template` | | | |
| Återbetald e-postmall | `company/email/credit_reimbursed_email_template` | | | |
| Mall för återförd e-post | `company/email/credit_refunded_email_template` | | | |
| Återställd e-postmall | `company/email/credit_reverted_email_template` | | | |

{style="table-layout:auto"}

### Rekvisitionslistor - sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Kunder** > **Rekvisitionslistor**.

| Namn | Konfigurationssökväg | Krypterad? | Systemspecifik? | Känslig? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Antal rekvisitionslistor | `requisitionlist/general/number_requisition_lists` | | | |

{style="table-layout:auto"}

## Försäljningskategori

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **Lagrar** > Inställningar > **Konfiguration** > **Försäljning**.

### Säljmejlsökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Försäljning** > **Försäljningsmeddelanden**.

| Namn | Konfigurationssökväg | Krypterad? | Systemspecifik? | Känslig? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Aktiverad | `sales_email/quote/enabled` | | | |
| Uppdaterad offertmall (till köpare) | `sales_email/quote/updated_buyer_template` | | | |
| Avböjd offertmall (till köpare) | `sales_email/quote/declined_buyer_template` | | | |
| Ny offertmall (för säljare) | `sales_email/quote/new_seller_template` | | | |
| Uppdaterad offertmall (till säljare) | `sales_email/quote/updated_seller_template` | | | |
| Förfallodatum för offert (i 48 timmar) | `sales_email/quote/expire_two_days_template` | | | |
| Förfallodatum för offert (i 24 timmar) | `sales_email/quote/expire_one_day_template` | | | |
| Återställning av förfallodatum | `sales_email/quote/expire_reset_template` | | | |
| Skicka offertens e-postkopia till | `sales_email/quote/copy_to` | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka offertkopieringsmetod | `sales_email/quote/copy_method` | | | |

{style="table-layout:auto"}

### Citattecken

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Försäljning** > **Kurser**.

| Namn | Konfigurationssökväg | Krypterad? | Systemspecifik? | Känslig? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Minimibelopp | `quote/general/minimum_amount` | | | |
| Meddelande om minimibelopp | `quote/general/minimum_amount_message` | | | |
| Förfallotid som standard | `quote/general/default_expiration_period` | | | |
| Filformat för överföring | `quote/attached_files/file_formats` | | | |
| Maximal filstorlek | `quote/attached_files/maximum_file_size` | | | |
| Minimibelopp | `quote/general/minimum_amount` | | | |
| Meddelande om minimibelopp | `quote/general/minimum_amount_message` | | | |
| Förfallotid som standard | `quote/general/default_expiration_period` | | | |
| Filformat för överföring | `quote/attached_files/file_formats` | | | |
| Maximal filstorlek | `quote/attached_files/maximum_file_size` | | | |

{style="table-layout:auto"}

## Sökvägar för betalningsmetod

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Försäljning** > **Betalningsmetoder**.

>[!INFO]
>
>Vilka sökvägar som är tillgängliga beror på vilket land du väljer.

| Namn | Konfigurationssökväg | Krypterad? | Systemspecifik? | Känslig? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Aktiverad | `payment/au/companycredit/active` | | | |
| Titel | `payment/au/companycredit/title` | | | |
| Ny orderstatus | `payment/au/companycredit/order_status` | | | |
| Betalning från tillämpliga länder | `payment/au/companycredit/allowspecific` | | | |
| Stöd från särskilda länder | `payment/au/companycredit/specificcountry` | | | |
| Minsta ordersumma | `payment/au/companycredit/min_order_total` | | | |
| Maximal ordersumma | `payment/au/companycredit/max_order_total` | | | |
| Sorteringsordning | `payment/au/companycredit/sort_order` | | | |
| Aktiverad | `payment/es/companycredit/active` | | | |
| Titel | `payment/es/companycredit/title` | | | |
| Ny orderstatus | `payment/es/companycredit/order_status` | | | |
| Betalning från tillämpliga länder | `payment/es/companycredit/allowspecific` | | | |
| Stöd från särskilda länder | `payment/es/companycredit/specificcountry` | | | |
| Minsta ordersumma | `payment/es/companycredit/min_order_total` | | | |
| Maximal ordersumma | `payment/es/companycredit/max_order_total` | | | |
| Sorteringsordning | `payment/es/companycredit/sort_order` | | | |
| Aktiverad | `payment/companycredit/active` | | | |
| Titel | `payment/companycredit/title` | | | |
| Ny orderstatus | `payment/companycredit/order_status` | | | |
| Betalning från tillämpliga länder | `payment/companycredit/allowspecific` | | | |
| Stöd från särskilda länder | `payment/companycredit/specificcountry` | | | |
| Minsta ordersumma | `payment/companycredit/min_order_total` | | | |
| Maximal ordersumma | `payment/companycredit/max_order_total` | | | |
| Sorteringsordning | `payment/companycredit/sort_order` | | | |
| Aktiverad | `payment/nz/companycredit/active` | | | |
| Titel | `payment/nz/companycredit/title` | | | |
| Ny orderstatus | `payment/nz/companycredit/order_status` | | | |
| Betalning från tillämpliga länder | `payment/nz/companycredit/allowspecific` | | | |
| Stöd från särskilda länder | `payment/nz/companycredit/specificcountry` | | | |
| Minsta ordersumma | `payment/nz/companycredit/min_order_total` | | | |
| Maximal ordersumma | `payment/nz/companycredit/max_order_total` | | | |
| Sorteringsordning | `payment/nz/companycredit/sort_order` | | | |
| Aktiverad | `payment/us/companycredit/active` | | | |
| Titel | `payment/us/companycredit/title` | | | |
| Ny orderstatus | `payment/us/companycredit/order_status` | | | |
| Betalning från tillämpliga länder | `payment/us/companycredit/allowspecific` | | | |
| Stöd från särskilda länder | `payment/us/companycredit/specificcountry` | | | |
| Minsta ordersumma | `payment/us/companycredit/min_order_total` | | | |
| Maximal ordersumma | `payment/us/companycredit/max_order_total` | | | |
| Sorteringsordning | `payment/us/companycredit/sort_order` | | | |
| Aktiverad | `payment/gb/companycredit/active` | | | |
| Titel | `payment/gb/companycredit/title` | | | |
| Ny orderstatus | `payment/gb/companycredit/order_status` | | | |
| Betalning från tillämpliga länder | `payment/gb/companycredit/allowspecific` | | | |
| Stöd från särskilda länder | `payment/gb/companycredit/specificcountry` | | | |
| Minsta ordersumma | `payment/gb/companycredit/min_order_total` | | | |
| Maximal ordersumma | `payment/gb/companycredit/max_order_total` | | | |
| Sorteringsordning | `payment/gb/companycredit/sort_order` | | | |
| Aktiverad | `payment/de/companycredit/active` | | | |
| Titel | `payment/de/companycredit/title` | | | |
| Ny orderstatus | `payment/de/companycredit/order_status` | | | |
| Betalning från tillämpliga länder | `payment/de/companycredit/allowspecific` | | | |
| Stöd från särskilda länder | `payment/de/companycredit/specificcountry` | | | |
| Minsta ordersumma | `payment/de/companycredit/min_order_total` | | | |
| Maximal ordersumma | `payment/de/companycredit/max_order_total` | | | |
| Sorteringsordning | `payment/de/companycredit/sort_order` | | | |
| Aktiverad | `payment/other/companycredit/active` | | | |
| Titel | `payment/other/companycredit/title` | | | |
| Ny orderstatus | `payment/other/companycredit/order_status` | | | |
| Betalning från tillämpliga länder | `payment/other/companycredit/allowspecific` | | | |
| Stöd från särskilda länder | `payment/other/companycredit/specificcountry` | | | |
| Minsta ordersumma | `payment/other/companycredit/min_order_total` | | | |
| Maximal ordersumma | `payment/other/companycredit/max_order_total` | | | |
| Sorteringsordning | `payment/other/companycredit/sort_order` | | | |
| Aktiverad | `payment/ca/companycredit/active` | | | |
| Titel | `payment/ca/companycredit/title` | | | |
| Ny orderstatus | `payment/ca/companycredit/order_status` | | | |
| Betalning från tillämpliga länder | `payment/ca/companycredit/allowspecific` | | | |
| Stöd från särskilda länder | `payment/ca/companycredit/specificcountry` | | | |
| Minsta ordersumma | `payment/ca/companycredit/min_order_total` | | | |
| Maximal ordersumma | `payment/ca/companycredit/max_order_total` | | | |
| Sorteringsordning | `payment/ca/companycredit/sort_order` | | | |
| Aktiverad | `payment/hk/companycredit/active` | | | |
| Titel | `payment/hk/companycredit/title` | | | |
| Ny orderstatus | `payment/hk/companycredit/order_status` | | | |
| Betalning från tillämpliga länder | `payment/hk/companycredit/allowspecific` | | | |
| Stöd från särskilda länder | `payment/hk/companycredit/specificcountry` | | | |
| Minsta ordersumma | `payment/hk/companycredit/min_order_total` | | | |
| Maximal ordersumma | `payment/hk/companycredit/max_order_total` | | | |
| Sorteringsordning | `payment/hk/companycredit/sort_order` | | | |
| Aktiverad | `payment/jp/companycredit/active` | | | |
| Titel | `payment/jp/companycredit/title` | | | |
| Ny orderstatus | `payment/jp/companycredit/order_status` | | | |
| Betalning från tillämpliga länder | `payment/jp/companycredit/allowspecific` | | | |
| Stöd från särskilda länder | `payment/jp/companycredit/specificcountry` | | | |
| Minsta ordersumma | `payment/jp/companycredit/min_order_total` | | | |
| Maximal ordersumma | `payment/jp/companycredit/max_order_total` | | | |
| Sorteringsordning | `payment/jp/companycredit/sort_order` | | | |
| Aktiverad | `payment/fr/companycredit/active` | | | |
| Titel | `payment/fr/companycredit/title` | | | |
| Ny orderstatus | `payment/fr/companycredit/order_status` | | | |
| Betalning från tillämpliga länder | `payment/fr/companycredit/allowspecific` | | | |
| Stöd från särskilda länder | `payment/fr/companycredit/specificcountry` | | | |
| Minsta ordersumma | `payment/fr/companycredit/min_order_total` | | | |
| Maximal ordersumma | `payment/fr/companycredit/max_order_total` | | | |
| Sorteringsordning | `payment/fr/companycredit/sort_order` | | | |
| Aktiverad | `payment/it/companycredit/active` | | | |
| Titel | `payment/it/companycredit/title` | | | |
| Ny orderstatus | `payment/it/companycredit/order_status` | | | |
| Betalning från tillämpliga länder | `payment/it/companycredit/allowspecific` | | | |
| Stöd från särskilda länder | `payment/it/companycredit/specificcountry` | | | |
| Minsta ordersumma | `payment/it/companycredit/min_order_total` | | | |
| Maximal ordersumma | `payment/it/companycredit/max_order_total` | | | |
| Sorteringsordning | `payment/it/companycredit/sort_order` | | | |

{style="table-layout:auto"}
