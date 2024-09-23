---
title: 'MDVA-41305: Fel i GraphQL Query addProductsToWishlist for Configurable Products'
description: MDVA-41305-korrigeringen löser problemet där användare får ett fel i GraphQL-frågan "addProductsToWishlist" för konfigurerbara produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 är installerat. Korrigerings-ID är MDVA-41305. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-41305: Fel i GraphQL Query addProductsToWishlist för konfigurerbara produkter

MDVA-41305-korrigeringen löser problemet där användare får ett fel i GraphQL-frågan `addProductsToWishlist` om konfigurerbara produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 är installerat. Korrigerings-ID är MDVA-41305. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När användare lägger till konfigurerbara produkter (med/utan konfiguration) i önskelistan av GraphQL, kan de inte få konfigurerbara SKU:er och konfigurerbara alternativ som svar.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt (med blå, grå och ett anpassat alternativ).
1. Öppna frontend; logga in som kund och skapa en önskelista (check önsklist_id).
1. Öppna affischmannen och skapa en kundtoken:

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(email: "", password: "") {
        token
      }
     }
     </code>
     </pre>

1. Ange denna token för auktorisering av Bearer.
1. Försök att lägga till en konfigurerbar produkt, *Blue*, i önskelistan enligt följande:

<pre>
<code class="language-graphql">
mutation {
 addProductsToWishlist(
   wishlistId: 1
   wishlistItems: [
     {
       sku: "conf2"
       selected_options: [
            "Y29uZmlndXJhYmxlLzkzLzUw"
       ]
       quantity: 1
       entered_options: [
         {
           uid: "Y3VzdG9tLW9wdGlvbi8x"
           value: "test"
         }
       ]
     }
    ]
  ) {
    wishlist {
      id
      items_count
      items_v2 (currentPage: 1, pageSize: 8 ) {
        items {
         id
         quantity
         ... on ConfigurableWishlistItem  {
           child_sku
           customizable_options {
             customizable_option_uid
           }
         }
         product {
           uid
           name
           sku
           options_container
           ... on CustomizableProductInterface {
             options {
              title
              required
              sort_order
              option_id
              ... on CustomizableFieldOption {
                value {
                  uid
                  sku
                  price
                  price_type
                  max_characters
                }
              }
            }
          }
          price_range {
            minimum_price {
              regular_price {
                currency
                value
              }
            }
            maximum_price {
               regular_price {
                 currency
                 value
               }
             }
           }
         }
       }
     }
   }
  user_errors {
    code
    message
   }
 }
}
</code>
</pre>

<u>Förväntade resultat</u>:

Användarna kan se en uppsättning konfigurerade produktalternativ i det svar som anges i nyttolasten och som läggs till i önskelistan.

<u>Faktiska resultat</u>:

Användarna får ett *internt serverfel* som svar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
