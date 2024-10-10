---
title: 'ACSD-54319: Produktpriset visar noll i *[!UICONTROL Products in Carts]* rapport'
description: Använd korrigeringsfilen ACSD-54319 för att korrigera Adobe Commerce-problemet där produktpriset är noll i *[!UICONTROL Products in Carts]*-rapporten
feature: Reporting, Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-54319: Produktpriset visar noll i rapporten *[!UICONTROL Products in Carts]*

Korrigeringen ACSD-54319 åtgärdar ett problem där produktpriset är noll i *[!UICONTROL Products in Carts]*-rapporten. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 har installerats. Korrigerings-ID är ACSD-54319. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktpriset visar noll i *[!UICONTROL Products in Carts]*-rapporten.

<u>Steg som ska återskapas</u>:

1. Ange **[!UICONTROL Catalog Price Scope]** till **[!UICONTROL Website]** från **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]**.
1. Skapa en andra webbplats från **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Skapa en produkt från **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Tilldela bara den här produkten till den andra webbplatsen.
1. Lägg en produkt i kundvagnen från den andra webbplatsen.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]** rutnät.
1. Kontrollera kolumnen *[!UICONTROL Price]* i rutnätet *[!UICONTROL Products In Carts]*.

<u>Förväntade resultat</u>:

Produktpriset är inte noll i rapportrutnätet *[!UICONTROL Products in Carts]*.

<u>Faktiska resultat</u>:

Produktpriset är noll i rapportrutnätet *[!UICONTROL Products in Carts]*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.