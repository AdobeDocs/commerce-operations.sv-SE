---
title: 'MDVA-40488: Konfigurerbara produkter med underordnade produkter utanför lagret som inte visas i rätt prisintervall'
description: MDVA-40488-korrigeringen åtgärdar ett problem där konfigurerbara produkter med underordnade produkter utanför lagret inte visas i rätt prisintervall. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 är installerat. Korrigerings-ID är MDVA-40488. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# MDVA-40488: Konfigurerbara produkter med underordnade produkter utanför lagret visas inte i rätt prisintervall

MDVA-40488-korrigeringen åtgärdar ett problem där konfigurerbara produkter med underordnade produkter utanför lagret inte visas i rätt prisintervall. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 har installerats. Korrigerings-ID är MDVA-40488. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Konfigurerbara produkter med underordnade produkter som inte finns i lager visas inte i rätt prisintervall.

<u>Förutsättningar</u>:

Gå till Commerce Admin > **stores** > **configuration** > **catalog** > **Inventory** > **stock options** och ställ in **Display Out of Stock Products** -konfigurationen på *Yes*.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med två associerade produkter. Till exempel: enkla produkter Red och Brown.
1. Ange lagret för den enkla produkten Red och ange Stock-status till *I Stock*, och ange sedan statusen Enable Product (Aktivera produkt) till *No*.
1. Ställ in lager för den enkla produkten Brown och ställ sedan in statusen Enable Product (Aktivera produkt) på *Yes*.
1. Kontrollera att den konfigurerbara produktStock-statusen är *I Stock*.
1. Ändra lagret för den enkla produkten Brown till 0 och ange Stock-statusen till *Utanför lager*.
1. För närvarande är den konfigurerbara produktStock-statusen fortfarande *I Stock*.
1. Utför omindexering.
1. Kontrollera `min_price` och `max_price` för den konfigurerbara produkten i databastabellen `catalog_product_index_price` - de två värdena är inställda på 0.
1. Men om vi ställer in den konfigurerbara produktStock-statusen till *Utanför lager* och indexerar om, kan vi se värden som inte är noll `min_price` och `max_price` för den konfigurerbara produkten.

<u>Förväntade resultat</u>:

Om alla underordnade produkter är *Utanför Stock* och den konfigurerbara produkten också är *Utanför Stock* beräknas priset med hjälp av alla underordnade produkter.

<u>Faktiska resultat</u>:

`min_price`- och `max_price`-värdena för den konfigurerbara produkten i `catalog_product_index_price` DB-tabellen anges till 0 när den konfigurerbara Stock-statusen är *I lager*, men om den är *Utanför lager* blir de inte nollvärden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
