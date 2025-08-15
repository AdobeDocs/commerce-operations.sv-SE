---
title: 'ACSD-63299: Specialpriset för en konfigurerbar produkt visas inte i butiken'
description: Använd patchen ACSD-63299 för att åtgärda Adobe Commerce-problemet där specialprisattributet inte längre påverkar visningen av specialpriser för konfigurerbara produkter.
feature: Catalog Management
Role: Admin, Developer
exl-id: cd1775c5-783e-4ed5-a148-1dae0b7542f8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-63299: Specialpriset för en konfigurerbar produkt visas inte i butiken

Korrigeringen ACSD-63299 åtgärdar ett problem där specialprisattributet inte längre påverkar visningen av specialpriser för konfigurerbara produkter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 har installerats. Korrigerings-ID är ACSD-63299. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

I [!DNL Adobe Commerce] påverkar inte längre hur specialpriser visas för konfigurerbara produkter om du ändrar värdet *Används i produktlista* för specialprisattributet.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Products]**.
1. Hitta attributet ***[!UICONTROL special_price]*** och navigera till **[!UICONTROL Storefront Properties]**.
1. Ändra ***[!UICONTROL Used in Product Listing]*** till ***[!UICONTROL No]***.
1. Skapa en konfigurerbar produkt med ett underordnat objekt:
   * Namn och SKU: Test
   * Pris: 159 dollar
   * Generera alternativ baserat på färg. Lägg till en ny färg: Blå
   * Spara
1. Öppna den underordnade produkten och följ dessa steg:
   * Ange ett specialpris på 99,90 USD i **[!UICONTROL Advanced Pricing]**
   * Ändra [!UICONTROL Visibility] till **[!UICONTROL Catalog, Search]**.
1. Öppna den enkla produktsidan och bekräfta att specialpriset visas.
1. Öppna den konfigurerbara produktsidan.
1. Välj den blå produkten.

<u>Förväntade resultat</u>:

Specialpriset visas på samma sätt som för den enkla produkten.

<u>Faktiska resultat</u>:

1. Det fullständiga priset visas när en konfigurerbar produkt väljs.
1. Det finns en avvikelse mellan avsnitten *Så låg som..* ($99.90) och det faktiska priset ($99.90 + $59.10 = $159.00).

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
