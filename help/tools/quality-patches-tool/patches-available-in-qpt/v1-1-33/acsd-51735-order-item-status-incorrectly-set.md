---
title: 'ACSD-51735: Orderartikelstatus är felaktigt inställd på *[!UICONTROL Ordered]* när produktaktien är 0'
description: Använd patchen ACSD-51735 för att åtgärda Adobe Commerce-problemet där orderartikelstatusen felaktigt är inställd på *[!UICONTROL Ordered]* när produktstocken är 0.
feature: Orders, Products
role: Admin
exl-id: 56c8b58c-819f-46bd-8912-f543f56b66d6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-51735: Orderartikelstatus är felaktigt inställd på *[!UICONTROL Ordered]* när produktlager är 0

ACSD-51735-korrigeringen åtgärdar ett problem där orderartikelns status är felaktigt inställd på *[!UICONTROL Ordered]* när produktlagret är 0. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 är installerad. Korrigerings-ID är ACSD-50895. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Orderartikelstatus är felaktigt inställd på *[!UICONTROL Ordered]* när produktlagret är 0.

<u>Förutsättningar</u>:

* Adobe Commerce Inventory management-moduler (MSI) är installerade.
* Restorder är aktiverade i **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**.

<u>Steg som ska återskapas</u>:

1. Skapa en ny aktie.
1. Skapa en ny källa.
1. Tilldela standardwebbplatsen till den nya Adobe Stock och tilldela den nya källan.
1. Skapa en ny produkt.

   * Ställ in standardkällans kvantitet till 10 och den nya källans kvantitet till 0.

1. Lägg produkten i kundvagnen på butiken.
1. Observera varningsmeddelandet vid utcheckning som anger att produkten kommer från en ny källa.
1. Beställ.
1. Öppna ordern i Admin och kontrollera restorderstatus.

<u>Förväntade resultat</u>:

Ordern visar att Kvantitet 1 är restorder.

<u>Faktiska resultat</u>:

Ordern visar att Kvantitet 1 är beställt, inte är underordnad.

>[!MORELIKETHIS]
>
>[Beställningsobjektets status är felaktigt inställd på *[!UICONTROL Backordered]*](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
