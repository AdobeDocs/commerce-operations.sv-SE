---
title: 'MDVA-38799: Hämtningsbara produkter som inte har sparats efter att en mellanlagringsuppdatering har skapats'
description: MDVA-38799-korrigeringen åtgärdar ett problem där hämtningsbara produkter inte sparas efter att en mellanlagringsuppdatering har skapats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 är installerat. Korrigerings-ID är MDVA-38799. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.
feature: Products, Staging
role: Admin
exl-id: 0ae665a8-cda2-4340-91e7-5b9b969a6607
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-38799: Hämtningsbara produkter som inte har sparats efter att en mellanlagringsuppdatering har skapats

MDVA-38799-korrigeringen åtgärdar ett problem där hämtningsbara produkter inte sparas efter att en mellanlagringsuppdatering har skapats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 har installerats. Korrigerings-ID är MDVA-38799. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce i molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0-2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Hämtningsbara produkter sparas inte när en mellanlagringsuppdatering har skapats. Användarna får felmeddelandet: *Det hämtningsbara exemplet är inte relaterat till produkten. Verifiera länken och försök igen*.

<u>Steg som ska återskapas</u>:

1. Navigera till **Katalog** > **Produkter**.
1. Klicka på listrutan bredvid Lägg till produkt och välj Hämtningsbar produkt.
   * Fyll i namn, SKU, pris och kvantitet för produkten.
1. Bläddra ned till sidan Hämtningsbar information.
1. Klicka på **Lägg till länk** under Exempel.
   * Fyll i rubriken Överför fil (filtypen spelar ingen roll).
1. Klicka på **Spara**. Du får följande meddelande: *Du har sparat produkten*.
1. Klicka på **Schemalägg ny uppdatering** högst upp på sidan.
   * Fyll i uppdateringsnamnet och ett giltigt startdatum och slutdatum.
1. Klicka på **Spara** i mellanlagringsuppdateringen.
1. Klicka på **Spara** för produkten.

<u>Förväntade resultat</u>:

Produkten sparas utan fel.

<u>Faktiska resultat</u>:

Felmeddelandet visas: *Det hämtningsbara exemplet är inte relaterat till produkten. Verifiera länken och försök igen*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
