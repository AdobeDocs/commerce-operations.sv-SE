---
title: 'ACSD-63520: Bilder som överförs via konfiguration för bildöverföring överskrider de konfigurerade storleksgränserna'
description: Använd patchen ACSD-63520 för att åtgärda Adobe Commerce-problemet där bilder som överförts via konfigurationen för bildöverföring på Admin-panelen inte följer de konfigurerade maxgränserna för överföringsstorlek.
feature: Media, Products
role: Admin, Developer
exl-id: 5132bfa9-813a-4623-8e02-a8801f6396e8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-63520: Bilder som överförts via [!UICONTROL Image Upload Configuration] överskrider de konfigurerade storleksgränserna

Korrigeringen ACSD-63520 åtgärdar ett problem där bilder som överförts via [!UICONTROL Images Upload Configuration] inte följer de konfigurerade maxgränserna för överföringsstorlek. Du kan åtgärda detta genom att konfigurera inställningarna för [!UICONTROL Images Upload Configuration] på panelen [!UICONTROL Admin]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 har installerats. Korrigerings-ID är ACSD-63520. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.7

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din [!DNL Adobe Commerce]-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Bilder som överförs via [!UICONTROL Images Upload Configuration] på panelen [!UICONTROL Admin] uppfyller inte den maximala överföringsstorleksgränsen.

<u>Steg som ska återskapas</u>:

1. Logga in på panelen **[!UICONTROL Admin]**.
1. Navigera till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Images Upload Configuration]** och ange:
   * Kvalitet: 100
   * Aktivera storleksändring av sidslut: Ja
   * Maximal bredd: 800
   * Maximal höjd: 600
1. Expandera **[!UICONTROL Media Gallery Image Optimization]** och ange:
   * Aktivera bildoptimering: Ja
   * Maximal bredd: 1 000
   * Maximal höjd: 1 000
1. Navigera till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Configurable Product]**.
   1. Lägg till **[!UICONTROL Product Name]**, **[!UICONTROL SKU]** och **[!UICONTROL Price]**.
   1. Klicka på **[!UICONTROL Create Configurations]**, markera **[!UICONTROL Attributes]** och klicka på **[!UICONTROL Next]**.
   1. Välj storlekar (S, M, L, XL) och klicka på **[!UICONTROL Next]**.
   1. Välj **[!UICONTROL Apply single set of images to all SKUs]** under **[!UICONTROL Images]**.
   1. Ladda upp en bild (minst 1 024 × 1 024) och klicka på **[!UICONTROL Next]**.
   1. Klicka på **[!UICONTROL Generate Product]**.
1. Klicka på **[!UICONTROL Save]**.

<u>Förväntade resultat</u>:

Bilderna ska följa den konfigurerade storleken på uppladdningen och storleksändringen.

<u>Faktiska resultat</u>:

Storleken på bilderna ändras inte och de konfigurerade storleksgränserna för överföring överskrids.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
