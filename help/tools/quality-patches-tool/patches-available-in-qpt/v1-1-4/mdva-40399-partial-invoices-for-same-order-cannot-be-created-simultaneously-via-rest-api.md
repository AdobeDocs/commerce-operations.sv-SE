---
title: "MDVA-40399: Det går inte att skapa partiella fakturor för samma order samtidigt via API"
description: Korrigeringen MDVA-40399 åtgärdar ett problem där partiella fakturor för samma order inte kan skapas samtidigt via Rest API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 är installerat. Korrigerings-ID är MDVA-40399. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 1fb76b8d648cbbe2a9f602d2b1a0149f1f4f0e46
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-40399: Det går inte att skapa partiella fakturor för samma order samtidigt via API

Korrigeringen MDVA-40399 åtgärdar ett problem där partiella fakturor för samma order inte kan skapas samtidigt via Rest API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 har installerats. Korrigerings-ID är MDVA-40399. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att skapa partiella fakturor för samma order samtidigt med Rest API.

<u>Förutsättningar</u>:

En konfigurerbar produkt med minst två variationer.

<u>Steg som ska återskapas</u>:

1. Lägg båda varianterna av den konfigurerbara produkten i kundvagnen.
1. Beställ.
1. Skapa två fakturor samtidigt för ordern via Rest API.

<u>Förväntade resultat</u>:

* Båda fakturorna måste skapas.
* `qty_invoiced` ska uppdateras för båda fakturorna i tabellen `sales_order_item`.
* Båda produkterna ska ha fakturerad kvantitet.

<u>Faktiska resultat</u>:

* Båda fakturorna har skapats.
* `qty_invoiced` uppdateras inte mot en av fakturorna i tabellen `sales_order_item`.
* Fakturakvantiteten visas endast för en produkt på sidan **Ordervy** hos administratören.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).