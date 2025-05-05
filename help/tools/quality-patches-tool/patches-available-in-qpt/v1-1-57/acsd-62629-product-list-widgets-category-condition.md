---
title: 'ACSD-62629: Produktlistan i widgetar visar felaktiga kategorier'
description: Använd patchen ACSD-62629 för att åtgärda problemet med Adobe Commerce där en produktlista som används i widgetar inte uppfyller kategorivillkoren.
feature: Page Content
role: Admin, Developer
source-git-commit: 6440738bf01a95a2f1e666826685d325bf393249
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-62629: Produktlistan i widgetar visar felaktiga kategorier

Korrigeringen ACSD-62629 åtgärdar ett problem där produktlistan som används i widgetar inte uppfyller kategorivillkoren. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 är installerad. Korrigerings-ID är ACSD-62629. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktlistan som används i widgetar uppfyller inte kategorivillkoret.

<u>Steg som ska återskapas</u>:

1. Skapa en [!UICONTROL simple product] med namnet TEST och lägg till den i kategori 1.
1. Skapa en mellanlagringsuppdatering utan slutdatum för TEST-produkten. Vänta tills uppdateringen aktiveras.
1. Skapa en [!UICONTROL configurable product] med namnet TEST 2 med två underordnade produkter och lägg till den i kategori 2.
1. Skapa ytterligare [!UICONTROL simple product] med namnet TEST 5 och lägg till den i kategori 1.
1. Kör en fullständig omindexering.
1. Navigera till **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** och redigera hemsidan.
1. Lägg till en [!UICONTROL Products]-widget med *[!UICONTROL Appearance]* inställd på *[!UICONTROL Product Carousel]* och *[!UICONTROL Category]* inställd på kategori 2. Spara sidan.
1. Gå till förgrunden och öppna hemsidan.

<u>Förväntade resultat</u>:

Endast TEST 2-produkten (konfigurerbar) ska finnas på sidan.

<u>Faktiska resultat</u>:

Både TEST 5 (enkel) och TEST 2 (konfigurerbar) finns på sidan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
