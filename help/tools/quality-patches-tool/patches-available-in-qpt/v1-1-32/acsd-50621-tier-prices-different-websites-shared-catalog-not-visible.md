---
title: 'ACSD-50621: Nivåpriser för olika webbplatser i delad katalog visas inte'
description: Använd korrigeringsfilen ACSD-50621 för att åtgärda Adobe Commerce-problemet där nivåpriserna för olika webbplatser i den delade katalogen inte syns när de redigeras i en miljö med flera webbplatser.
feature: Catalog Management, Orders
role: Admin
exl-id: 2256dee7-e544-4723-9753-ba9cf7247880
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-50621: Nivåpriser för olika webbplatser i delad katalog visas inte

Korrigeringen ACSD-50621 åtgärdar ett problem där nivåpriserna för olika webbplatser i den delade katalogen inte syns när de redigeras i en miljö med flera webbplatser. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.32 har installerats. Korrigerings-ID är ACSD-50621. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Nivåpriser för olika webbplatser i den delade katalogen visas inte när du redigerar dem i en miljö med flera webbplatser.

<u>Steg som ska återskapas</u>:

1. Ange **[!UICONTROL Catalog Price Scope]** som **[!UICONTROL Website]**.
1. Skapa ytterligare en webbplats, butik och butik.
1. Skapa en enkel produkt och tilldela den till alla webbplatser.
1. Skapa en anpassad delad katalog.
1. Gå till **[!UICONTROL Set Pricing and Structure]** för den anpassade delade katalog som du skapade.
1. I steg 1: välj produkter för katalog. Lägg till den enkla produkt du har skapat.
1. I steg 2: ange anpassade priser och klicka på **[!UICONTROL Configure]**.
1. Ange olika nivåpriser för olika webbplatser.
1. Markera **[!UICONTROL Done]**, klicka på **[!UICONTROL Generate Catalog]** och sedan på **[!UICONTROL Save]**.
1. Spring cron.
1. Navigera till **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** och verifiera skiktpriset.

<u>Förväntade resultat</u>:

Alla tidigare konfigurerade nivåpriser för olika webbplatser finns.

<u>Faktiska resultat</u>:

Det finns inga nivåpriser som tidigare konfigurerats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
