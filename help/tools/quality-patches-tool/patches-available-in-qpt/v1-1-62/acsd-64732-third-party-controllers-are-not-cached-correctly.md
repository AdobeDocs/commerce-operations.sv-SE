---
title: 'ACSD-64732: Externa styrenheter cachelagras inte korrekt med kundsegment'
description: Använd patchen ACSD-64732 för att åtgärda Adobe Commerce-problemet där externa styrenheter inte cachas korrekt med kundsegment.
feature: Cache
role: Admin, Developer
source-git-commit: 047de42098f711036f1f5252d2cbc4a329ebbfb2
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# ACSD-64732: Externa styrenheter cachelagras inte korrekt med kundsegment

Korrigeringen ACSD-64732 åtgärdar ett problem där styrenheter från tredje part inte cachas korrekt med kundsegment. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 har installerats. Korrigerings-ID är ACSD-64732. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Tredjepartsstyrenheter cachas inte korrekt med kundsegment.

<u>Steg som ska återskapas</u>:

1. Gå till den anpassade kontrollenheten (/katalog/kategori/variera).
1. Gå till fliken **[!UICONTROL Network]** och kontrollera värdet för **[!DNL X-Magento-Vary]**.

<u>Förväntade resultat</u>:

Värdet **[!UICONTROL X-Magento-Vary]** ska vara detsamma på den anpassade kontrollenheten.

<u>Faktiska resultat</u>:

Värdet för **[!UICONTROL X-Magento-Vary]** är annorlunda, vilket orsakar cachemissar. Det innebär att den tidigare genererade cachen inte kan användas när du besöker den anpassade kontrollenheten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: Uppgraderingar och korrigeringar > Tillämpa korrigeringar i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
