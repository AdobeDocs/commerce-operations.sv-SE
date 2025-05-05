---
title: '"MDVA-42509: CSV kunde inte överföras för snabbbeställning vilket resulterade i felet "Det gick inte att skicka cookien"'
description: MDVA-42509-korrigeringen löser problemet där en CSV-fil inte kunde överföras för snabbbeställning vilket resulterade i *Det gick inte att skicka cookie-filen*. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 är installerat. Korrigerings-ID är MDVA-42509. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: B2B, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-42509: Det gick inte att överföra CSV för snabbbeställning vilket resulterade i felet&quot;Det går inte att skicka cookien&quot;

MDVA-42509-korrigeringen löser problemet där en CSV inte kunde överföras för snabbbeställning vilket resulterade i *Det gick inte att skicka cookie*-felet. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 är installerat. Korrigerings-ID är MDVA-42509. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du skapar en snabborder med ett stort antal produkter med hjälp av en CSV-fil visas ett cookie-fel: *Det går inte att skicka cookien*

<u>Steg som ska återskapas</u>:

1. Aktivera snabbordning genom att gå till **Lager** > **Inställningar** > **Konfigurationer** > **Allmänt** > **B2B-funktioner**.
1. Skapa ett kundkonto och gå till **Snabbbeställning** på den översta länken.
1. Försök att skapa en snabb beställning med en CSV-fil som har fler än 100 SKU:er.

<u>Förväntade resultat</u>:

Du kan skapa en snabb beställning med ett stort antal SKU:er.

<u>Faktiska resultat</u>:

Ett felmeddelande visas som relaterar till cookie-storleken.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
