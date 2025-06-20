---
title: 'ACSD-54776: Omarkerade [!UICONTROL Use Default Value] och icke-standardvärden för produktfält sparas inte för den andra webbplatsen, butiken och butiksvyn'
description: Använd korrigeringsfilen ACSD-54776 för att åtgärda Adobe Commerce-problemet där värdena för omarkerade [!UICONTROL Use Default Value] och icke-standardproduktfält inte sparas för den andra webbplatsen, butiken och butiksvyn.
feature: Products
role: Admin, Developer
exl-id: d9f63abb-5d00-4777-a186-1120344af018
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-54776: Omarkerade *[!UICONTROL Use Default Value]* och icke-standardvärden för produktfält sparas inte

>[!NOTE]
>
>Den här korrigeringen ersätter korrigeringen [ACSD-51984](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) som släpptes i QPT 1.1.35.

Korrigeringen ACSD-54776 åtgärdar ett problem där de omarkerade **[!UICONTROL Use Default Value]** och icke-standardvärdena för produktfält inte sparas för den andra webbplatsen, butiken och butiksvyn. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39 är installerad. Patch-ID:t är ACSD-54776. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p4, 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Avmarkerade *[!UICONTROL Use Default Value]* och icke-standardvärden för produktfält sparas inte för den andra webbplatsen, butiken och butiksvyn.

<u>Steg som ska återskapas</u>:

1. Gå till serverdelen och navigera till **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** och skapa en ny webbplats-, butiks- och butiksvy.
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, skapa en enkel produkt, spara den och tilldela produkten till båda webbplatserna från **[!UICONTROL Product in Websites]**.
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
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool]-handboken.
