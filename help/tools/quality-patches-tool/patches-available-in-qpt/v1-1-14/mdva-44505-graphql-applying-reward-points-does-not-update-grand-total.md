---
title: 'MDVA-44505: GraphQL-fråga för kundvagnstillämpande belöningspunkter uppdaterar inte totalsumman'
description: MDVA-44505-korrigeringen löser problemet där GraphQL-frågan för en kundvagn som tillämpar belöningspoäng inte tar hänsyn till belöningspoängen och returnerar ett felaktigt totalbelopp. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 är installerat. Patch-ID:t är MDVA-44505. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
exl-id: 543698d8-8963-4bf7-af82-11c2498e882e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-44505: GraphQL-fråga för kundvagnstillämpande belöningspunkter uppdaterar inte totalsumman

MDVA-44505-korrigeringen löser problemet där GraphQL-frågan för en kundvagn som tillämpar belöningspoäng inte tar hänsyn till belöningspoängen och returnerar ett felaktigt totalbelopp. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 är installerat. Patch-ID:t är MDVA-44505. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

I GraphQL-frågan för en kundvagn som tillämpar belöningspoäng tas inga hänsyn till belöningspoängen och en felaktig totalsumma returneras.

<u>Steg som ska återskapas</u>:

1. Konfigurera belöningspoäng.
1. Skapa en kundvagn och använd några belöningspoäng.
1. Anropa frågan `GetCart` från slutpunkten `GraphQL` och hämta kundvagnen:

   ```GraphQL
   query {
     cart(cart_id: "{CART_ID}") {
       prices {
         discounts {
           amount {
             value
           }
         }
         grand_total {
           value
         }
       }
     }
   }
   ```

1. Kontrollera totalposten.
1. Kontrollera kundens kundvagnssumma med hjälp av rest-API (`/rest/V1/carts/mine/totals`).

<u>Förväntade resultat</u>:

GraphQL-frågan för kundvagnen returnerar den korrekta totalsumman som tar hänsyn till belöningspoängen.

<u>Faktiska resultat</u>:

GraphQL-frågan tar inte hänsyn till belöningspoängen och returnerar en felaktig totalsumma.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
