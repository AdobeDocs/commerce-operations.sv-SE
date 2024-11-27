---
title: 'ACSD-61667: Förbättrar lagerprestanda för att skapa frakt'
description: Använd patchen ACSD-60584 för att förbättra lagrets prestanda när det gäller att skapa leveranser i många källor med upphämtning i butiken.
feature: Customers, Shipping/Delivery
role: Admin, Developer
source-git-commit: 29748a439992c0e3efbbc84c5ab9c8239f460b73
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-61667: Förbättrar lagerprestanda för leverans

Korrigeringen ACSD-61667 åtgärdar ett problem där handlaren inte kan leverera ordern när [[!DNL Inventory Management for Commerce]](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction)-hämtningsarkivet (tidigare MSI) har aktiverats med flera källor. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 har installerats. Korrigerings-ID är ACSD-61667. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Du kan inte skicka beställningen när MSI-upphämtningsarkivet är aktiverat, med flera källor. Den här korrigeringen förbättrar lagerprestanda så att frakt kan skapas om många källor har hämtats i butiken.

<u>Krav:</u>:

Adobe Commerce Inventory-modulerna är installerade och aktiverade.

<u>Steg som ska återskapas</u>:

1. Skapa fler än *10* källor och aktivera deras hämtningsplatser.
1. Hämtningsarkivet är aktiverat under **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Skapa ett stort antal hämtningsorder.
1. Gå till **[!UICONTROL Admin login]** och välj **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL View]**.
1. Filtrera och sök efter väntande order.
1. Klicka på **[!UICONTROL Ship]**.

<u>Förväntade resultat</u>:

Leveranssidan läses in som förväntat.

<u>Faktiska resultat</u>:

Du får ett *503-fel om maximal körningstid*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.

