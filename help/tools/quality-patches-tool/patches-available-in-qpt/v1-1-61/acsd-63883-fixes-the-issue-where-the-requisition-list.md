---
title: 'ACSD-63883: Korrigerar felaktigt "items_count" i  [!DNL GraphQL] svar för [!UICONTROL Requisition List]'
description: Använd ACSD-63883-korrigeringen för att åtgärda problemet där [!UICONTROL Requisition List] returnerar ett felaktigt "items_count" i  [!DNL GraphQL] svaret.
feature: B2B, GraphQL
role: Admin, Developer
exl-id: 8946d7fb-558a-4867-a843-a61715416f25
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# ACSD-63883: Korrigerar felaktigt `items_count` i [!DNL GraphQL]-svar för [!UICONTROL Requisition List]

ACSD-63883-korrigeringen åtgärdar ett problem där **[!UICONTROL Requisition List]** returnerar ett felaktigt `items_count` i [!DNL GraphQL]-svaret. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 har installerats. Korrigerings-ID är ACSD-63883. Observera att problemet är planerat att åtgärdas i Adobe Commerce B2B 1.5.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

**[!UICONTROL Requisition List]** returnerar ett felaktigt `items_count` i [!DNL GraphQL]-svaret.


<u>Steg som ska återskapas</u>:

1. Aktivera funktionen B2B **[!UICONTROL Requisition List]**.
1. Skapa några produkter.
1. Skapa ett kundkonto.
1. Klicka på **[!UICONTROL Create new Requisition List]**.
1. Skicka mutationsbegäran `addProductsToRequisitionList` [!DNL GraphQL] med en produkt för att lägga till den i [!UICONTROL Requisition List].

   ```
   mutation addProductsToRequisitionList(
   $requisitionListUid: ID!
   $requisitionListItems: [RequisitionListItemsInput!]!
   ) {
   addProductsToRequisitionList(
   requisitionListUid: $requisitionListUid
   requisitionListItems: $requisitionListItems
   ) {
   requisition_list
   { uid name description items_count }
   }
   }
   ```

1. Skicka `addProductsToRequisitionList` [!DNL GraphQL]-mutationsbegäran med tre andra produkter för att lägga till dem i [!UICONTROL Requisition List].
1. Kontrollera `items_count` i svaret.

**Förväntade resultat**:

* `items_count`: 4 ska returneras i svaret.

**Faktiska resultat**:

* `items_count`: 2 returneras i svaret.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
