---
title: 'MDVA-37897: Felaktig omdirigering när produkter från Senast visade läggs till'
description: MDVA-37897-korrigeringen löser problemet med felaktig omdirigering när användare försöker lägga till produkter med alternativ från widgeten Senast visade. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1 är installerat. Patch-ID:t är MDVA-37897. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.4.
feature: Products
role: Admin
exl-id: d4d1d735-38e4-455e-9045-a2443ce33851
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37897: Felaktig omdirigering när produkter från Senast visade läggs till

MDVA-37897-korrigeringen löser problemet med felaktig omdirigering när användare försöker lägga till produkter med alternativ från widgeten Senast visade. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1 har installerats. Patch-ID:t är MDVA-37897. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce i vår molninfrastruktur 2.4.1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När en användare försöker lägga till en produkt från avsnittet Senast visade som kräver att du väljer alternativ, dirigeras användaren till produktlistsidan i stället för till produktinformationssidan.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt med anpassningsbara alternativ (Typ: Alternativknapp).
1. Konfigurera widgeten Senast visade om du vill visa produkter.
1. Besök produkter som har anpassningsbara alternativ så att de visas i widgeten Senast visade.
1. Klicka på **Lägg till i kundvagnen** på en av produkterna i widgeten Senast visade.

<u>Förväntade resultat</u>:

Du omdirigeras till sidan med produktinformation för att välja alternativ.

<u>Faktiska resultat</u>:

Du omdirigeras till produktlistsidan.

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken distributionstyp du har när du vill använda enskilda korrigeringsfiler:

* Adobe Commerce lokalt: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i vår molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om kvalitetspatchar för Adobe Commerce finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE).
