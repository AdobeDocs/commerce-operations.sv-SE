---
title: 'MDVA-44940: SQL-fel när kategori sparas från admin'
description: MDVA-44940-korrigeringen åtgärdar ett problem där ett SQL-fel inträffar när en kategori sparas från administratören. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 är installerat. Korrigerings-ID är MDVA-44940. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
feature: Admin Workspace, Categories, Sales Channels
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-44940: SQL-fel när kategori sparas från admin

MDVA-44940-korrigeringen åtgärdar ett problem där ett SQL-fel inträffar när en kategori sparas från administratören. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 är installerat. Korrigerings-ID är MDVA-44940. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett SQL-fel inträffar när en kategori sparas från administratören.

<u>Steg som ska återskapas</u>:

1. Installera exempeldata.
1. Skapa en andra webbplats med en butiksgrupp tilldelad standardkategorin.

   * Skapa en butiksvy som tilldelats den nya butiksgruppen.

1. Skapa Stock och ytterligare en källa som är tilldelad detta lager och en försäljningskanal som är tilldelad den andra webbplatsen.
1. Skapa en testprodukt som tilldelats den andra webbplatsen.
1. Gå till **Admin** > **Katalog** > **Kategorier**, välj **Omfång** = **Andra webbplatsen** och gå till **Produkter i kategori** > **Automatisk sortering** > Flytta utmedieprodukter längst ned och klicka på **Spara**&rbrace;.

<u>Förväntade resultat</u>:

Kategorin sparas.

<u>Faktiska resultat</u>:

Följande fel inträffar: *Något gick fel när kategorin* sparades.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
