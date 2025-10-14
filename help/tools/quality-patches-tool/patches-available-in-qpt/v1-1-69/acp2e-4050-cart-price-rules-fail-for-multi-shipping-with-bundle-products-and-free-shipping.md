---
title: 'ACP2E-4050: [!UICONTROL Free Shipping] används inte med utcheckning för flera leveranser'
description: Använd korrigeringsfilen ACP2E-4050 för att åtgärda Adobe Commerce-problemet där [!UICONTROL Free Shipping] inte tillämpas vid utcheckning av flera adresser när [!UICONTROL Cart Price Rules] innehåller delvillkor och produkter med specifika priser.
feature: Shopping Cart, Shipping/Delivery
role: Admin, Developer
type: Troubleshooting
source-git-commit: d36ce39fcd897261b784d57f8806b3eceb66fc01
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# ACP2E-4050: **[!UICONTROL Free Shipping]** används inte med utcheckning för flera leveranser

Korrigeringen för ACP2E-4050 åtgärdar ett problem där **[!UICONTROL Free Shipping]** inte tillämpas vid utcheckning av flera leveranser när **[!UICONTROL Cart Price Rules]** innehåller delvillkor och produkter med specifika priser. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACP2E-4050. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p10

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

**[!UICONTROL Free Shipping]** används inte vid utcheckning av flera leveranser när **[!UICONTROL Cart Price Rules]** innehåller villkor för delurval och produkter med specifika priser.

<u>Steg som ska återskapas</u>:

1. Skapa ett kundkonto med två adresser.
1. Aktivera **[!UICONTROL Free Shipping]** och ange **[!UICONTROL Minimum Order Amount]** till *999999*.
1. Navigera till [!UICONTROL Admin] > [!UICONTROL Marketing] > [!UICONTROL Cart Price Rules] och skapa en kundprisregel med följande villkor:

```
If ALL of these conditions are TRUE:
 * Subtotal is at least 50
 * The subtotal is at most 500
 * Apply this condition if the total amount is 50 or more for a subset of cart items that meet all specified criteria:
 * Category is 23
```

1. Installera exempeldata.
1. Lägg följande produkter i vagnen i angiven ordning:
   * Wayfarer Messenger Bag
   * Olivia 1/4 Zip Light Jacket
   * Sprite Yoga Companion Kit.
1. Öppna kundvagnen och kontrollera att alternativet **[!UICONTROL Free Shipping]** är tillgängligt.
1. Klicka på **[!UICONTROL Check Out with Multiple Addresses]**.
1. Välj en annan leveransadress för den enkla produkten.
1. Klicka på **[!UICONTROL Go to Shipping Information]**.

<u>Förväntade resultat</u>:

**[!UICONTROL Free Shipping]** gäller för konfigurerbara och paketerade produktleveranser.

<u>Faktiska resultat</u>:

**[!UICONTROL Free Shipping]** är inte tillgänglig.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
