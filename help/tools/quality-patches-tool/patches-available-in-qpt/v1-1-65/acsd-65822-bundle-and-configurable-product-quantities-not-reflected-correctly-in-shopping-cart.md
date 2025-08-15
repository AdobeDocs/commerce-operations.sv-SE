---
title: 'ACSD-65822: Paketet och konfigurerbara produktkvantiteter visas inte korrekt i kundvagnen'
description: Använd patchen ACSD-65822 för att åtgärda Adobe Commerce-problemet där kvantiteten var 0 i kundvagnssektionen på adminpanelen när du lägger till paketprodukter.
feature: Admin Workspace, Checkout, Orders
role: Admin, Developer
exl-id: 6740b5a6-8710-458c-abe4-03d2a8a694c5
source-git-commit: 7e9598e3ac0558706ef98ca81c19d27c37f7e860
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-65822: Paketet och konfigurerbara produktkvantiteter visas inte korrekt i [!UICONTROL Shopping Cart]

Korrigeringen ACSD-65822 åtgärdar ett problem där programpaket och konfigurerbara produktkvantiteter inte visas korrekt i avsnittet **[!UICONTROL Shopping Cart]** under *[!UICONTROL Customer's Activities]*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 har installerats. Korrigerings-ID är ACSD-65822. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Paketet och de konfigurerbara produktkvantiteterna visas inte korrekt i avsnittet **[!UICONTROL Shopping Cart]** under *[!UICONTROL Customer's Activities]*.

<u>Steg som ska återskapas</u>:

1. Skapa en användare i butiken.
2. Skapa en **[!UICONTROL Bundle product]** på administratörspanelen.
3. Som inloggad användare i butiken lägger du till paketprodukten i kundvagnen med en angiven kvantitet.
4. Gå till *på panelen* Admin **[!UICONTROL Customers]** och klicka på **[!UICONTROL Edit]** för den kund som skapades i steg 1.
5. Klicka på **[!UICONTROL Create Order]**.
6. Till vänster, under *[!UICONTROL Customer's Activities]*, kontrollerar du avsnittet **[!UICONTROL Shopping Cart]**. Du bör se paketprodukten tillsammans med den valda kvantiteten.

<u>Förväntade resultat</u>:

Paketartikelkvantiteten ska matcha den kvantitet som visas i butiken.

<u>Faktiska resultat</u>:

Paketartikelkvantiteten visas som 0.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
