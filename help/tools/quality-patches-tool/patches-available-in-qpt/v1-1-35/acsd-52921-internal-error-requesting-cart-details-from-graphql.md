---
title: 'ACSD-52921: Fel vid begäran om kundvagnsinformation från GraphQL för produkt som inte finns i lager'
description: Använd patchen ACSD-52921 för att åtgärda Adobe Commerce-problemet när ett internt fel inträffar när kundvagnsinformation begärs från GraphQL för en ej lagrad konfigurerbar produkt.
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 7790718a-6b86-497e-b1a1-88ba22c3e8ff
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-52921: Fel vid begäran om kundvagnsinformation från GraphQL för produkt som inte finns i lager

Korrigeringsfilen ACSD-52921 åtgärdar ett problem där ett internt fel inträffar när kundvagnsinformation begärs från GraphQL för en ej lagrad konfigurerbar produkt. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 har installerats. Korrigerings-ID är ACSD-52921. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett internt fel inträffar när kundvagnsinformation begärs från GraphQL för en produkt som inte är lagrad.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med några alternativ.
1. Lägg till ett alternativ för ovanstående konfigurerbara produkt i kundvagnen från frontend (gästutcheckning).
1. Hämta `[ masked_id ]` från datatabellen `[ quote_id_mask ]` för den offert som skapats ovan.
1. Kör följande GraphQL-fråga för att få information om gästvagnen ovan.

   Lägg till `[ masked_id ]` som tagits emot från steg 3 i frågan.

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. Då returneras offertinformationen utan några problem.
1. Gå till serverdelen och uppdatera den konfigurerbara produktens *[!UICONTROL Stock Status]* till *[!UICONTROL Out of Stock]*.
1. Kör samma GraphQL-fråga som i steg 4.

<u>Förväntade resultat</u>:

Felmeddelandet skickas/behandlas korrekt i svaret.

<u>Faktiska resultat</u>:

*500 Internt serverfel* genereras som svar på GraphQL-frågan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool]
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden för Commerce om molninfrastruktur

## Relaterad läsning

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool]
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
