---
title: 'ACSD-61756: Prestandaförsämring av "AdvancedSalesRule"-filter på grund av saknade databasindex'
description: Använd patchen ACSD-61756 för att åtgärda Adobe Commerce-problemet där frågan "magento_salesrule_filter" utför en fullständig tabellsökning utan index, vilket leder till sämre prestanda vid hantering av stora mängder poster. Den här korrigeringen förbättrar prestandan genom att lägga till de saknade databasindexen för "AdvancedSalesRule"-filter.
feature: Price Rules, Price Indexer
role: Admin, Developer
source-git-commit: 42a376d1a791a17d88bea68dfef178a7b2849ce2
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-61756: Prestandaförsämring av `AdvancedSalesRule` filter på grund av saknade databasindex

Använd ACSD-61756-korrigeringen för att förbättra prestanda för `AdvancedSalesRule`-filtren genom att lägga till saknade databasindex. Detta åtgärdar problemet där `magento_salesrule_filter`-frågan utför en fullständig tabellsökning utan att använda index, vilket leder till prestandaförsämring när det finns många poster i tabellen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.54 har installerats. Korrigerings-ID är ACSD-61756. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p9

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`magento_salesrule_filter`-frågan utför en fullständig tabellsökning utan index, vilket leder till prestandaförsämring av `AdvancedSalesRule` -filtren när det finns många poster i tabellen.

<u>Steg som ska återskapas</u>:

1. Checka ut med flera aktiva försäljningsregler.

<u>Förväntade resultat</u>:

Förbättrade prestanda för försäljningsregler.

<u>Faktiska resultat</u>:

Frågan utför en fullständig tabellsökning och använder inte index, vilket leder till prestandaförsämring när det finns många poster i tabellen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
