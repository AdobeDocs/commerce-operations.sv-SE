---
title: 'MDVA-38393: Katalogregler slutar fungera för konfigurerbara produkter om den enkla produkten får ett nytt namn'
description: MDVA-38393-korrigeringen åtgärdar ett problem där katalogregler slutar fungera för en konfigurerbar produkt om dess enkla produkt namnges på nytt. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 är installerat. Korrigerings-ID är MDVA-38393. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: Catalog Management, Categories, Configuration, Products
role: Admin
exl-id: 3d98671c-6ee7-4fe8-80d9-67fa697cae75
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-38393: Katalogregler slutar fungera för konfigurerbara produkter om den enkla produkten får ett nytt namn

MDVA-38393-korrigeringen åtgärdar ett problem där katalogregler slutar fungera för en konfigurerbar produkt om dess enkla produkt namnges på nytt. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 har installerats. Korrigerings-ID är MDVA-38393. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Katalogregler slutar fungera för en konfigurerbar produkt om den enkla produkten får ett nytt namn.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med en associerad enkel produkt.
1. Skapa en kategori.
1. Tilldela bara den konfigurerbara produkten till den nya kategorin.
1. Skapa nya katalogregler:
   * Villkor = Kategorin innehåller \&lt;nytt kategori-id>
   * Åtgärd = 50 % rabatt
   * Aktiv = Ja
1. Utför omindexering.
1. Kontrollera den konfigurerbara produkten i klientprogrammet (rabatten ska gälla).
1. Kontrollera tabellen `catalogrule_product` (den enkla produkten ska ha en rabatt).
1. Gå till Admin och ändra namnet på den enkla produkten. Detta skulle lägga till en post i tabellen `catalogrule_product_cl`.
1. Kör kron eller kommandot `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`.
1. Kontrollera tabellen `catalogrule_product`.

<u>Förväntade resultat</u>:

Den konfigurerbara produkten har rabatt.

<u>Faktiska resultat</u>:

* Rabattposterna som har skapats för de enkla produkterna saknas i tabellen `catalogrule_product`.
* Den konfigurerbara produkten i klientorganisationen har det fullständiga ursprungliga priset.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
