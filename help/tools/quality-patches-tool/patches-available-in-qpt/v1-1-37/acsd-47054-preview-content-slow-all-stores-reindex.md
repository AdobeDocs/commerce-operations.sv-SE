---
title: 'ACSD-47054: Förhandsgranska innehåll långsamt när alla butiker indexerar om'
description: Använd korrigeringsfilen ACSD-47054 för att åtgärda Adobe Commerce-problemet där förhandsvisningssidan laddas långsamt på grund av omindexering av alla butiker.
feature: Page Content
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-47054: Förhandsgranska innehåll långsamt när alla butiker indexerar om

Korrigeringen ACSD-47054 åtgärdar ett problem där en förhandsgranskning av innehållstagningen tar längre tid att läsa in när det finns många butiker. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.37 är installerad. Korrigerings-ID är ACSD-47054. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder): 2.4.2-p2, 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det tar lång tid att läsa in förhandsgranskningssidan eftersom alla butiker har indexerats om.

<u>Steg som ska återskapas</u>:

1. Gå till Commerce Admin.
1. Skapa schemalagda uppdateringar.
1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Dashboard]**.
1. Förhandsgranska den schemalagda uppdateringen.
1. Öppna en kategori.

<u>Förväntade resultat</u>:

Förhandsgranskningssidan läses in inom en acceptabel tidsperiod.

<u>Faktiska resultat</u>:

Det tar lång tid att förhandsgranska innehållstagningen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
