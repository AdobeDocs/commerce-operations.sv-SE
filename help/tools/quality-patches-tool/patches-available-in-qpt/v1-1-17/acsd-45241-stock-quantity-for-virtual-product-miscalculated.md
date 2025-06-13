---
title: 'ACSD-45241: Felaktig beräkning av den virtuella produktens lagerkvantitet'
description: Korrigeringen ACSD-45241 åtgärdar ett problem där den virtuella produktens lagerkvantitet inte beräknas korrekt efter att en kreditnota har skapats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 är installerat. Korrigerings-ID är ACSD-45241. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4.
feature: Orders, Products
role: Admin
exl-id: 447a84f0-aab4-4bb1-9f06-c056c006cd69
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# ACSD-45241: Felaktig beräkning av den virtuella produktens lagerkvantitet

Korrigeringen ACSD-45241 åtgärdar ett problem där den virtuella produktens lagerkvantitet inte beräknas korrekt efter att en kreditnota har skapats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 är installerat. Korrigerings-ID är ACSD-45241. Observera att problemet har åtgärdats i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerkvantiteten för en virtuell produkt beräknas inte korrekt efter att en kreditnota har skapats.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med en virtuell produkt som underordnad produkt i Commerce Admin.
1. Kontrollera att båda produkterna som skapats i steg 1 finns i lager.
1. Markera kvantiteten för den virtuella produkten som skapats i steg 1 som 100 och behåll även den säljbara kvantiteten 100.
1. Lägg produkten i kundvagnen.
1. Gör en beställning med den virtuella produkten som skapats i steg ett.
1. Behåll orderstatus som Väntande. Du behöver inte behandla betalningen.
1. `order_created` post skapades i `inventory_reservation`. Den virtuella produktkvantiteten visar 100 med säljbar kvantitet som 99.
1. Öppna ordern och gå till **Faktura** > **Skicka faktura**.
1. `invoice_created` post skapades i `inventory_reservation`. Den virtuella produktkvantiteten är nu 99 och den säljbara kvantiteten är 99.
1. Skapa en kreditnota utan att välja **Återgå till Stock**.

<u>Förväntade resultat</u>:

Ingen ny post skapas i `inventory_reservation` och lagerkvantiteten för den virtuella produkten är oförändrad.

<u>Faktiska resultat</u>:

En `creditmemo_created`-post skapas i `inventory_reservation` och den virtuella produktlagerkvantiteten justeras till 98 med försäljningsbar kvantitet som 99.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
