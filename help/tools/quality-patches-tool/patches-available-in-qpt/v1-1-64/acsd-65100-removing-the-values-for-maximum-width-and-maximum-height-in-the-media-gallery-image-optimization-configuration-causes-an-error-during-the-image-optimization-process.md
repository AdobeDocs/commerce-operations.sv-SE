---
title: 'ACSD-65100: Om du tar bort värdena [!UICONTROL Maximum Width] och [!UICONTROL Maximum Height] i konfigurationen [!UICONTROL Media Gallery Image Optimization] uppstår ett fel'
description: Använd korrigeringen ACSD-65100 för att åtgärda Adobe Commerce-problemet där borttagningen av värdena [!UICONTROL Maximum Width] och [!UICONTROL Maximum Height] i konfigurationen [!UICONTROL Media Gallery Image Optimization] orsakar ett fel under bildoptimeringsprocessen.
feature: Media
role: Admin, Developer
source-git-commit: 97ffcd84b760962e1ad7290343f81860ca6568c7
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# ACSD-65100: Om du tar bort värdena [!UICONTROL Maximum Width] och [!UICONTROL Maximum Height] i konfigurationen [!UICONTROL Media Gallery Image Optimization] uppstår ett fel

Korrigeringen ACSD-65100 åtgärdar ett problem där borttagning av värdena **[!UICONTROL Maximum Width]** och **[!UICONTROL Maximum Height]** i konfigurationen **[!UICONTROL Media Gallery Image Optimization]** orsakar ett fel under bildoptimeringsprocessen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 har installerats. Korrigerings-ID är ACSD-65100. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-P5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel inträffar under bildoptimeringsprocessen när värdena för **[!UICONTROL Maximum Width]** och **[!UICONTROL Maximum Height]** tas bort i **[!UICONTROL Media Gallery Image Optimization]**-konfigurationen.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery Image Optimization]**.
1. Ta bort värdena för **[!UICONTROL Maximum Width]** och **[!UICONTROL Maximum Height]**.
1. Rensa konfigurationscachen.
1. Navigera till **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**.
1. Öppna en sida för redigering.
1. I innehållsområdet:
   1. Välj **[!UICONTROL Add Layout]** > **[!UICONTROL Row]**.
   1. Välj **[!UICONTROL Add Elements]** > **[!UICONTROL Text]**.
   1. Klicka på **[!UICONTROL Add Image]** i WYSIWYG Editor.
   1. Överför en bild och välj **[!UICONTROL Add Selected]**.
1. Kontrollera filen `var/log/exception.log`.

<u>Förväntade resultat</u>:

Inga fel.

<u>Faktiska resultat</u>:

Ett fel som liknar följande loggas:

```
report.ERROR: InvalidArgumentException: Invalid image dimensions. in /var/www/html/vendor/magento/framework/Image/Adapter/AbstractAdapter.php:630
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
