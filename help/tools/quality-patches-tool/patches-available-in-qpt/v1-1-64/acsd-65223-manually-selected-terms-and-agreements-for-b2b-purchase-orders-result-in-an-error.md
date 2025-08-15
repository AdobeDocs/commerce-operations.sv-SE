---
title: 'ACSD-65223: Manuellt valda villkor och avtal för B2B-inköpsorder resulterar i ett fel'
description: Använd korrigeringsfilen ACSD-65223 för att åtgärda Adobe Commerce-problemet där beställningar som skapats med [!UICONTROL Purchase Orders] inte kan slutföras med onlinebetalningsmetoder som kreditkort när villkor krävs för utcheckning.
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 5a5d0774-3801-4688-86bd-58a390394cc0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-65223: Manuellt valda villkor och avtal för B2B-inköpsorder resulterar i ett fel

Korrigeringen ACSD-65223 åtgärdar ett problem där beställningar som skapats med **[!UICONTROL Purchase Orders]** inte kan slutföras med onlinebetalningsmetoder som kreditkort när villkor krävs för utcheckning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 har installerats. Korrigerings-ID är ACSD-65223.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) B2B 1.5.1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) B2B 1.5.1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om villkor krävs för att göra en beställning, och du försöker slutföra en beställning som har skapats med [!UICONTROL Purchase Orders], kan beställningen inte placeras med onlinebetalningsmetoder som kreditkort.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** och välj **[!UICONTROL B2B Features]**.
1. Ange **[!UICONTROL Enable Company]** och **[!UICONTROL Enable Purchase Orders]** som *Ja*.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Terms and Conditions]** och skapa ett nytt villkor. Ange **[!UICONTROL Applied]** till *[!UICONTROL Manually]*.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** och ställ in **[!UICONTROL Enable Terms and Conditions]** på *Ja*.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment Methods]** och konfigurera [!DNL Braintree].
1. Skapa ett företag i butiken.
1. Gå till **[!UICONTROL Customers]** > **[!UICONTROL Companies]** i administratören.
1. Godkänn företaget och tillåt **[!UICONTROL Purchase Orders]**.
1. Logga in på kontot i förgrunden.
1. Lägg en artikel i kundvagnen.
1. Placera en order med **[!UICONTROL Purchase Order]**.
1. Klicka på fliken **[!UICONTROL Purchase Orders]** på kundkontrollpanelen.
1. Skapa en order från den nya inköpsordern. Välj sedan kreditkort som betalningsmetod.
1. Godkänn villkoren.
1. Beställ.

<u>Förväntade resultat</u>:

Du kan göra en beställning med en onlinebetalningsmetod på godkända inköpsorder när villkor krävs för utcheckning.

<u>Faktiska resultat</u>:

Du kan inte göra en beställning med en onlinebetalningsmetod på godkända inköpsorder när villkor krävs för utcheckning.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
