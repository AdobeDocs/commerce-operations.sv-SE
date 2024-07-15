---
title: Referens för kundkonfigurationssökvägar
description: Se en lista över kundkonfigurationsvärden.
feature: Configuration, Customers
exl-id: a0571423-6fbd-4cfc-9797-a13c0c24bb53
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# Referens för kundkonfigurationssökvägar

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **Lagrar** > Inställningar > **Konfiguration** > **Kunder**.

[`magento app:config:dump`-kommandot ](../cli/export-configuration.md) skriver dessa värden till den delade konfigurationsfilen `app/etc/config.php` som ska finnas i källkontrollen. Om du vill åsidosätta konfigurationsinställningar eller ange känsliga inställningar läser du [Använda miljövariabler för att åsidosätta konfigurationsinställningar](override-config-settings.md#environment-variables). Det här avsnittet listar _inte_ [känsliga och systemspecifika värden](config-reference-sens.md).

## Sökvägar till nyhetsbrev

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Kunder** > **Nyhetsbrev**.

| Namn | Konfigurationssökväg | Endast Commerce? |
|--------------|--------------|--------------|
| Tillåt gästprenumeration | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bekräfta måste | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bekräftelse av e-postavsändare | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för bekräftelse | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändaren lyckades | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för slutförda | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Avbeställ e-postavsändare | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall för prenumeration | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Sökvägar för kundkonfiguration

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Kunder** > **Kundkonfiguration**.

| Namn | Konfigurationssökväg | Endast Commerce? |
|--------------|--------------|--------------|
| Intervall för onlineminuter | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dela kundkonton | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera automatisk tilldelning till kundgrupp | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skatteberäkning baserad på | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardgrupp | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupp för giltigt moms-ID - inhemska | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupp för giltigt moms-ID - inom unionen | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupp för ogiltigt moms-ID | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupp för verifieringsfel | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validera vid varje transaktion | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardvärde för Inaktivera automatiska gruppändringar baserat på moms-ID | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa momsregistreringsnummer i butiken | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardvälkomstmeddelande | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardvälkomstmeddelande utan lösenord | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändare | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bekräfta att e-post krävs | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bekräftelselänkens e-postadress | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Välkomstmeddelande | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Generera kundvänligt ID | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skyddstyp för lösenordsåterställning | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximalt antal begäranden om återställning av lösenord | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta tid mellan begäranden om återställning av lösenord | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Glömt e-postmall | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Påminn e-postmall | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Återställ lösenordsmall | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändare för lösenordsmall | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Förfallotid för återställningslänk (timmar) | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera Fyll i automatiskt vid inloggning/glömt lösenordsformulär | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Antal teckenklasser som krävs | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximalt antal inloggningsfel för att låsa konto | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minsta lösenordslängd | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utelåsningstid (minuter) | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Antal rader i en gatuadress | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa prefix | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alternativ för listrutor med prefix | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa mellannamn (inledande) | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa suffix | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Listrutealternativ för suffix | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa födelsedatum | `customer/address/dob_show`<br>I enlighet med gällande säkerhets- och sekretessrutiner måste du vara medveten om eventuella juridiska risker och säkerhetsrisker som är förknippade med lagring av kundens fullständiga födelsedatum (månad, dag, år) tillsammans med andra personliga identifierare, till exempel fullständigt namn, innan du samlar in eller bearbetar sådana data. | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa momsregistreringsnummer | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa kön | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera butikskreditfunktioner | `customer/magento_customerbalance/is_enabled` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Visa butikskredithistorik för kunder | `customer/magento_customerbalance/show_history` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Återbetala butikskrediten automatiskt | `customer/magento_customerbalance/refund_automatically` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| E-postavsändare för butikskredituppdatering | `customer/magento_customerbalance/email_identity` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| E-postmall för butikskredituppdatering | `customer/magento_customerbalance/email_template` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Omdirigera kund till kontouppsättningen efter inloggning | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Text | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Text en rad | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera funktioner för kundsegment | `customer/magento_customersegment/is_enabled` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktivera CAPTCHA på Storefront | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Teckensnitt | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visningsläge | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Antal misslyckade inloggningsförsök | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout för CAPTCHA (minuter) | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Antal symboler | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Symboler som används i CAPTCHA | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Skiftlägeskänslig | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Sökvägar i önskelistan

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Kunder** > **Önsklista**.

| Namn | Konfigurationssökväg | Endast Commerce? |
|--------------|--------------|--------------|
| Aktiverad | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera flera önskelistor | `wishlist/general/multiple_enabled` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Antal flera önskelistor | `wishlist/general/multiple_wishlist_number` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| E-postavsändare | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Max antal e-postmeddelanden som får skickas | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Längd på e-posttext | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visa Önsklistesammanfattning | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Sökvägar för inbjudningar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Kunder** > **Inbjudningar**.

| Namn | Konfigurationssökväg | Endast Commerce? |
|--------------|--------------|--------------|
| Aktivera funktioner för inbjudningar | `magento_invitation/general/enabled` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktivera inbjudningar i Storefront | `magento_invitation/general/enabled_on_front` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Refererad kundgrupp | `magento_invitation/general/registration_use_inviter_group` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Registrering av nya konton | `magento_invitation/general/registration_required_invitation` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Tillåt kunder att lägga till anpassat meddelande i e-postinbjudan | `magento_invitation/general/allow_customer_message` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximalt antal inbjudningar som kan skickas samtidigt | `magento_invitation/general/max_invitation_amount_per_send` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Avsändare av e-postinbjudan till kund | `magento_invitation/email/identity` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| E-postmall för kundinbjudan | `magento_invitation/email/template` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Banor för belöningspunkter

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Kunder** > **Belöningspunkter**.

| Namn | Konfigurationssökväg | Endast Commerce? |
|--------------|--------------|--------------|
| Aktivera funktionen för belöningspunkter | `magento_reward/general/is_enabled` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Aktivera funktionen Belöna punkter på Storefront | `magento_reward/general/is_enabled_on_front` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Kunder kan se historik över belöningspunkter | `magento_reward/general/publish_history` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Inlösningströskel för belöningspoäng | `magento_reward/general/min_points_balance` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Belöningspoäng för tak vid | `magento_reward/general/max_points_balance` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Belöningspoäng förfaller om (dagar) | `magento_reward/general/expiration_days` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Beräkning av förfallodatum för belöningspunkter | `magento_reward/general/expiry_calculation` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Återbetala belöningspunkter automatiskt | `magento_reward/general/refund_automatically` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Ta automatiskt bort belöningspunkter från återbetalningsbelopp | `magento_reward/general/deduct_automatically` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Landningssida | `magento_reward/general/landing_page` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Inköp | `magento_reward/points/order` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Registrering | `magento_reward/points/register` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Registrering av nyhetsbrev | `magento_reward/points/newsletter` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Konverterar inbjudan till kund | `magento_reward/points/invitation_customer` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Kvantitetsgräns för inbjudan till kundkonvertering | `magento_reward/points/invitation_customer_limit` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Konverterar inbjudan till ordning | `magento_reward/points/invitation_order` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Kvantitetsgräns för inbjudan till orderkonvertering | `magento_reward/points/invitation_order_limit` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Inbjudningskonvertering till orderbelöning | `magento_reward/points/invitation_order_frequency` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Granska inlämningen | `magento_reward/points/review` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Kvantitetsgräns för mottagna granskningar | `magento_reward/points/review_limit` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| E-postavsändare | `magento_reward/notification/email_sender` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Prenumerera kunder som standard | `magento_reward/notification/subscribe_by_default` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| E-post för saldouppdatering | `magento_reward/notification/balance_update_template` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| E-postmeddelande om förfallovarning för belöningspunkter | `magento_reward/notification/expiry_warning_template` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Förfallovarning före (dagar) | `magento_reward/notification/expiry_day_before` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Kampanjsökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Kunder** > **Kampanjer**.

| Namn | Konfigurationssökväg | Endast Commerce? |
|--------------|--------------|--------------|
| Aktivera påminnelsemeddelanden | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frekvens | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervall | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minut av timmen | `promo/magento_reminder/minutes` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Starttid | `promo/magento_reminder/time` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Maximalt antal e-postmeddelanden per körning | `promo/magento_reminder/limit` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Feltröskel för e-postutskick | `promo/magento_reminder/threshold` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Påminnelse - e-postavsändare | `promo/magento_reminder/identity` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Kodlängd | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kodformat | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kodprefix | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kodsuffix | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Streck var X tecken | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Sökvägar för presentregister

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Kunder** > **Presentregister**.

| Namn | Konfigurationssökväg | Endast Commerce? |
|--------------|--------------|--------------|
| Aktivera presentregistret | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Högsta antal registranter | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändare | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändare | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tröskelvärde för högsta antal skickade e-postmeddelanden | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postmall | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-postavsändare | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Beständiga kundvagnssökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Kunder** > **Beständig varukorg**.

| Namn | Konfigurationssökväg | Endast Commerce? |
|--------------|--------------|--------------|
| Aktivera beständighet | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Livstid för beständighet (sekunder) | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aktivera &quot;Kom ihåg mig&quot; | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standardvärdet &quot;Kom ihåg mig&quot; | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rensa beständighet vid utloggning | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beständig kundvagn | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beständig önskelista | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Behåll nyligen sorterade objekt | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Behåll produkter som för närvarande jämförs | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beständig jämförelsehistorik | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Behåll nyligen visade produkter | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Behåll kundgruppsmedlemskap och segmentering | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
