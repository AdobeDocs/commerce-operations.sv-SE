---
title: 'ACSD-55414: Dåliga prestanda när MariaDB försöker byta ut entitys_ids'
description: Använd korrigeringsfilen ACSD-55414 för att åtgärda Adobe Commerce-problemet när MariaDB försöker konvertera "entitys_ids" från sträng till heltal, vilket förhindrar prestandan vid omindexering.
feature: Attributes
role: Admin, Developer
exl-id: 76309cef-559e-4a55-a27b-7d807ef9f74e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-55414: Felaktiga prestanda när MariaDB försöker byta `entitys_ids`

Korrigeringen ACSD-55414 åtgärdar ett problem där prestandan för omindexering hindras när MariaDB försöker konvertera `entitys_ids` från sträng till heltal. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.41 har installerats. Korrigerings-ID är ACSD-55414. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Prestanda för omindexering hindras när MariaDB försöker konvertera `entitys_ids` från sträng till heltal.

<u>Steg som ska återskapas</u>:

1. Uppdatera `setup/performance-toolkit/profiles/ce/small.xml` genom att konfigurera *50000* enkla produkter.
1. Generera den här profilen genom att köra kommandot: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Kör omindexering: `bin/magento indexer:reindex catalog_product_attribute`.

<u>Förväntade resultat</u>:

Omindexeringen tar rimlig tid att slutföra.

<u>Faktiska resultat</u>:

Indexeringen tar för lång tid att slutföra.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
