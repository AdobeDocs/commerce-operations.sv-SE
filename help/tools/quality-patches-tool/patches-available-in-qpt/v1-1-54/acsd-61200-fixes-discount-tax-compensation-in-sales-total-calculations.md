---
title: 'ACSD-61200: Fast rabattkompensation i totalberäkningar'
description: Använd korrigeringsfilen ACSD-61200 för att åtgärda Adobe Commerce-problemet där *[!UICONTROL Discount Tax Compensation Amount]* och *[!UICONTROL Shipping Discount Tax Compensation Amount]* saknas i summaberäkningarna, vilket ger skillnader mellan försäljningsorderdata och kupongrapportdata.
feature: Reporting, Taxes
role: Admin, Developer
exl-id: eb908827-de29-4b2c-b094-b5db0931cd52
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-61200: Fast rabattkompensation i totalberäkningar

Korrigeringen ACSD-61200 åtgärdar ett problem där *[!UICONTROL Discount Tax Compensation Amount]* och *[!UICONTROL Shipping Discount Tax Compensation Amount]* saknas i beräkningarna *[!UICONTROL Total Amount]* och *[!UICONTROL Total Amount Actual]*, vilket resulterar i avvikelser mellan försäljningsorderdata och kupongrapportdata. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 har installerats. Korrigerings-ID är ACSD-61200. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

- Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

- Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felaktiga data i försäljningsorder och kupongrapport på grund av att *[!UICONTROL Discount Tax Compensation Amount]* och *[!UICONTROL Shipping Discount Tax Compensation Amount]* saknas i summaberäkningar för försäljning.

<u>Steg som ska återskapas</u>:

1. Skapa en [!UICONTROL Tax Zone] och en [!UICONTROL Tax Rule].
1. Ange följande momskonfigurationer:
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. Uppdatera följande visningsinställningar för beställningar, fakturor och kreditnotor:
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. Skapa en [!UICONTROL Cart Price Rule] med en kupong för 10 % rabatt.
1. Slutför en beställning med kupongen och generera en faktura och leverans.
1. Gå till **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Coupons]** och generera en rapport.
1. Jämför data i ordersammanfattningen med rapportens data.

<u>Förväntade resultat</u>:

Beräkningarna *[!UICONTROL Total Amount]* och *[!UICONTROL Total Amount Actual]* innehåller både *[!UICONTROL Discount Tax Compensation Amount]* och *[!UICONTROL Shipping Discount Tax Compensation Amount]*, och matchar ordersammanfattningen med rapportdata.

<u>Faktiska resultat</u>:

Försäljningsorderdata och kupongrapportdata matchar inte eftersom *[!UICONTROL Discount Tax Compensation Amount]* och *[!UICONTROL Shipping Discount Tax Compensation Amount]* saknas i beräkningar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

- Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
- Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

[[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i verktygshandboken.
