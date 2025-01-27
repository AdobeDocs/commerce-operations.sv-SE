---
title: 'ACSD-63182: Ett fel uppstod när en produkt sparades efter duplicering av paketprodukt'
description: Använd patchen ACSD-63182 för att åtgärda Adobe Commerce-problemet om ett fel inträffar när en produkt sparas efter att en paketprodukt har duplicerats med MSI aktiverat.
feature: Inventory, Catalog Management
Role: Admin, Developer
source-git-commit: e532323a743512f0fdd12b6ba30d1c56e8e37e20
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# ACSD-63182: Ett fel uppstod när en produkt sparades efter duplicering av paketprodukt

Korrigeringen ACSD-63182 åtgärdar ett problem där en enkel produkt som används som paketalternativ inte kunde sparas efter dupliceringen av paketprodukten. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 har installerats. Korrigerings-ID är ACSD-63182. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel inträffar när en enkel produkt som används som paketalternativ sparas efter att paketprodukten har duplicerats.

<u>Steg som ska återskapas</u>:

1. Skapa en ny MSI-källa och ett nytt lager.
1. Skapa två enkla produkter: **p1** och **p2**.
1. Skapa en paketprodukt **b1** med **p1** och **p2** som paketerade alternativ.
1. Redigera **paketprodukten b1** och klicka på ***[!UICONTROL Save and Duplicate]***.
1. Redigera den **enkla produkten p1** och klicka på **[!UICONTROL Save]**.

<u>Förväntade resultat</u>:

Produkten sparas utan fel.

<u>Faktiska resultat</u>:

Följande fel visas:
*Undantag: Det finns redan ett objekt (Magento\Catalog\Model\Product\Interceptor) med samma ID, &quot;XXX&quot;.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
