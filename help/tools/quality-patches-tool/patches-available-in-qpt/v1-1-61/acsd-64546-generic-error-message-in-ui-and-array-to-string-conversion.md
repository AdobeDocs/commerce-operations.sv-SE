---
title: 'ACSD-64546: Allmänt felmeddelande i användargränssnittet och konverteringsundantag för matris till strängkonvertering när UPS-etiketter skapas'
description: Använd patchen ACSD-64546 för att åtgärda Adobe Commerce-problemet där ett generiskt felmeddelande visas i användargränssnittet och när undantag för strängkonvertering loggas när UPS-etiketter skapas. Korrigeringen ser till att rätt fel visas i användargränssnittet och loggarna.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 458371bc-4afe-4675-b090-5797e05c5b88
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-64546: Allmänt felmeddelande i användargränssnittet och *undantag för konvertering från matris till sträng* när UPS-etiketter skapas

Korrigeringen ACSD-64546 åtgärdar ett problem där ett generiskt felmeddelande visas i användargränssnittet och undantaget *Array to string conversion* loggas när UPS-etiketter skapas, vilket säkerställer att rätt fel visas i användargränssnittet och loggarna. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 har installerats. Korrigerings-ID är ACSD-64546. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett generiskt felmeddelande visas i användargränssnittet och undantaget *Array för strängkonvertering* inträffar när UPS-etiketter skapas.

<u>Steg som ska återskapas</u>:

1. Skapa ett kundkonto med en giltig adress.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL GENERAL]** > **[!UICONTROL General]** > **[!UICONTROL Store Information]** och lägg till en giltig adress.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Shipping settings]** > **[!UICONTROL Origin]** och lägg till en giltig adress.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Delivery methods]** > **[!UICONTROL UPS]** och konfigurera UPS.
1. Placera en order med [!UICONTROL UPS].
1. Ta bort användar-ID och lösenord för UPS från `core_config_data` i databasen.
1. Rensa konfigurationscachen.
1. Öppna den skapade ordern i **[!UICONTROL Admin]**.
1. Skapa en ny leverans.
   1. Markera kryssrutan **[!UICONTROL Create Shipping Label]**.
   1. Klicka på **[!UICONTROL Submit shipment]**.
   1. Lägg till produkten i ett paket. Ange paketstorleken (längd, bredd och höjd).
   1. Klicka på **[!UICONTROL Save]**.

<u>Förväntade resultat</u>:

Det faktiska felmeddelandet visas i användargränssnittet och i loggarna.

<u>Faktiska resultat</u>:

* Följande fel visas i användargränssnittet:
  *Ett fel uppstod när en leveransetikett skapades.*
* Undantaget *Array till strängkonvertering* förhindrar att det faktiska felmeddelandet visas eller lagras i loggarna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:
* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: Uppgraderingar och korrigeringar > Tillämpa korrigeringar i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:
* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
