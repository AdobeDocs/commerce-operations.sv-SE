---
title: 'MDVA-42855: Den nya kundadressen sparas inte i adressboken vid utcheckning '
description: Korrigeringen MDVA-42855 åtgärdar ett problem där den nya kundadressen inte sparas i adressboken under utcheckningen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Patch-ID:t är MDVA-42855. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Checkout, Orders, Shipping/Delivery
role: Admin
exl-id: 924b8f57-1fec-4e62-bf0e-1f9cafa75cab
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-42855: Den nya kundadressen sparas inte i adressboken vid utcheckning

Korrigeringen MDVA-42855 åtgärdar ett problem där den nya kundadressen inte sparas i adressboken under utcheckningen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Patch-ID:t är MDVA-42855. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den nya kundadressen sparas inte i adressboken under utcheckningen.

<u>Steg som ska återskapas</u>:

1. Skapa ett kundkonto och uppdatera standardadressen för frakt och fakturering.
1. Lägg en produkt i kundvagnen och gå till kassan.
1. Vid leverans klickar du på **+ Ny adress**.
1. Ange din nya adress och håll kryssrutan **Spara i adressbok** markerad.
1. Vid betalning markerar du kryssrutan **Min faktura- och leveransadress är densamma**.
1. Beställ.
1. Kontrollera adressboken.

<u>Förväntade resultat</u>:

Den nya leveransadressen sparas i adressboken.

<u>Faktiska resultat</u>:

Den nya leveransadressen sparas inte i adressboken.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
