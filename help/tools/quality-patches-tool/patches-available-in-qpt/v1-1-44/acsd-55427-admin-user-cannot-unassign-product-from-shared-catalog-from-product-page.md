---
title: 'ACSD-55427: En administratör kan inte ta bort produkttilldelningen från **[!UICONTROL Product in Shared Catalogs]** på produktens sida'
description: Använd korrigeringsfilen ACSD-55427 för att åtgärda Adobe Commerce-problemet där en produkt inte kan tas bort från **[!UICONTROL Product in Shared Catalogs]**.
feature: Products, B2B
role: Admin, Developer
exl-id: 974347fd-351d-4a4b-a9ca-a534daf3fbd7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-55427: En administratör kan inte ta bort produkttilldelningen från **[!UICONTROL Product in Shared Catalogs]** på produktsidan

Korrigeringen ACSD-55427 åtgärdar ett problem där du inte kan ta bort tilldelningen av en produkt från **[!UICONTROL Product in Shared Catalogs]** på produktens sida i katalogen i Commerce Admin. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44 har installerats. Korrigerings-ID är ACSD-55427. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Du kan inte ta bort tilldelningen för en produkt från **[!UICONTROL Product in Shared Catalogs]** på produktens sida i katalogen i Commerce Admin.

<u>Steg som ska återskapas</u>:

Krav: Adobe Commerce har installerats med både B2B och **[!UICONTROL Shared Catalogs]** aktiverat.
1. Skapa en produkt.
1. Navigera till kontrollpanelen för den delade katalogen och öppna den delade standardkatalogen.
1. Tilldela produkten till standardkatalogen och ange ett pris som är lägre än produktpriset.
1. Spara den delade katalogen.
1. Kör [!UICONTROL CRON] för att uppdatera konsumenterna/indexerarna.
1. Öppna produkten och ta bort produkten från avsnittet **[!UICONTROL Product in Shared Catalogs]**.

<u>Förväntade resultat</u>:

Produkten ska tas bort från avsnittet **[!UICONTROL Product in Shared Catalogs]**.

<u>Faktiska resultat</u>:

Produkten visas fortfarande i avsnittet **[!UICONTROL Product in Shared Catalogs]**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
