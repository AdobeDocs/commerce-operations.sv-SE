---
title: 'ACSD-58685: Inaktiverade e-postmeddelanden skickas när återaktivering sker'
description: Använd patchen ACSD-58685 för att åtgärda Adobe Commerce-problemet där e-postmarknadsföring som initieras när e-postkommunikation inaktiveras skickas när e-postkommunikation återaktiveras.
feature: Configuration
role: Admin, Developer
exl-id: 773c0e0e-92c3-42b1-8fbf-fcb05e0e8311
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-58685: Inaktiverade e-postmeddelanden skickas när återaktivering sker

Korrigeringen ACSD-58685 åtgärdar ett problem där e-postmeddelanden som initieras när e-postkommunikation inaktiveras skickas när e-postkommunikation återaktiveras. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 är installerad. Patch-ID:t är ACSD-58685. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

E-postmarknadsföring som initieras medan e-postkommunikation inaktiveras skickas när e-postkommunikation återaktiveras.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Mail Sending Settings]** och ställ in **[!UICONTROL Disable Email Communications]** på *[!UICONTROL No]*.
1. Navigera till **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales Emails]** > **[!UICONTROL General Settings]** och ställ in **[!UICONTROL Asynchronous Sending]** på *[!UICONTROL Yes]*.
1. Rensa konfigurationscachen.
1. Beställ.
1. Aktivera e-postkommunikation.
1. Lägg en ny order.
1. Kör kronen.

<u>Förväntade resultat</u>:

Endast e-postmeddelandet för den andra ordern skickas.

<u>Faktiska resultat</u>:

E-postmeddelanden för både den första och den andra ordern skickas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

[[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
