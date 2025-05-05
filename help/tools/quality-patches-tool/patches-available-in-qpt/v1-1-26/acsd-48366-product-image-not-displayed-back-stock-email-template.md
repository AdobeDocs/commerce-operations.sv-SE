---
title: 'ACSD-48366: produktbilden visas inte i e-postmallen [!UICONTROL Back to Stock]'
description: Använd patchen ACSD-48366 för att åtgärda problemet med Adobe Commerce där miniatyrbilden av produkten inte visas i produktens varningsmeddelande.
feature: Admin Workspace, Communications, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48366: produktbilden visas inte i e-postmallen [!UICONTROL Back to Stock]

Korrigeringen ACSD-48366 åtgärdar ett problem där produktminiatyrbilden inte visas i produktens varningsmeddelande. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 har installerats. Korrigerings-ID är ACSD-48366. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktbilden visas inte i e-postmallen [!UICONTROL Back to Stock].

<u>Steg som ska återskapas</u>:

1. Aktivera *[!UICONTROL Product Alert]* för *[!UICONTROL Back in Stock]* genom att gå till **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*.
1. Aktivera *[!UICONTROL Display Out of Stock Products]* genom att gå till **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*.
1. Skapa en enkel produkt med kvantitet = 0.
1. Skapa en kund från butiken och prenumerera på produkten ovan för att få produktvarningar när den finns i lager.
1. Gör produkten i lager.
1. Kör produktvarningsprogrammet.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Starta produktvarningen för kunden.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. Kontrollera e-postmeddelandet. Lagervarningsmeddelanden ska nu vara tillgängliga i e-postkatalogen.

<u>Förväntade resultat</u>:

Produktbilden visas i e-postmeddelandet om stockmeddelanden.

<u>Faktiska resultat</u>:

Produktbilden är inte tillgänglig i e-postmeddelandet om lagermeddelanden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
