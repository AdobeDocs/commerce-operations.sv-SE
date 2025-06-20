---
title: 'MDVA-39546: Startdatum för mellanlagringsuppdatering kan anges till ett datum som är tidigare än dagens datum'
description: MDVA-39546-korrigeringen åtgärdar ett problem där startdatumet för mellanlagringsuppdateringen kan anges till ett tidigare datum än det aktuella datumet. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Korrigerings-ID är MDVA-39546. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Staging
role: Admin
exl-id: 5d53db52-71af-4c19-84dd-dffb7303c00f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-39546: Startdatum för mellanlagringsuppdatering kan anges till ett datum som är tidigare än dagens datum

MDVA-39546-korrigeringen åtgärdar ett problem där startdatumet för mellanlagringsuppdateringen kan anges till ett tidigare datum än det aktuella datumet. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Korrigerings-ID är MDVA-39546. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Startdatumet för mellanlagringsuppdateringen kan anges till ett datum som är tidigare än det aktuella datumet.

<u>Steg som ska återskapas</u>:

1. Schemalägg en ny uppdatering för en produkt med ett framtida startdatum.
1. Redigera uppdateringen från **Innehåll** > **Förproduktion av innehåll** > **Kontrollpanel** och uppdatera startdatumet med ett äldre datum och spara ändringen.
1. Öppna uppdateringen ovan igen.

<u>Förväntade resultat</u>:

Tidigare data visas i redigeringsformuläret.

<u>Faktiska resultat</u>:

Värden i formuläret saknas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
