---
title: 'ACSD-63578: SKU tas inte bort om du klickar på ikonen [!UICONTROL Delete] i [!UICONTROL Add to Order by SKU]'
description: Använd korrigeringsfilen ACSD-63578 för att åtgärda Adobe Commerce-problemet där du inte tar bort SKU:n genom att klicka på ikonen [!UICONTROL Delete] i [!UICONTROL Add to Order by SKU] i Admin.
feature: Orders
role: Admin, Developer
source-git-commit: 3dc2af76dac1a3ed9fd0e666f1dfdf09077770d2
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# ACSD-63578: SKU tas inte bort om du klickar på ikonen **[!UICONTROL Delete]** i *[!UICONTROL Add to Order by SKU]*

ACSD-63578-korrigeringen åtgärdar ett problem där SKU:n inte tas bort när du klickar på ikonen **[!UICONTROL Delete]** i *[!UICONTROL Add to Order by SKU]* i Admin. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 har installerats. Korrigerings-ID är ACSD-63578. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p7

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du klickar på ikonen **[!UICONTROL Delete]** i *[!UICONTROL Add to Order by SKU]* i Admin tas inte SKU:n bort från ordningen.

<u>Steg som ska återskapas</u>:

1. Navigera till Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** och klicka på **[!UICONTROL Create New Order]**.
1. Välj en kund.
1. Klicka på **[!UICONTROL Add to Order by SKU]**.
   * Ange en SKU.
   * Klicka på knappen **[!UICONTROL Add another]**.
1. Klicka på ikonen **[!UICONTROL Delete]**.

<u>Förväntade resultat</u>:

* Produkter läggs till och tas bort från en beställning i Admin.

<u>Faktiska resultat</u>:

* Ikonen **[!UICONTROL Delete]** fungerar inte.
* Det finns ett fel i konsolen:

  `jquery.js:130 Refused to execute inline script because it violates the following Content Security Policy directive`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
