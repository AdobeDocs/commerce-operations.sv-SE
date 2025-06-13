---
title: 'ACSD-51984: Omarkerade [!UICONTROL Use Default Value] och icke-standardvärden för produktfält sparas inte för den andra webbplatsen, butiken och butiksvyn'
description: Använd korrigeringen ACSD-51984 för att åtgärda Adobe Commerce-problemet där värdena för omarkerade [!UICONTROL Use Default Value] och icke-standardproduktfält inte sparas för den andra webbplatsen, butiken och butiksvyn.
feature: Products
role: Admin
exl-id: 51a810fa-d416-4b37-b5bd-66eed9fe4626
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# ACSD-51984: Omarkerade *[!UICONTROL Use Default Value]* och icke-standardvärden för produktfält sparas inte

>[!NOTE]
>
>Den här korrigeringen är inaktuell och har ersatts av korrigeringen [ACSD-54776](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-39/acsd-54776-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) som lades till i QPT-versionen 1.1.39.

Korrigeringen ACSD-51984 åtgärdar ett problem där de omarkerade **[!UICONTROL Use Default Value]** och icke-standardvärdena för produktfält inte sparas för den andra webbplatsen, butiken och butiksvyn. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35 är installerad. Korrigerings-ID är ACSD-51984. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Avmarkerade *[!UICONTROL Use Default Value]* och icke-standardvärden för produktfält sparas inte för den andra webbplatsen, butiken och butiksvyn.

<u>Steg som ska återskapas</u>:

1. Gå till serverdelen och navigera till **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** och skapa en ny webbplats-, butiks- och butiksvy.
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, skapa en enkel produkt och spara den, och tilldela produkten till båda webbplatserna från **[!UICONTROL Product in Websites]**.
1. Ändra omfattningen till den nya butiksvyn från steg 2.
1. Gå till **[!UICONTROL Search Engine Optimization]** och avmarkera kryssrutorna **[!UICONTROL Use Default Value]** för [!UICONTROL Meta Title], [!UICONTROL Meta Keywords] och [!UICONTROL Meta Description].
1. Rensa texten från fälten: *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* och *[!UICONTROL Meta Description]* och klicka på **[!UICONTROL Save]**.
1. Gå till **[!UICONTROL Search Engine Optimization]** igen.

<u>Förväntade resultat</u>

Värdena för fälten och kryssrutorna sparas.

<u>Faktiska resultat</u>

Värdena för fälten och kryssrutorna sparas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE>) i [!DNL Quality Patches Tool]-handboken.
