---
title: 'ACSD-62056: Bildöverföring för konfigurerbar produkt misslyckas om MSI är installerat'
description: Använd patchen ACSD-62056 för att åtgärda Adobe Commerce-problemet där bilder för konfigurerbara produkter inte läggs till om MSI är installerat.
feature: Products, Media
role: Admin, Developer
exl-id: bab8e617-d80c-4456-8ade-bdc6b4294d26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# ACSD-62056: Bildöverföring för konfigurerbar produkt misslyckas om MSI är installerat

Korrigeringen ACSD-62056 åtgärdar ett problem där bilder för konfigurerbara produkter inte läggs till om MSI är installerat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 har installerats. Korrigerings-ID är ACSD-62056. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du redigerar en konfigurerbar produkt med [!UICONTROL Inventory Management/MSI] aktiverat fungerar inte alternativen för att lägga till bilder. Detta påverkar både alternativen [!UICONTROL Apply a single set of images to all SKUs] och [!UICONTROL Apply unique images by attribute to each SKU].

<u>Förutsättningar</u>:

[!UICONTROL Inventory Management/MSI] moduler är installerade och aktiverade.

<u>Steg som ska återskapas</u>:

1. Skapa en ny källa.
1. Skapa en ny aktie och tilldela den nya källan.
1. Redigera en konfigurerbar produkt.
1. Klicka på **[!UICONTROL Edit Configurations]** > **[!UICONTROL Next]** > **[!UICONTROL Next]**.
1. Välj något av följande och lägg till en bild.

   * [!UICONTROL Apply a single set of images to all SKUs]
   * [!UICONTROL Apply unique images by attribute to each SKU]

<u>Förväntade resultat</u>:

Bilderna läggs till.

<u>Faktiska resultat</u>:

Bilderna läggs inte till.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
