---
title: 'ACSD-57477: Bearbetning av försäljningsregler gör att prestanda försämras vid kundrelaterade begäranden'
description: Använd korrigeringsfilen ACSD-57477 för att åtgärda Adobe Commerce-problemet där Commerce försöker läsa in alla dessa produktattribut när en åtgärd av typen AddProductsToCart körs med variabler i ett projekt med många tillgängliga produktattribut (till exempel 1000 attribut) och orsakar långsamma prestandaproblem i GraphQL-åtgärden AddProductsToCart.
feature: GraphQL, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 00fce49fbe5432a16324937e0430a08ec7c41188
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACSD-57477: Bearbetning av försäljningsregler gör att prestanda försämras vid kundrelaterade begäranden

Korrigeringen ACSD-57477 åtgärdar ett problem där bearbetning av försäljningsregler orsakar långsamma prestanda för kundvagnsrelaterade begäranden. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Patch-ID:t är ACSD-57477. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Bearbetning av försäljningsregel orsakar långsamma prestanda för kundvagnsrelaterade begäranden om du skickar parametrarna som GraphQL-variabler.

<u>Steg som ska återskapas</u>:

1. Lägg till 1 000 produktattribut.
1. Skapa en kundvagn med hjälp av GraphQL nedan.

   ```
   mutation {createEmptyCart}{noformat}
   ```

1. Lägg en produkt i kundvagnen med hjälp av GraphQL nedan.

   ```
   mutation AddProductsToCart($cartId: String!, $products: [CartItemInput!]!) {
       addProductsToCart(cartId: $cartId, cartItems: $products) {
         cart {
           id
           __typename
         }
         __typename
       }
     }
   ```

1. Ange dessa variabler.

   ```
   {
     "cartId": "id_here",
     "products": [
       {
         "sku": "product_dynamic_1",
         "parent_sku": "product_dynamic_1",
         "quantity": 1
       }
     ]
   }
   ```

1. Problemet uppstår bara när du skickar parametrarna som GraphQL-variabler. Om du inkluderar parametrarna i själva GraphQL-frågan uppstår inte detta problem.
1. Skicka samma **Lägg till i kundvagn**-förfrågan när du har lagt till parametrar i själva GraphQL-frågan.

   ```
   mutation {
    addProductsToCart(
      cartId: "id_here"
      cartItems:  [
       {
         sku: "product_dynamic_1",
         parent_sku: "product_dynamic_1",
         quantity: 1
       }
     ]
    ) {
      cart {
           id
           __typename
         }
         __typename
    }
   }
   ```

<u>Förväntade resultat</u>:

`AddProductsToCart` GraphQL-åtgärdsprestanda bör inte försämras.

<u>Faktiska resultat</u>:

Operationsprestanda för `AddProductsToCart` GraphQL försämras eftersom alla produktattribut läses in när parametrar skickas som variabler.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool]
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden för Commerce om molninfrastruktur

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken
