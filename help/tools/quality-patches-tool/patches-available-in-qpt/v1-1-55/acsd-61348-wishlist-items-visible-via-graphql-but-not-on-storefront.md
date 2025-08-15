---
title: 'ACSD-61348: Önsklisteobjekt synliga via GraphQL men inte i butiken'
description: Använd patchen ACSD-61348 för att åtgärda Adobe Commerce-problemet där önskelisteobjekten är synliga via GraphQL men inte på butiken i en miljö med flera webbplatser.
feature: Customers
role: Admin, Developer
exl-id: fcba2c28-077d-4663-b129-7da436e2791d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-61348: Önsklisteobjekt synliga via GraphQL men inte i butiken

Korrigeringen ACSD-61348 åtgärdar ett problem där önskelisteobjekten är synliga via GraphQL men inte på butiken i en miljö med flera webbplatser. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 är installerad. Korrigerings-ID är ACSD-61348. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.6-p5

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Önsklisteobjekt visas via GraphQL men inte i butiken i en miljö med flera webbplatser.

<u>Steg som ska återskapas</u>:

1. Konfigurera två webbplatser.
1. Gå till **[!UICONTROL Config Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** och ställ in **[!UICONTROL Share Customer Accounts]** på *[!UICONTROL Global]*.
1. Gå till **[!UICONTROL Config Customers]** > **[!UICONTROL Wishlist]** > **[!UICONTROL General Options]** och ställ in **[!UICONTROL Enable Multiple Wish Lists]** på *Ja*.
1. Gå till **[!UICONTROL Config General]** > **[!UICONTROL Web]** och ställ in **[!UICONTROL Add Store Code to URLs]** på *Ja*.
1. Skapa en enkel produkt och tilldela den till den andra webbplatsen.
1. Skapa en kund och logga in.
1. Lägg till en produkt i önskelistan.
1. Tilldela produkten till standardwebbplatsen.
1. Gå till sidan *[!UICONTROL Wishlist]* på standardwebbplatsen.

<u>Förväntade resultat</u>:

Produkten finns på önskelistan.

<u>Faktiska resultat</u>:

Det finns inga produkter på önskelistan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
