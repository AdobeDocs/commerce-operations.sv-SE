---
title: 'ACSD-45817: GraphQL-produktmutation ger alla konfigurerbara varianter'
description: Korrigeringen ACSD-45817 åtgärdar ett problem där en GraphQL-mutation för en viss butik returnerar alla konfigurerbara varianter, inklusive de som inte tilldelats den begärda butiken. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 är installerat. Korrigerings-ID är ACSD-45817. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: f00e9a8e-c18b-4fa8-b7c6-c228b6a22a2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-45817: GraphQL-produktmutation ger alla konfigurerbara varianter

Korrigeringen ACSD-45817 åtgärdar ett problem där en GraphQL `products`-mutation för en viss butik returnerar alla konfigurerbara varianter, inklusive de som inte tilldelats den begärda butiken. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 är installerat. Korrigerings-ID är ACSD-45817. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En GraphQL `products`-mutation för en viss butik returnerar alla konfigurerbara varianter, inklusive de som inte har tilldelats den begärda butiken.

<u>Förutsättningar</u>:

Skapa en andra webbplats, en andra butik och en andra butiksvy.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med två underprodukter: &quot;configurable-a&quot; och &quot;configurable-b&quot;.
1. Tilldela den konfigurerbara produkten till båda webbplatserna.
1. Tilldela bara en&quot;konfigurerbar-a&quot;-variant till den andra webbplatsen.
1. Gå till **Storefront**, växla till den andra webbplatsen och öppna den konfigurerbara produkten.
1. Se till att endast ett underordnat alternativ visas: &quot;configurable-a&quot;.
1. Kör en GraphQL-fråga med `POST: /graphql`-slutpunkt och `Headers: "store" = "new"`

   ```GraphQL
   {
     products(filter: { sku: { eq: "configurable" } }) {
       items {
         id
         attribute_set_id
         name
         sku
         __typename
         price_range{
           minimum_price{
             regular_price{
               value
               currency
             }
           }
         }
         categories {
           id
         }
         ... on ConfigurableProduct {
           configurable_options {
             id
             attribute_id_v2
             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
             }
             product_id
           }
           variants {
             product {
               id
               name
               sku
               attribute_set_id
               ... on PhysicalProductInterface {
                 weight
               }
               price_range{
                 minimum_price{
                   regular_price{
                     value
                     currency
                   }
                 }
               }
             }
             attributes {
               uid
               label
               code
               value_index
             }
           }
         }
       }
     }
   }
   ```

<u>Förväntade resultat</u>:

Variationen&quot;configurable-b&quot; är inte tilldelad den andra webbplatsen och ska inte visas i svaret.

<u>Faktiska resultat</u>:

Variationen&quot;configurable-b&quot; visas i svaret.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
