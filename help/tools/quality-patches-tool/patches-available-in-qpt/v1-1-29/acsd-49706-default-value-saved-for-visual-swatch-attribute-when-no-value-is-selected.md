---
title: 'ACSD-49706: Standardvärde har sparats för attributet för visuell färgruta när inget värde har valts'
description: Använd korrigeringsfilen ACSD-49706 för att korrigera Adobe Commerce-problemet där ett standardvärde sparas för ett visuellt färgruteattribut när inget värde har valts.
feature: Admin Workspace, Attributes
role: Admin
exl-id: fa3cb0a1-f898-4826-aa64-efeba1af58a8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-49706: Standardvärde har sparats för attributet för visuell färgruta när inget värde har valts

Korrigeringen ACSD-49706 åtgärdar ett problem där ett standardvärde sparas för ett visuellt färgruteattribut när inget värde har valts. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 är installerad. Korrigerings-ID är ACSD-49706. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett standardvärde sparas för ett visuellt färgruteattribut när inget värde är markerat.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Klicka på **[!UICONTROL Add New Attribute]**.
1. Fyll i fälten.

   * Välj till exempel indatatypen *[!UICONTROL Visual Swatch]* och lägg till flera alternativ (till exempel *Röd*, *Grön*). Se till att du väljer något av dessa alternativ som standard.
   * Klicka på **[!UICONTROL Save Attribute]**.

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Redigera attributuppsättningen *[!UICONTROL Default]*.
1. Flytta *[!UICONTROL New Attribute]* från kolumnen *[!UICONTROL Unassigned Attributes]* till mappen *[!UICONTROL Product Details]* i den mittersta kolumnen.

   * Klicka på **[!UICONTROL Save]**.

1. Skapa en ny produkt med attributuppsättningen *[!UICONTROL Default]*.

   * Lämna *[!UICONTROL New Attribute]* tom och spara den.

1. När du har sparat ett värde visas det i *[!UICONTROL New Attribute]*.

<u>Förväntade resultat</u>:

*[!UICONTROL New Attribute]* tilldelas inget värde som standard.

<u>Faktiska resultat</u>:

Ett standardvärde används för attributet när en produkt sparas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
