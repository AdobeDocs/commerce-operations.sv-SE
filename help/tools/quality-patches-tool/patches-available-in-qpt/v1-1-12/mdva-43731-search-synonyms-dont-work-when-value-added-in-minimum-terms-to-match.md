---
title: 'MDVA-43731: Söksynonymer fungerar inte när ett värde läggs till i Minimivillkor för matchning'
description: Korrigeringen MDVA-43731 åtgärdar ett problem där söksynonymer slutar att fungera när ett värde läggs till i"Minimala villkor att matcha". Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Korrigerings-ID är MDVA-43731. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Cache, Marketing Tools, Search
role: Admin
exl-id: 1eada0cd-c0ab-4f0f-b6bf-7c10e1df07ce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# MDVA-43731: Söksynonymer fungerar inte när ett värde läggs till i Minimivillkor för matchning

Korrigeringen MDVA-43731 åtgärdar ett problem där söksynonymer slutar att fungera när ett värde läggs till i&quot;Minimala villkor att matcha&quot;. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Korrigerings-ID är MDVA-43731. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Söksynonymer slutar att fungera när ett värde läggs till i &quot;Minimivillkor att matcha&quot;.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce med exempeldata.
1. Konfigurera Elasticsearch7 som sökmotor.
1. Sök efter ordet &quot;Jacket&quot;. En lista över produkter visas.
1. Lägg till parametern [4&lt;60%] i **Konfiguration** > **Katalog** > **Katalogsökning** > **Minimivillkor som ska matchas**.
1. Rensa konfigurationscachen och gör en omindexering.
1. Sök igen efter ordet &quot;Jacket&quot; och lägg märke till att en lista med produkter visas.
1. Gå till **Marknadsföring** > **SEO &amp; Search** > **Sök synonymer**.
1. Skapa söksynonymer genom att lägga till följande synonymer: jacka, vätekare, express plus.
1. Gör en omindexering.
1. Gör en produktsökning med någon av synonymerna. T.ex. jacka.

<u>Förväntade resultat</u>:

Du får samma produktlista som tidigare i sökresultaten.

<u>Faktiska resultat</u>:

Ingen produkt visas i sökresultatet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
