---
title: 'ACSD-50794: Det går inte att ta bort presenter från kundorder via GraphQL'
description: Använd patchen ACSD-50794 för att åtgärda Adobe Commerce-problemet, där användare inte kan ta bort presentförpackningarna från kundordern via GraphQL.
feature: Gift, GraphQL, Orders
role: Admin
exl-id: e088fb18-89d3-47e4-ad02-54068c1ab653
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-50794: Det går inte att ta bort presenter från kundorder via GraphQL

Korrigeringen ACSD-50794 åtgärdar ett problem där användare inte kan ta bort presentförpackningar från kundordern via GraphQL. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32 är installerad. Korrigerings-ID är ACSD-50794. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användare kan inte ta bort presenter från kundorder via GraphQL.

<u>Steg som ska återskapas</u>:

1. Skapa en kund från frontend.
1. Skapa en enkel produkt.
1. Aktivera *[!UICONTROL Gift Messages]* genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** och ange *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*.
1. Skapa *[!UICONTROL Gift Wrapping]* genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. Hämta kundtoken.
1. Skapa en tom kundvagn, customerCart.
   * Lägg till produkter i kundvagnen: `addProductsToCart` mutation
   * Ange faktureringsadress: `setBillingAddressOnCart` mutation
   * Ange leveransadress: `setShippingAddressesOnCart` mutation
   * Ange leveransmetod: `setShippingMethodsOnCart` mutation (flatrate)
   * Ange betalningsmetod: `setPaymentMethodOnCart` mutation (checkmo)
1. Kontrollera nu presentomslutningen *Uid* med den här kundvagnsfrågan:

   ```GraphQL
   {
     cart(cart_id: "{{CART_ID}}") {
       available_gift_wrappings{
           uid
       }
   }
   }
   ```

1. Ange figursättning med `setGiftOptionsOnCart`.
1. Kontrollera kundvagnsfrågan: kundvagn.
1. Frigör presentfigursättning med `setGiftOptionsOnCart` (ange värdet null).
1. Kontrollera återigen kundvagnsfrågan: kundvagn.
1. Monteringsordning: `placeOrder` mutation.
1. Kör kundfråga: kund.

   ```GraphQL
   query {
     customer {
       firstname
       middlename
       lastname
       suffix
       email
       orders {
           items {
               order_date
               gift_wrapping {
                   design
                   uid
               }
           }
       }
       addresses {
         firstname
         middlename
         lastname
         street
         city
         region {
           region_code
           region
         }
         postcode
         country_code
         telephone
       }
     }
   }
   ```

<u>Förväntade resultat</u>:

När en användare har ställt in en presentbrytning och ångrar den returnerar kundfrågan null.

<u>Faktiska resultat</u>:

Kundfrågan returnerar fortfarande presentomslutningen som den används.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
