---
title: 'ACSD-45520: Alternativ för färgrutor har inte valts på produktinformationssidan'
description: Korrigeringen ACSD-45520 åtgärdar ett problem där alternativen för färgrutor inte är förvalda på produktinformationssidan när en användare redigerar konfigurerbara produkter från kundvagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 är installerat. Korrigerings-ID är ACSD-45520. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
feature: Products
role: Admin
exl-id: a8b37dba-5a02-45a9-8e43-5288352a9d75
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-45520: Alternativ för färgrutor har inte valts på produktinformationssidan

Korrigeringen ACSD-45520 åtgärdar ett problem där alternativen för färgrutor inte är förvalda på produktinformationssidan när en användare redigerar konfigurerbara produkter från kundvagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 är installerat. Korrigerings-ID är ACSD-45520. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Alternativ för färgrutor väljs inte på produktinformationssidan när en användare redigerar konfigurerbara produkter från kundvagnen.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med produktalternativ (till exempel färg).
1. Lägg den konfigurerbara produkten i kundvagnen.
1. Gå till sidan Min kundvagn.
1. Klicka på redigeringsknappen för den konfigurerbara produkt som lagts till i steg 1.
1. Lägg märke till produktalternativen på redigeringssidan.

<u>Förväntade resultat</u>:

Produktalternativ är valda.

<u>Faktiska resultat</u>:

Produktalternativ har inte valts.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
