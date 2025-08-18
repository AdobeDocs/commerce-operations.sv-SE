---
title: 'AC-15223: Börsidan visar cachelagrat innehåll efter växling av butiker'
description: Använd korrigeringsfilen AC-15223 för att åtgärda Adobe Commerce-problemet där sidan hanteras från cacheminnet efter bytet och butiken inte byts som förväntat.
feature: Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: ea3584e180acad1765f5b8105c45170725c71269
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# AC-15223: Börsidan visar cachelagrat innehåll efter växling av butiker

Korrigeringen AC-15223 åtgärdar ett problem där sidan hanteras från cacheminnet när butiksväxlaren inte fungerar efter växling av butiker. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Patch-ID:t är AC-15223. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Efter växling av butiker hanteras sidan från cacheminnet (butiksväxlaren fungerar inte).

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**.
2. Skapa en ny butiksvy.
3. Gå till butiken och försök växla butiksvyer.

<u>Förväntade resultat</u>:

Butiksvyn har växlats.

<u>Faktiska resultat</u>:

Butiksvyns namn ändras inte i huvudet förrän cachen rensas från serverdelen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
