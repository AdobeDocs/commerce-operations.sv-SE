---
title: 'ACSD-51497: Det går inte att sortera katalogsidan efter ett anpassat attribut av typen Listruta'
description: Använd patchen ACSD-51497 för att åtgärda Adobe Commerce-problemet där en kund inte kan sortera en katalogsida efter anpassade attribut av typen listruta.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-51497: Det går inte att sortera katalogsidan efter ett anpassat attribut av typen *Listruta*

Korrigeringen ACSD-51497 åtgärdar ett problem där en kund inte kan sortera en katalogsida efter ett anpassat attribut av typen *Listruta*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 är installerad. Korrigerings-ID är ACSD-51497. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En kund kan inte sortera en katalogsida efter ett anpassat attribut av typen *Listruta*.

<u>Steg som ska återskapas</u>

1. Skapa sex enkla produkter och tilldela dem till en enda kategori.
1. Skapa ett produktattribut om du vill lägga till det som ett sorteringsalternativ på listsidorna.

   * Gå till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * Ange följande på fliken **[!UICONTROL Properties]**:

      * *[!UICONTROL Default Label]* = *test*
      * *[!UICONTROL Catalog Input Type]* för butiksägare = *Listruta*
      * *[!UICONTROL Options]*:

         * *först*
         * *sekund*
         * *tredje*
         * *fjärde*

   * Ange följande på fliken **[!UICONTROL Storefront Properties]**:

      * *[!UICONTROL Used for sorting in product listing]* = *Ja*
      * Lämna alla andra alternativ som *Standard*.

1. Tilldela attributet *test* till attributet *Default* som anges i **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Konfigurera produkterna så att attributvärden för *test* finns.

   * SKU: s00001, test: fjärde
   * SKU: s00002, test: third
   * SKU: s00003, test: sekund
   * SKU: s00004, test: first
   * SKU: s00005, test: fjärde
   * SKU: s00006, test: third

1. Indexera om och rensa cache.
1. Gå till kategorin i butiken.
1. Sortera efter attributet *test*.

<u>Förväntade resultat</u>:

Produkterna sorteras efter attributet *test*.

<u>Faktiska resultat</u>:

Produkterna sorteras inte av attributet *test*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
