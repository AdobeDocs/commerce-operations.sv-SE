---
title: 'MDVA-40120: GraphQL product DESC/ASC sort does not work'
description: MDVA-40120-korrigeringen löser problemet där GraphQL sortering efter DESC/ASC inte fungerar med produkter som har samma relevans eller pris. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 är installerat. Korrigerings-ID är MDVA-40120. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: GraphQL, Products
role: Admin
exl-id: 4df7f14d-181b-4f34-aff7-0af823632015
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# MDVA-40120: GraphQL product DESC/ASC sort does not work

MDVA-40120-korrigeringen löser problemet där GraphQL sortering efter DESC/ASC inte fungerar med produkter som har samma relevans eller pris. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 har installerats. Korrigerings-ID är MDVA-40120. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättningar</u>:

Skapa några olika produkter till samma pris.

<u>Steg som ska återskapas</u>:

1. Kör följande GraphQL-fråga:

   ```GraphQL
   {
     products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: ASC}) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Kontrollera svaret.
1. Ändra sorteringsordningen från **ASC** till **DESC** i GraphQL-frågan:

   ```GraphQL
   {
     products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: DESC}) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Kontrollera svaret.

<u>Förväntade resultat</u>:

Produktlistan i GraphQL svar bör ändras i enlighet med sorteringsordningen.

<u>Faktiska resultat</u>:

Sorteringsordningen ändras inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
