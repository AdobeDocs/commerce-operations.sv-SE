---
title: 'ACSD-66179: Om du avbryter en faktura med betalningstypen [!UICONTROL Not Capture] uppstår en 404-felsida'
description: Använd korrigeringsfilen ACSD-66179 för att korrigera Adobe Commerce-problemet där annullering av en faktura med betalningstypen [!UICONTROL Not Capture] ledde till en felsida på 404.
feature: Orders, Payments
role: Admin, Developer
type: Troubleshooting
source-git-commit: 02a446114be0f9c1ff8d4532cb13a94f1ef64ed2
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# ACSD-66179: Om du avbryter en faktura med betalningstypen [!UICONTROL Not Capture] uppstår en 404-felsida

Korrigeringen ACSD-66179 åtgärdar ett problem där en annullering av en faktura som skapats med betalningstypen *[!UICONTROL Not Capture]* resulterade i en 404-felsida. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 har installerats. Korrigerings-ID är ACSD-66179. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p11 - 2.4.4-p14, 2.4.5-p10 - 2.4.5-p13, 2.4.6-p8 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du avbryter en faktura som skapats med betalningstypen *[!UICONTROL Not Capture]* uppstår en felsida på 404.

<u>Steg som ska återskapas</u>:

1. Skapa en order med en betalningsmetod som PayPal Express Checkout.
1. Skapa en faktura. Ange **[!UICONTROL Amount]** till *[!UICONTROL Not Capture]* och skicka fakturan.
1. Öppna den skapade fakturan och välj **[!UICONTROL Cancel]**.

<u>Förväntade resultat</u>:

1. Fakturan har annullerats.
1. Ett meddelande om att det lyckades visas: *Du avbröt fakturan.*

<u>Faktiska resultat</u>:

En 404-felsida visas: *Sidan hittades inte.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
