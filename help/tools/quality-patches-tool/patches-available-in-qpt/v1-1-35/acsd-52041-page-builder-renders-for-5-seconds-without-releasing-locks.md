---
title: 'ACSD-52041: Page Builder-återgivning frigör inte lås'
description: Använd korrigeringsfilen ACSD-52041 för att åtgärda Adobe Commerce-problemet där Page Builder renderar i fem sekunder utan att frigöra lås.
feature: Page Builder
role: Admin, Developer
exl-id: 48a7fc36-e98a-4a4e-bed3-248d7d73f6cb
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52041: Page Builder-återgivning frigör inte lås

Korrigeringen ACSD-52041 åtgärdar ett problem där Page Builder renderar i fem sekunder utan att frigöra lås. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.48 har installerats. Korrigerings-ID är ACSD-52041-v2. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 och 2.4.6 - 2.4.6-p2.



>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.


## Problem

**[!DNL Page Builder]** återger i *5* sekunder utan att låsa upp.

<u>Steg som ska återskapas</u>:

1. Redigera en CMS-sida, produktsida eller något annat som har **[!DNL Page Builder]**.
1. Spara ändringarna.
1. Lägg märke till att sidan sparar tid.

<u>Förväntade resultat</u>

Innehållet sparas. Inga fel hittades i webbläsarloggen.

<u>Faktiska resultat</u>

Det tar längre tid än vanligt att spara.
Fel i konsolen: ``Page Builder was rendering for 5 seconds without releasing locks``

## Tillämpa korrigeringen

Om du vill använda enskilda korrigeringsfiler för versionerna **2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 och 2.4.6 - 2.4.6-p2** använder du följande länkar beroende på distributionsmetod:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool]-handboken.
