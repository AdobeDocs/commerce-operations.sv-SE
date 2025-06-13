---
title: 'ACSD-48234: Katalogsökningen resulterar i felaktigt antal kategoriobjekt när [!UICONTROL Display Out of Stock Products] är aktiverat'
description: Använd patchen ACSD-48234 för att åtgärda Adobe Commerce-problemet där katalogsökningsresultatet visar ett felaktigt antal kategoriobjekt när alternativet [!UICONTROL Display Out of Stock Products] är aktiverat.
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
exl-id: c177f12d-2db5-48e2-8f88-ff589cea4dd4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48234: Katalogsökresultatet visar felaktigt antal kategoriobjekt **[!UICONTROL Display Out of Stock Products]** aktiverat

Korrigeringen ACSD-48234 löser problemet där katalogsökresultatet visar ett felaktigt antal kategoriobjekt när alternativet **[!UICONTROL Display Out of Stock Products]** är aktiverat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 är installerad. Korrigerings-ID är ACSD-48234. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.


## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Katalogsökresultatet visar ett felaktigt antal kategoriobjekt när alternativet **[!UICONTROL Display Out of Stock Products]** är aktiverat.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** och öppna attributet **[!UICONTROL color]**.
1. Lägg till två alternativ, till exempel orange och grönt. Spara attributet.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** och lägg till attributet **[!UICONTROL color]** i attributuppsättningen **[!UICONTROL Default]**.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** och ställ in **[!UICONTROL Display Out of Stock Products]** på _Ja_.
1. Skapa kategorin &quot;cat1&quot;.
1. Skapa två produkter:
   1. Namn: prod1, Color: orange, Categories: cat1.
   1. Namn: prod2, Color: green, Categories: cat1.
1. Öppna katt1-kategorin i butiken.
1. Markera den orangefärgade färgen i lagernavigeringen.

<u>Förväntade resultat</u>:

Endast prod1-produkt visas.

<u>Faktiska resultat</u>:

Både prod1- och prod2-produkter visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
