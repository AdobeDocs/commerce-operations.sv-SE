---
title: 'ACSD-45675: Produktexport använder kategorinamn från standardarkivomfånget'
description: Korrigeringen ACSD-45675 åtgärdar ett problem där produktexporten använder kategorinamn från standardbutiksvyn. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 är installerat. Korrigerings-ID är ACSD-45675. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: ebe72038-511d-43e1-bd65-e5b468342f05
source-git-commit: b1f7739688a538b25b738efc337fa81f15a5bac8
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-45675: Produktexport använder kategorinamn från standardarkivomfånget

Korrigeringen ACSD-45675 åtgärdar ett problem där produktexporten använder kategorinamn från standardbutiksvyn. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 har installerats. Korrigerings-ID är ACSD-45675. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Vid produktexport används kategorinamn från standardomfånget för butiksvyn.

<u>Steg som ska återskapas</u>:

1. Skapa en anpassad butiksvy **[!UICONTROL Thai]** i huvudbutiken.
1. Använd **[!UICONTROL Thai]** som standardbutiksvy för huvudwebbplatsen.
1. Skapa följande kategoristruktur under **[!UICONTROL Default Category]**:

   *[!UICONTROL Default category/Tea/Black]*

1. Markera kategorin **[!UICONTROL Tea]** och ändra **[!UICONTROL Scope]** till **[!UICONTROL Thai]**.
1. Ange **[!UICONTROL Category Name]** som **[!UICONTROL ชาดำ]**.
1. Skapa en enkel produkt **[!UICONTROL SP001]** och tilldela kategorin **[!UICONTROL Black]**.
1. Se till att kronen inte går.
1. Gör en produktexport. Filtrera efter SKU och välj **[!UICONTROL SP001]**.
1. Kontrollera kolumnen **[!UICONTROL categories]** i den exporterade CSV-filen.

<u>Förväntade resultat</u>:

Eftersom ingen butik valdes under exporten bör du hämta en kategorisökväg som följande: *[!UICONTROL Default Category/Tea/Black]*.

<u>Faktiska resultat</u>:

Kategorisökvägen har blandade språk: *[!UICONTROL Default Category/ชาดำ/Black]*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tools] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden för kvalitetspatchar.
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
