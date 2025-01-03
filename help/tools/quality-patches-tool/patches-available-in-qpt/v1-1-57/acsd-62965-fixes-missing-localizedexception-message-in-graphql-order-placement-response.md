---
title: 'ACSD-62965: Åtgärdar ett LocalizedException-meddelande som saknas i GraphQL-svar på orderplacering'
description: Använd patchen ACSD-62965 för att åtgärda Adobe Commerce-problem där meddelandet "LocalizedException" inte fanns med i GraphQL svar vid orderplacering.
feature: Orders, GraphQL
role: Admin, Developer
source-git-commit: 8191bf8feda8f8e041ecf83d9ddf5c5119930531
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-62965: Korrigerar saknade `LocalizedException`-meddelanden i GraphQL-svar för orderplacering

ACSD-62965-korrigeringen åtgärdar ett problem där `LocalizedException`-meddelandet inte ingick i GraphQL-svaret vid orderplacering. Den här korrigeringen är tillgänglig med [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. Korrigerings-ID är ACSD-62965. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.7

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL-svaret för orderplacering innehåller inte något `LocalizedException`-meddelande, vilket resulterar i otillräcklig felinformation för felsökning.

<u>Steg som ska återskapas</u>:

1. Installera en ren **[!DNL Adobe Commerce]**-instans.
1. Lägg en produkt i kundvagnen och fortsätt till orderplaceringssteget.
1. Lägg till en `LocalizedException` i `Magento\Framework\Exception\LocalizedException` i `app/code/Magento/QuoteGraphQl/Model/Resolver/PlaceOrder.php`.
1. Infoga undantaget efter följande rad:

   ```
   $cart = $this->getCartForCheckout->execute($maskedCartId, $userId, $storeId);
   ```

   Lägg till undantaget:

   ```
   throw new LocalizedException(new Phrase("Test LocalizedException"));
   ```

1. Gör en beställning från GraphQL:

   ```
   mutation {
   placeOrder(input: {cart_id: "cart_id"}) {
       order {
       order_number
       }
   }
   }
   ```

1. Observera svaret:
   1. Svaret innehåller inte meddelandet `LocalizedException`.
   1. Exempel på felaktigt svar:

      ```
      {
      "data": {
          "placeOrder": {
          "order": null
          }
      }
      }
      ```

<u>Förväntade resultat</u>:

Om `LocalizedException` inträffar bör undantagsmeddelandet inkluderas i GraphQL-svaret för orderplacering för förbättrad felhantering.

<u>Faktiska resultat</u>:

Om `LocalizedException` inträffar, inkluderas inte undantagsmeddelandet i GraphQL-svaret för orderplaceringen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
