---
title: 'ACSD-61133: "sales_clean_quotes" cron raderar citattecken från ej godkända inköpsorder'
description: Använd patchen ACSD-61133 för att åtgärda Adobe Commerce-problemet där "sales_clean_quotes" tar bort citat från ej godkända inköpsorder.
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 06979d4b-08ea-40fe-a211-3d950c9afb47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-61133: `sales_clean_quotes` cron tar bort offerter från ej godkända inköpsorder

Korrigeringen ACSD-61133 åtgärdar ett problem där kron `sales_clean_quotes` tar bort offerter från ej godkända inköpsorder. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.53 har installerats. Korrigerings-ID är ACSD-61133. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4-p5 - 2.4.4-p11, 2.4.5-p4 - 2.4.5-p10 och 2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`sales_clean_quotes` cron tar bort offerter från ej godkända inköpsorder. Det går inte att konvertera *[B2B-inköpsordern]* till den offertordning som är associerad med den köpta ordern eftersom cron tar bort den.

<u>Förutsättningar</u>:

Adobe Commerce [!UICONTROL B2B]-moduler är installerade och aktiverade.

<u>Steg som ska återskapas</u>:

1. Aktivera funktionen *[!UICONTROL B2B Purchase Order]*.
1. Skapa ett företag.
1. Skapa en *[!UICONTROL Purchase Order]*.
1. Vänta tills offerten upphör att gälla och tas bort av kronen. Du kan ange en förfalloperiod för offerten med **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]** > **[!UICONTROL Default Expiration Period configuration]**.
1. Konvertera *[!UICONTROL Purchase Order]* till ordningen via *[!UICONTROL My Purchase Order in Customer Dashboard]* eller med [!DNL GraphQL] `placeOrderForPurchaseOrder`-mutation.

<u>Förväntade resultat</u>:

Offerten som är associerad med den aktiva *[!UICONTROL Purchase Order]* tas inte bort eftersom den har upphört att gälla av cron. Ordern har placerats antingen i butiken eller via [!DNL GraphQL].

<u>Faktiska resultat</u>:

Ordningen placeras inte och ett fel visas i butiken eller returneras i svaret [!DNL GraphQL].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
