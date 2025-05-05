---
title: 'ACSD-63974: Korrigerar långsam [!UICONTROL Requisition List] inläsningstid med sidnumrering'
description: Använd ACSD-63974-korrigeringen för att åtgärda problemet där sidan [!UICONTROL Requisition List] tar lång tid att läsa in när det finns för många objekt.
feature: B2B
role: Admin, Developer
source-git-commit: e5f8112b870e3550b4f3a9113be48428a54d454a
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# ACSD-63974: Korrigerar långsam [!UICONTROL Requisition List] inläsningstid med sidnumrering

Korrigeringen ACSD-63974 åtgärdar ett problem där sidan **[!UICONTROL Requisition List]** tar lång tid att läsa in när det finns för många objekt. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 har installerats. The patch ID is ACSD-63974. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det tar lång tid att läsa in sidan **[!UICONTROL Requisition List]** när det finns många objekt (2 000+). Detta beror på att sidnumrering saknas, vilket gör att alla objekt läses in samtidigt.

<u>Steg som ska återskapas</u>:

1. Go to the **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > *[!UICONTROL General]* > **[!UICONTROL B2B features]**.
1. Set **[!UICONTROL Enable Requisition List]** to *Yes*.
1. Generate 2000+ products by editing `simple_products` node in `setup/performance-toolkit/profiles/ce/small.xml`.
1. Run the command:

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Create a customer and log in.
1. Add all products to the **[!UICONTROL Requisition List]**.
1. Visa **[!UICONTROL Requisition List]** på Storefront.


<u>Förväntade resultat</u>:

Sidan ska läsas in inom rimlig tid.


<u>Faktiska resultat</u>:

The Page load time increases with the number of items because all items are loaded at once due to the absence of pagination.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: Uppgraderingar och korrigeringar > Tillämpa korrigeringar i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
