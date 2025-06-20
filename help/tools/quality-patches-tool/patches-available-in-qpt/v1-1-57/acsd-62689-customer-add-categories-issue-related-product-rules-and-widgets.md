---
title: 'ACSD-62689: Det går inte att lägga till kategorier i [!UICONTROL Related Product Rules] och widgetar efter djup 4'
description: Använd korrigeringsfilen ACSD-62689 för att åtgärda Adobe Commerce-problemet, där kunden inte kan lägga till kategorier i [!UICONTROL Related Product Rules] och widgetar efter fyra djupkapslingar.
feature: Categories
role: Admin, Developer
exl-id: 2506744a-01c8-462b-9a27-cd0bdb5664f9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-62689: Det går inte att lägga till kategorier i *[!UICONTROL Related Product Rules]* och widgetar efter djup 4

>[!NOTE]
>
>Den här korrigeringen har ersatts av [ACP2E-3689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3689-issues-with-category-tree-display-reflect-anchor-non-anchor-relationships.md).

Korrigeringen ACSD-62689 åtgärdar ett problem där en kund inte kan lägga till kategorier i *[!UICONTROL Related Product Rules]* och widgetar efter djupet fyra kapslingar. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 är installerad. Korrigerings-ID är ACSD-62689. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En kund kan inte lägga till kategorier i *[!UICONTROL Related Product Rules]* och widgetar efter fyra djupkapslingar.

<u>Steg som ska återskapas</u>:

1. Skapa två kategorier med namnen *[!UICONTROL Anchor]* och *[!UICONTROL Non-Anchor]* under standardrotkategorin.
   * Kontrollera att flaggan *[!UICONTROL Is Anchor]* är inaktiverad för kategorin *[!UICONTROL Non-Anchor]*.
1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Widgets]** och skapa en widget.
1. Under *[!UICONTROL Layout Updates]* väljer du **[!UICONTROL Non-Anchor Categories]** i fältet *[!UICONTROL Display on]*.
1. Klicka på **[!UICONTROL Specific Categories]**.
1. Klicka på kategorivalsikonen.
1. Expandera rotkategorin.
1. Kontrollera kategorierna. Båda ska vara inaktiverade och inte valbara.
1. Under *[!UICONTROL Layout Updates]* väljer du **[!UICONTROL Anchor Categories]** i fältet *[!UICONTROL Display on]*. Följ sedan steg 5 och 6.
1. Kontrollera kategorierna. Båda ska vara aktiverade och valbara.

<u>Förväntade resultat</u>:

I steg 7 bör bara kategorin *[!UICONTROL Non-Anchor]* vara markeringsbar. I steg 9 bör kategorin *[!UICONTROL Anchor]* vara valbar.

<u>Faktiska resultat</u>:

I steg 7 går det inte att markera båda kategorierna. I steg 9 kan båda kategorierna markeras.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.

