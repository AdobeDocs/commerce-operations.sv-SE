---
title: 'MDVA-42768: GraphQL visar fel pris när underordnade produkter inte finns i lager'
description: MDVA-42768-korrigeringen åtgärdar ett problem där GraphQL visar fel pris när de underordnade produkterna i en konfigurerbar produkt inte finns i lager. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 är installerat. Patch-ID:t är MDVA-42768. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: GraphQL, Orders, Products
role: Admin
exl-id: 9f6ab418-2267-4548-952a-17dc8295f632
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-42768: GraphQL visar fel pris när underordnade produkter inte finns i lager

MDVA-42768-korrigeringen åtgärdar ett problem där GraphQL visar fel pris när de underordnade produkterna i en konfigurerbar produkt inte finns i lager. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 är installerat. Patch-ID:t är MDVA-42768. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När de underordnade produkterna för en konfigurerbar produkt inte finns i lager och inställningen Visa utanför Stock-produkter är aktiverad, visas produktens ordinarie pris som **0** i GraphQL-frågan.

<u>Förutsättningar</u>:

Exempeldata har installerats.

<u>Steg som ska återskapas</u>:

1. Aktivera produktinställningen Visa utanför Stock i Commerce Admin genom att gå till **Lager** > **Konfiguration** > **Katalog** > **Lager**.
1. Skapa en konfigurerbar produkt och tilldela den en enkel underordnad produkt.
1. Ställ in lagervärdet för variantprodukten (enkel) till **Utanför lager**.
1. Indexera om.
1. Kör följande GraphQL-fråga:

   ```GraphQL
   query {
     products(filter: { sku: { eq: "MH01" } }) {
       items {
         sku
         price_range {
           minimum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
           maximum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
         }
       }
     }
   }
   ```

1. Kontrollera svarsavsnittet `minimum_price` > `regular price`.

<u>Förväntade resultat</u>:

Det lägsta ordinarie priset visas inte som 0 som svar.

<u>Faktiska resultat</u>:

Det lägsta ordinarie priset = 0 som svar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
