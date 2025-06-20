---
title: 'ACSD-62118: Tabellen "sales_order_tax_item" har inte uppdaterats fullständigt för B2B-beställningar som gjorts med metoden [!UICONTROL Purchase Order]'
description: Använd patchen ACSD-62118 för att åtgärda Adobe Commerce-problemet där tabellen "sales_order_tax_item" inte uppdateras fullständigt när B2B-beställningar placeras med metoden [!UICONTROL Purchase Order].
feature: Purchase Orders, B2B
role: Admin, Developer
exl-id: 8ace73ad-f5a5-47ab-aca7-62c818775d2f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-62118: Tabellen `sales_order_tax_item` har inte uppdaterats fullständigt för B2B-order som placerats med metoden [!UICONTROL Purchase Order]

Korrigeringen ACSD-62118 åtgärdar ett problem där tabellen `sales_order_tax_item` inte uppdateras fullständigt när en B2B-ordning placeras med metoden *[!UICONTROL Purchase Order]*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 har installerats. Korrigerings-ID är ACSD-62118. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När B2B-order placeras med metoden *[!UICONTROL Purchase Order]* uppdateras inte tabellen `sales_order_tax_item` fullständigt. Det här problemet påverkar skatteberäkningar och orderbearbetning. `applied_taxes`-arrayen är tom när ordningen efterfrågas via API, och både `tax_item_amount` och `tax_item_percent` är NULL.

<u>Steg som ska återskapas</u>:

1. Lägg till momsregler för både **[!UICONTROL Product]** och **[!UICONTROL Shipping]**.
1. Aktivera metoden **[!UICONTROL Purchase Order]** i företagsinställningarna.
1. Logga in som företagsadministratör.
1. Placera en **[!UICONTROL Purchase Order]** med en offlinebetalningsmetod.
1. När [!UICONTROL Purchase Order] har godkänts automatiskt och konverterats till en order kontrollerar du skattedata i tabellen `sales_order_tax_item` och via REST API.

<u>Förväntade resultat</u>:

* Tabellen `sales_order_tax_item` ska innehålla `tax_item` data.
* Arrayen `applied_taxes` ska visa korrekt skatteinformation i API-svaret för inköpsorder, liknande andra betalningsmetoder (t.ex. Check/Pengar Order).

<u>Faktiska resultat</u>:

* Tabellen `sales_order_tax_item` innehåller inga `tax_item`-data.
* `applied_taxes`- och `item_applied_taxes`-arrayerna är tomma i API-svaret för *[!UICONTROL Purchase Order]*.
* Inga skattedata visas när betalningsmetoden *[!UICONTROL Purchase Order]* används.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
