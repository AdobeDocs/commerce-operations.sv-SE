---
title: 'ACSD-62591: Temat växlar inte när **[!UICONTROL User Agent Rules]** har konfigurerats'
description: Använd korrigeringsfilen ACSD-62591 för att åtgärda Adobe Commerce-problemet där temat inte växlar korrekt när **[!UICONTROL User Agent Rules]** är konfigurerat.
feature: Themes
role: Admin, Developer
exl-id: 7b206b25-8918-40a6-a956-d38d5058d38f
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# ACSD-62591: Temat växlar inte korrekt när [!UICONTROL User Agent Rules] har konfigurerats

Korrigeringen ACSD-62591 åtgärdar ett problem där temat inte växlar korrekt när **[!UICONTROL User Agent Rules]** har konfigurerats. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 är installerad. Korrigerings-ID är ACSD-62591. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Temat växlar inte korrekt när **[!UICONTROL User Agent Rules]** har konfigurerats.

<u>Steg som ska återskapas</u>:

1. Öppna Commerce **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Redigera ett butiksvytema.
1. Ange `/iPhone|iPod|BlackBerry|Palm|Googlebot-Mobile|Mobile|mobile|mobi|Windows Mobile|Safari Mobile|Android|Opera Mini/i` i **[!UICONTROL User Agent Rules]** och välj ett annat tema.
1. Spara ändringar och rensa cacheminnen.
1. Öppna en Adobe Storefront-sida på en mobil enhet.
1. Öppna samma sida från en webbläsare.

<u>Förväntade resultat</u>:

Skrivbordswebbläsaren och den mobila enheten visar sidor med sina respektive teman.

<u>Faktiska resultat</u>:

Skrivbordswebbläsaren visar den cachelagrade sidan med mobiltemat.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.

