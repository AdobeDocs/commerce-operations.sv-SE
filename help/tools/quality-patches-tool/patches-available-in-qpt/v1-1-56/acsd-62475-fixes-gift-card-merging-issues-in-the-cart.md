---
title: 'ACSD-62475: Korrigerar problem med att slå ihop presentkort i vagnen'
description: Använd patchen ACSD-62475 för att åtgärda Adobe Commerce-problemet där presentkortsprodukter med olika detaljer felaktigt sammanfogas till en enda radartikel i kundvagnen.
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: fc97c3c0-dc1b-4546-aad0-ef3b4b6a3415
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62475: Korrigerar problem med att slå ihop presentkort i vagnen

Korrigeringen ACSD-62475 åtgärdar ett problem där presentkortsprodukter med olika detaljer felaktigt sammanfogas till en enda radartikel i vagnen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 har installerats. Korrigerings-ID är ACSD-62475. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Presentkortsprodukter som läggs till i vagnen med unika avsändare- eller mottagardetaljer sammanfogas felaktigt till ett enda radobjekt, vilket resulterar i inkonsekvenser i data.

<u>Steg som ska återskapas</u>:

1. Skapa en [!UICONTROL Gift Card]-produkt med följande inställningar:
   * **[!UICONTROL Card Type]**: [!UICONTROL Virtual]
   * **[!UICONTROL Amount]**: 10

1. Skapa en ny användare i butiken och logga in.

1. Lägg presentkortsprodukten i kundvagnen med följande information:
   * **[!UICONTROL Sender Name]**: Avsändare 1
   * **[!UICONTROL Sender Email**]: sender1@test.com
   * **[!UICONTROL Recipient Name**]: Mottagare 1
   * **[!UICONTROL Recipient Email**]: recipient1@test.com


1. Logga ut

1. Lägg samma presentkortsprodukt i kundvagnen med följande information:
   * **[!UICONTROL Sender Name]**: Avsändare 2
   * **[!UICONTROL Sender Email**]: sender2@test.com
   * **[!UICONTROL Recipient Name**]: Mottagare 2
   * **[!UICONTROL Recipient Email**]: recipient2@test.com

1. Logga in igen och kontrollera vagnen.

<u>Förväntade resultat</u>:

Båda presentkorten ska visas som två separata radartiklar med respektive information.

<u>Faktiska resultat</u>:

Presentkorten sammanfogas till en radartikel med en kvantitet på 2, och detaljerna för det första presentkortet behålls.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
