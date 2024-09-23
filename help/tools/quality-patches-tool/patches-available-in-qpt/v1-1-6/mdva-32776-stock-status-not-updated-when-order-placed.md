---
title: 'MDVA-32776: Stock-status har inte uppdaterats med orderplacering'
description: MDVA-32776-korrigeringen åtgärdar ett problem där lagerstatusen inte uppdateras när en order läggs men inte skickas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 är installerat. Patch-ID:t är MDVA-32776. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
feature: Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-32776: Stock-status har inte uppdaterats med orderplacering

MDVA-32776-korrigeringen åtgärdar ett problem där lagerstatusen inte uppdateras när en order läggs men inte skickas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 har installerats. Patch-ID:t är MDVA-32776. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.0

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerstatusen uppdateras inte när en order placeras men inte skickas.

<u>Förutsättningar</u>:

1. Lagermodulen är installerad.
1. Visa färdiga produkter är inställt på *Ja*.

   Gå till **Lager** > **Konfiguration** > **Katalog** > **Lager** > **Visa ej lagrade produkter** = *Ja* om du vill ange inställningar.

<u>Steg som ska återskapas</u>:

1. Skapa två enkla produkter med kvantitet = 11 och 22.
1. Skapa en grupperad produkt med hjälp av de enkla produkter som skapas i steg 1.
1. Lägg grupperade produkter i varukorgen genom att ange en produktkvantitet till 11 och göra den andra enkla produkten till lagerförd.
1. Slutför utcheckningen och lägg ordern.

<u>Förväntade resultat</u>:

Grupperade produkter visar `out-of-stock` etiketter när associerade enkla produkter lämnar lagret.

<u>Faktiska resultat</u>:

1. Den enkla produkten med kvantitet = 11 har slut på lager.
1. Den grupperade produkten visar inte något *ej i lager*-meddelande för produkten med kvantitet = 11. Om du lägger till den här produkten i kundvagnen uppstår dock ett *fel som inte finns i lager*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html-).
