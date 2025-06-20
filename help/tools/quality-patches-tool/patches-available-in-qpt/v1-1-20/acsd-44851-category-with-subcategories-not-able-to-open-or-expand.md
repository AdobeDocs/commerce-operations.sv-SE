---
title: 'ACSD-44851: Kategori med underkategorier som inte kan öppnas eller expanderas'
description: Den här artikeln innehåller en lösning på problemet där användaren inte kan öppna eller utöka en kategori med underkategorier.
feature: Categories
role: Admin
exl-id: c1ad13d8-94e1-47cf-ad65-9bc5ce1c26ad
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-44851: Kategori med underkategorier som inte kan öppnas eller expanderas

Korrigeringen ACSD-44851 löser problemet där användaren inte kan öppna eller utöka en kategori med underkategorier. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 är installerat. Korrigerings-ID är ACSD-44851. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användaren kan inte öppna eller utöka en kategori med underkategorier.

<u>Steg som ska återskapas</u>:

1. I Adobe Commerce Admin skapar du ett kategoriträd med två rotkategorier och några underkategorier för var och en av dem.
1. Öppna mobilvyn/emulatorn eller minska fönsterbredden tills layouten ändras till mobil.
1. Öppna katalogens huvudmeny.
1. Försök att utöka rotkategorierna.
1. Försök att öppna kategorin.

<u>Förväntade resultat</u>:

Menyn är tillgänglig.

<u>Faktiska resultat</u>:

Mobilmenyns andra nivå öppnas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal plats för Adobe Commerce eller Magento Open Source: [Verktyg för kvalitetskorrigeringar > Användning](/help/tools/quality-patches-tool/usage.md) i guiden för kvalitetskorrigeringsverktyget.

* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
