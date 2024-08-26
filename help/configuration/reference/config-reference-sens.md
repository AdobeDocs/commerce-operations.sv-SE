---
title: Känsliga och systemspecifika sökvägar
description: Se en lista med systemspecifika och känsliga konfigurationsvärden.
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: e5a1c5634124831c8d5a95df6818ec30c372e8dd
workflow-type: tm+mt
source-wordcount: '3676'
ht-degree: 0%

---

# Känsliga och systemspecifika inställningar

I det här avsnittet visas konfigurationssökvägar för systemspecifika och känsliga inställningar:

- [`magento app:config:dump`-kommandot ](../cli/export-configuration.md) skriver systemspecifika inställningar till den systemspecifika konfigurationsfilen, `app/etc/env.php`, som _inte_ ska finnas i källkontrollen. Den skriver även delad konfiguration för alla Commerce-instanser till `app/etc/config.php`, den här filen _bör_ finnas i källkontrollen.
- Kommandot [`magento config:sensitive:set` ](../cli/set-configuration-values.md) skriver känsliga inställningar till `app/etc/env.php`.

  Du kan också ange känsliga värden med hjälp av konfigurationsvariabler som beskrivs i [Använd miljövariabler för att åsidosätta konfigurationsinställningarna](../reference/override-config-settings.md#environment-variables).

En lista med andra konfigurationssökvägar finns i:

- [Alla konfigurationssökvägar utom betalningar](../reference/config-reference-general.md)
- [Sökvägar för betalningskonfiguration](../reference/config-reference-payment.md).

>[!INFO]
>
>Alla konfigurationssökvägar som listas i det här avsnittet är känsliga. Kolumnen `System-specific?` visar vilka värden som också är systemspecifika.

## Allmänna kategorikänsliga och systemspecifika sökvägar

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **Lagrar** > Inställningar > **Konfiguration** > **Allmänt**.

### Webbsökvägar, känsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Allmänt** > **Webb**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Bas-URL | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Bas länk-URL | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Bas-URL för statiska vyfiler | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Bas-URL för användarmediefiler | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| URL för säker bas | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| URL för säker baslänk | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Säker bas-URL för statiska vyfiler | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Säker bas-URL för användarmediefiler | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Standardwebb-URL | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Standard-URL utan rutt | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Cookie-sökväg | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Cookie-domän | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Cookie-livstid | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Använd endast HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Begränsningsläge för cookie | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Känsliga och systemspecifika sökvägar för valutainställningar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Allmänt** > **Valutainställning**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-postmottagare med fel | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Lagra e-postadresskänsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **E-postkonfiguration** > **Allmänt** > **Lagra e-postadresser**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Avsändarens namn | `trans_email/ident_general/name` | | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Avsändarens e-postadress | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Avsändarens namn | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Avsändarens e-postadress | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Avsändarens namn | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Avsändarens e-postadress | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Avsändarens namn | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Avsändarens e-postadress | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Avsändarens namn | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Avsändarens e-postadress | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Kontaktkänsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Allmänt** > **Kontakter**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Skicka e-post till | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postavsändare | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postmall | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### New Relic rapporterar känsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Allmänt** > **New Relic Reporting**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| New Relic konto-ID | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| New Relic-program-ID | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| New Relic API-nyckel | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel för insikter | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| New Relic API-URL | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-URL för insikter | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Kundernas kategorikänsliga och systemspecifika sökvägar

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **Lagrar** > Inställningar > **Konfiguration** > **Kunder**.

### Kundkonfigurationskänsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Kunder** > **Kundkonfiguration**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Standarddomän för e-post | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## Katalogkategori

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **Lagrar** > Inställningar > **Konfiguration** > **Katalog**.

### Katalogkänsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Katalog** > **Katalog**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-postmottagare med fel | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| YouTube API-nyckel | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Värdnamn för Solr-server | `catalog/search/solr_server_hostname` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Solr-serverport | `catalog/search/solr_server_port` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Användarnamn för Solr-server | `catalog/search/solr_server_username` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för Solr-server | `catalog/search/solr_server_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Sökväg till Solr-server | `catalog/search/solr_server_path` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Värdnamn för Elasticsearch Server | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch Server-port | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch-indexprefix | `catalog/search/elasticsearch_index_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Aktivera Elasticsearch HTTP-autentisering | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP-användarnamn | `catalog/search/elasticsearch_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP-lösenord | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Elasticsearch Server-timeout | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP-användarnamn | `catalog/search/elasticsearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP-lösenord | `catalog/search/elasticsearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Elasticsearch Server-timeout | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| OpenSearch Server-värdnamn | `catalog/search/opensearch_server_hostname` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| OpenSearch Server-port | `catalog/search/opensearch_server_port` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Indexprefix för OpenSearch | `catalog/search/opensearch_index_prefix` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Aktivera OpenSearch HTTP-autentisering | `catalog/search/opensearch_enable_auth` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| OpenSearch HTTP-användarnamn | `catalog/search/opensearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| OpenSearch HTTP-lösenord | `catalog/search/opensearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Timeout för OpenSearch Server | `catalog/search/opensearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

>[!NOTE]
>
>OpenSearch-inställningarna infördes i Adobe Commerce 2.4.6.

### Lagerkänsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Katalog** > **Lager**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Google API-nyckel | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### XML - systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Katalog** > **XML-platskarta**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-postmottagare med fel | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Försäljningskategori

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **Lagrar** > Inställningar > **Konfiguration** > **Försäljning**.

### Leveransinställningskänsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Försäljning** > **Leveransinställningar**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Land | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Region/stat | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Postnummer | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Ort | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gatuadress | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gatuadress 2 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live-konto | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### E-postmeddelanden som är känsliga och systemspecifika

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Försäljning** > **Försäljningsmeddelanden**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Skicka e-postkopia till beställning | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka e-postkopia av orderkommentar till | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka e-postkopia av faktura till | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka e-postkopia av fakturakommentar till | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka e-postkopia till utleverans | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka e-postkopia av försändelsekommentar till | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka e-postkopia till kreditnota | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka e-postkopia av kreditnotskommentar till | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka e-postkopia för plockningsklar till | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Checka ut känsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Försäljning** > **Utcheckning**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Skicka misslyckad e-postkopia till betalning | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Google API-känsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Försäljning** > **Google API**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Behållar-ID | `google/analytics/container_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Leveransmetoder, känsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Försäljning** > **Leveransmetoder**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Gateway-URL | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL för säker gateway | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Titel | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Användar-ID | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Användar-ID | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstlicensnummer | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Spårar XML-URL | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gateg-XML-URL | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Speditörsnummer | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Felsök | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Konto-ID | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Nyckel | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Mätarnummer | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomst-ID | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Felsök | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Kontonummer | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gateway-URL | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Sandlådeläge | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Säljkänsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Försäljning** > **Försäljning**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Kontaktperson | `sales/magento_rma/store_name` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gatuadress | `sales/magento_rma/address` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gatuadress | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Ort | `sales/magento_rma/city` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Stat/provins | `sales/magento_rma/region_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Postnummer | `sales/magento_rma/zip` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Land | `sales/magento_rma/country_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka RMA-postkopia till | `sales_email/magento_rma/copy_to` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka RMA Authorization Email Copy till | `sales_email/magento_rma_auth/copy_to` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka e-postkopia av RMA-kommentar till | `sales_email/magento_rma_comment/copy_to` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka e-postkopia av RMA-kommentar till | `sales_email/magento_rma_customer_comment/copy_to` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Google API-sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Försäljning** > **Google API**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Kontonummer | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Avancerad kategori

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **Lagrar** > Inställningar > **Konfiguration** > **Avancerat**.

### Administratörskänsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Avancerat** > **Admin**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL för anpassad administratör | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Anpassad administratörssökväg | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Systemkänsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Avancerat** > **System**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-postmottagare med fel | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstlista | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postavsändare med fel | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Utvecklarkänsliga och systemspecifika sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Avancerat** > **Utvecklare**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Tillåtna IP-adresser (kommaavgränsade) | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Avancerad kategori

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **Lagrar** > Inställningar > **Konfiguration** > **Avancerat**.

### Systemsökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Avancerat** > **System**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Värd | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Port (25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Serverdelsvärd | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Backend-port | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Utvecklarsökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Avancerat** > **Utvecklare**.

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Logga JS-fel i sessionslagringsnyckeln | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## Betalningskänsliga och systemspecifika sökvägar

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **Lagrar** > Inställningar > **Konfiguration** > **Försäljning** > **Betalning**.

### Allmän variabel

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? |
|--------------|--------------|--------------|--------------|
| Handelsland | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

>[!INFO]
>
>Ditt val för den här variabeln avgör vilka [internationella sökvägar](#international-paths) du kan använda.

### PayPal-känsliga och systemspecifika sökvägar

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-post associerad med PayPal Merchant-konto (valfritt) | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| ID för handelskonto | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Utgivar-ID | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Inloggning | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Värdnamn för anpassad slutpunkt eller IP-adress | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Sandlådeläge | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Felsökningsläge | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Felsökningsläge | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| SFTP-autentiseringsuppgifter | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Pro-känsliga och systemspecifika sökvägar

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Användare | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Egen bana | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Användare | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Partner | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Proxyvärd | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Proxyport | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Felsökningsläge | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| SFTP-autentiseringsuppgifter | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Kreditkortsinställningar | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Link-känsliga och systemspecifika sökvägar

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Användare | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Använd proxy | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Proxyvärd | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Proxyport | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Felsökningsläge | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| URL-metod för Avbryt URL och Retur-URL | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Felsökningsläge | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| SFTP-autentiseringsuppgifter | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro-känsliga och systemspecifika sökvägar

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API-användarnamn | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-lösenord | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-signatur | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-certifikat | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Proxyvärd | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Proxyport | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Sandlådeläge | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| SFTP-autentiseringsuppgifter | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro Hosted sensitive and system-specific paths

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Felsökningsläge | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| SFTP-autentiseringsuppgifter | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### systemspecifika sökvägar som är känsliga för Braintree

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Affärs-ID | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Offentlig nyckel | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Privat nyckel | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| ID för handelskonto | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Kount Merchant ID | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åsidosätt handelsnamn | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Telefon | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Kontrollera/beställ pengar

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Skicka kontroll till | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka kontroll till | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Internationella sökvägar

| Namn | Konfigurationssökväg | Endast Commerce? | Krypterad? | Systemspecifik? | Känslig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Transaktionsnyckel | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL för transaktionsinformation | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_au/cybersource/transaction_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstnyckel | `payment_au/cybersource/access_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Hemlig nyckel | `payment_au/cybersource/secret_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_au/cybersource/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Lösenord för betalningssvar | `payment_au/worldpay/response_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för fjärråtkomst till administratörsauktorisering | `payment_au/worldpay/auth_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Sandlådeläge | `payment_au/eway/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Live API-nyckel | `payment_au/eway/live_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live API-lösenord | `payment_au/eway/live_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan | `payment_au/eway/live_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel för sandlåda | `payment_au/eway/sandbox_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-lösenord för sandlåda | `payment_au/eway/sandbox_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan för sandlådan | `payment_au/eway/sandbox_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL för transaktionsinformation | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_es/cybersource/transaction_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstnyckel | `payment_es/cybersource/access_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Hemlig nyckel | `payment_es/cybersource/secret_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_es/cybersource/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Lösenord för betalningssvar | `payment_es/worldpay/response_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för fjärråtkomst till administratörsauktorisering | `payment_es/worldpay/auth_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| MD5-hemlighet för transaktioner | `payment_es/worldpay/md5_secret` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Felsök | `payment_es/worldpay/debug` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Sandlådeläge | `payment_es/eway/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Live API-nyckel | `payment_es/eway/live_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live API-lösenord | `payment_es/eway/live_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan | `payment_es/eway/live_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel för sandlåda | `payment_es/eway/sandbox_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-lösenord för sandlåda | `payment_es/eway/sandbox_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan för sandlådan | `payment_es/eway/sandbox_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL för transaktionsinformation | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_nz/cybersource/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Testläge | `payment_nz/worldpay/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Sandlådeläge | `payment_nz/eway/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Live API-nyckel | `payment_nz/eway/live_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live API-lösenord | `payment_nz/eway/live_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan | `payment_nz/eway/live_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel för sandlåda | `payment_nz/eway/sandbox_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-lösenord för sandlåda | `payment_nz/eway/sandbox_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan för sandlådan | `payment_nz/eway/sandbox_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Proxyvärd | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Proxyport | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Felsökningsläge | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| URL-metod för Avbryt URL och Retur-URL | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Testläge | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL för transaktionsinformation | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstnyckel | `payment_us/cybersource/access_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Hemlig nyckel | `payment_us/cybersource/secret_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_us/cybersource/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Testläge | `payment_us/worldpay/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Sandlådeläge | `payment_us/eway/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Live API-nyckel | `payment_us/eway/live_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live API-lösenord | `payment_us/eway/live_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan | `payment_us/eway/live_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel för sandlåda | `payment_us/eway/sandbox_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-lösenord för sandlåda | `payment_us/eway/sandbox_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan för sandlådan | `payment_us/eway/sandbox_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Testläge | `payment_gb/cybersource/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Testläge | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL för transaktionsinformation | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_gb/worldpay/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Sandlådeläge | `payment_gb/eway/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Live API-nyckel | `payment_gb/eway/live_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live API-lösenord | `payment_gb/eway/live_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan | `payment_gb/eway/live_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel för sandlåda | `payment_gb/eway/sandbox_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-lösenord för sandlåda | `payment_gb/eway/sandbox_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan för sandlådan | `payment_gb/eway/sandbox_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_de/cybersource/transaction_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstnyckel | `payment_de/cybersource/access_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Hemlig nyckel | `payment_de/cybersource/secret_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_de/cybersource/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Transaktionsnyckel | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL för transaktionsinformation | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för betalningssvar | `payment_de/worldpay/response_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för fjärråtkomst till administratörsauktorisering | `payment_de/worldpay/auth_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Felsök | `payment_de/worldpay/debug` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Sandlådeläge | `payment_de/eway/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Live API-nyckel | `payment_de/eway/live_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live API-lösenord | `payment_de/eway/live_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan | `payment_de/eway/live_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel för sandlåda | `payment_de/eway/sandbox_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-lösenord för sandlåda | `payment_de/eway/sandbox_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan för sandlådan | `payment_de/eway/sandbox_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gateway-URL | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL för transaktionsinformation | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Transaktionsnyckel | `payment_other/cybersource/transaction_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstnyckel | `payment_other/cybersource/access_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Hemlig nyckel | `payment_other/cybersource/secret_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Ny orderstatus | `payment_other/cybersource/order_status` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Testläge | `payment_other/cybersource/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Lösenord för betalningssvar | `payment_other/worldpay/response_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för fjärråtkomst till administratörsauktorisering | `payment_other/worldpay/auth_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_other/worldpay/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Sandlådeläge | `payment_other/eway/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Live API-nyckel | `payment_other/eway/live_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live API-lösenord | `payment_other/eway/live_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan | `payment_other/eway/live_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel för sandlåda | `payment_other/eway/sandbox_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-lösenord för sandlåda | `payment_other/eway/sandbox_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan för sandlådan | `payment_other/eway/sandbox_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL för transaktionsinformation | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_ca/cybersource/transaction_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstnyckel | `payment_ca/cybersource/access_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Hemlig nyckel | `payment_ca/cybersource/secret_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Ny orderstatus | `payment_ca/cybersource/order_status` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Testläge | `payment_ca/cybersource/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Lösenord för betalningssvar | `payment_ca/worldpay/response_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Lösenord för fjärråtkomst till administratörsauktorisering | `payment_ca/worldpay/auth_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_ca/worldpay/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Sandlådeläge | `payment_ca/eway/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Live API-nyckel | `payment_ca/eway/live_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live API-lösenord | `payment_ca/eway/live_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan | `payment_ca/eway/live_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel för sandlåda | `payment_ca/eway/sandbox_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-lösenord för sandlåda | `payment_ca/eway/sandbox_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan för sandlådan | `payment_ca/eway/sandbox_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL för transaktionsinformation | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_hk/cybersource/transaction_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstnyckel | `payment_hk/cybersource/access_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Hemlig nyckel | `payment_hk/cybersource/secret_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_hk/cybersource/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för betalningssvar | `payment_hk/worldpay/response_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för fjärråtkomst till administratörsauktorisering | `payment_hk/worldpay/auth_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_hk/worldpay/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live API-nyckel | `payment_hk/eway/live_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live API-lösenord | `payment_hk/eway/live_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan | `payment_hk/eway/live_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel för sandlåda | `payment_hk/eway/sandbox_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-lösenord för sandlåda | `payment_hk/eway/sandbox_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan för sandlådan | `payment_hk/eway/sandbox_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL för transaktionsinformation | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_jp/cybersource/transaction_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstnyckel | `payment_jp/cybersource/access_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Hemlig nyckel | `payment_jp/cybersource/secret_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Ny orderstatus | `payment_jp/cybersource/order_status` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Testläge | `payment_jp/cybersource/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Lösenord för betalningssvar | `payment_jp/worldpay/response_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för fjärråtkomst till administratörsauktorisering | `payment_jp/worldpay/auth_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_jp/worldpay/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Sandlådeläge | `payment_jp/eway/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Live API-nyckel | `payment_jp/eway/live_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live API-lösenord | `payment_jp/eway/live_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan | `payment_jp/eway/live_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel för sandlåda | `payment_jp/eway/sandbox_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-lösenord för sandlåda | `payment_jp/eway/sandbox_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan för sandlådan | `payment_jp/eway/sandbox_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL för transaktionsinformation | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_fr/cybersource/transaction_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstnyckel | `payment_fr/cybersource/access_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Hemlig nyckel | `payment_fr/cybersource/secret_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_fr/cybersource/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Lösenord för betalningssvar | `payment_fr/worldpay/response_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för fjärråtkomst till administratörsauktorisering | `payment_fr/worldpay/auth_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_fr/worldpay/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Sandlådeläge | `payment_fr/eway/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Live API-nyckel | `payment_fr/eway/live_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live API-lösenord | `payment_fr/eway/live_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan | `payment_fr/eway/live_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel för sandlåda | `payment_fr/eway/sandbox_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-lösenord för sandlåda | `payment_fr/eway/sandbox_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan för sandlådan | `payment_fr/eway/sandbox_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| URL för transaktionsinformation | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_it/cybersource/transaction_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstnyckel | `payment_it/cybersource/access_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Hemlig nyckel | `payment_it/cybersource/secret_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_it/cybersource/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Lösenord för betalningssvar | `payment_it/worldpay/response_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för fjärråtkomst till administratörsauktorisering | `payment_it/worldpay/auth_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Testläge | `payment_it/worldpay/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Sandlådeläge | `payment_it/eway/sandbox_flag` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | ![Sys-specific](/help/assets/configuration/cloud-env.png) |
| Live API-nyckel | `payment_it/eway/live_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Live API-lösenord | `payment_it/eway/live_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan | `payment_it/eway/live_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel för sandlåda | `payment_it/eway/sandbox_api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-lösenord för sandlåda | `payment_it/eway/sandbox_api_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Krypteringsnyckel på klientsidan för sandlådan | `payment_it/eway/sandbox_encryption_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-nyckel | `fraud_protection/signifyd/api_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-URL | `fraud_protection/signifyd/api_url` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Sys-specific](/help/assets/configuration/cloud-env.png) | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-inloggnings-ID | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postkund | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID för fjärradministratör | `payment_au/worldpay/admin_installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| MD5-hemlighet för transaktioner | `payment_au/worldpay/md5_secret` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka kontroll till | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-inloggnings-ID | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postkund | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Affärs-ID | `payment_es/cybersource/merchant_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_es/cybersource/profile_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID för fjärradministratör | `payment_es/worldpay/admin_installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter |
| SFTP-autentiseringsuppgifter | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-inloggnings-ID | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postkund | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Affärs-ID | `payment_nz/cybersource/merchant_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_nz/cybersource/transaction_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_nz/cybersource/profile_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstnyckel | `payment_nz/cybersource/access_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Hemlig nyckel | `payment_nz/cybersource/secret_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_nz/worldpay/installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för betalningssvar | `payment_nz/worldpay/response_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID för fjärradministratör | `payment_nz/worldpay/admin_installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för fjärråtkomst till administratörsauktorisering | `payment_nz/worldpay/auth_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| MD5-hemlighet för transaktioner | `payment_nz/worldpay/md5_secret` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-inloggnings-ID | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postkund | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Affärs-ID | `payment_us/cybersource/merchant_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_us/cybersource/transaction_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_us/cybersource/profile_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_us/worldpay/installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för betalningssvar | `payment_us/worldpay/response_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID för fjärradministratör | `payment_us/worldpay/admin_installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för fjärråtkomst till administratörsauktorisering | `payment_us/worldpay/auth_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| MD5-hemlighet för transaktioner | `payment_us/worldpay/md5_secret` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka kontroll till | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Affärs-ID | `payment_gb/cybersource/merchant_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_gb/cybersource/transaction_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_gb/cybersource/profile_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Åtkomstnyckel | `payment_gb/cybersource/access_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Hemlig nyckel | `payment_gb/cybersource/secret_key` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-inloggnings-ID | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Transaktionsnyckel | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postkund | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_gb/worldpay/installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för betalningssvar | `payment_gb/worldpay/response_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID för fjärradministratör | `payment_gb/worldpay/admin_installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Lösenord för fjärråtkomst till administratörsauktorisering | `payment_gb/worldpay/auth_password` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gör kontrollen betalbar till | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka kontroll till | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Affärs-ID | `payment_de/cybersource/merchant_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_de/cybersource/profile_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-inloggnings-ID | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postkund | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_de/worldpay/installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Installations-ID för fjärradministratör | `payment_de/worldpay/admin_installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| MD5-hemlighet för transaktioner | `payment_de/worldpay/md5_secret` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gör kontrollen betalbar till | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka kontroll till | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-inloggnings-ID | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Ny orderstatus | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Affärs-ID | `payment_other/cybersource/merchant_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_other/cybersource/profile_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_other/worldpay/installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID för fjärradministratör | `payment_other/worldpay/admin_installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| MD5-hemlighet för transaktioner | `payment_other/worldpay/md5_secret` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gör kontrollen betalbar till | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka kontroll till | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-inloggnings-ID | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Ny orderstatus | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postkund | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Affärs-ID | `payment_ca/cybersource/merchant_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_ca/cybersource/profile_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_ca/worldpay/installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID för fjärradministratör | `payment_ca/worldpay/admin_installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| MD5-hemlighet för transaktioner | `payment_ca/worldpay/md5_secret` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gör kontrollen betalbar till | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka kontroll till | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-inloggnings-ID | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postkund | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Affärs-ID | `payment_hk/cybersource/merchant_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_hk/cybersource/profile_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_hk/worldpay/installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID för fjärradministratör | `payment_hk/worldpay/admin_installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| MD5-hemlighet för transaktioner | `payment_hk/worldpay/md5_secret` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Signaturfält | `payment_hk/worldpay/signature_fields` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gör kontrollen betalbar till | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka kontroll till | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-inloggnings-ID | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postkund | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Affärs-ID | `payment_jp/cybersource/merchant_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_jp/cybersource/profile_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_jp/worldpay/installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) |
| Installations-ID för fjärradministratör | `payment_jp/worldpay/admin_installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| MD5-hemlighet för transaktioner | `payment_jp/worldpay/md5_secret` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Signaturfält | `payment_jp/worldpay/signature_fields` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gör kontrollen betalbar till | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka kontroll till | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-inloggnings-ID | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postkund | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Affärs-ID | `payment_fr/cybersource/merchant_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_fr/cybersource/profile_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_fr/worldpay/installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID för fjärradministratör | `payment_fr/worldpay/admin_installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| MD5-hemlighet för transaktioner | `payment_fr/worldpay/md5_secret` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Signaturfält | `payment_fr/worldpay/signature_fields` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| SFTP-autentiseringsuppgifter | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Gör kontrollen betalbar till | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Skicka kontroll till | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| API-inloggnings-ID | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| E-postkund | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Affärs-ID | `payment_it/cybersource/merchant_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Profil-ID | `payment_it/cybersource/profile_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | ![Krypterad](/help/assets/configuration/cloud-enc.png) | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID | `payment_it/worldpay/installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| Installations-ID för fjärradministratör | `payment_it/worldpay/admin_installation_id` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |
| MD5-hemlighet för transaktioner | `payment_it/worldpay/md5_secret` | ![Endast Commerce](/help/assets/configuration/cloud-ee.png) | | | ![Känslig](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}
