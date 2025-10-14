---
title: 'ACSD-65787: SchemaBuilder kraschar när scheman skapas eller uppdateras på grund av den odefinierade matrisnyckeln "column" i tabelldata'
description: Använd patchen ACSD-65787 för att åtgärda Adobe Commerce-problemet där klassen SchemaBuilder kraschar när scheman skapas eller uppdateras på grund av en odefinierad matrisnyckel,"column", vid bearbetning av tabelldata.
feature: Backend Development, Deploy
role: Admin, Developer
exl-id: c01d1799-13fe-4657-a480-698efbe45a30
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-65787: `SchemaBuilder` kraschar när schema skapas eller uppdateras på grund av den odefinierade matrisnyckeln &quot;column&quot; i tabelldata

Korrigeringen ACSD-65787 åtgärdar ett problem där klassen `SchemaBuilder` kraschar när scheman skapas eller uppdateras på grund av en odefinierad matrisnyckel,&quot;kolumn&quot;, vid bearbetning av tabelldata. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 har installerats. Patch-ID:t är ACSD-65787. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Klassen `SchemaBuilder` kraschar när scheman skapas eller uppdateras på grund av en odefinierad matrisnyckel (kolumn) vid bearbetning av tabelldata.

<u>Steg som ska återskapas</u>:

1. Kör följande kommando:

```
bin/magento setup:upgrade
```

<u>Förväntade resultat</u>:

Inga fel.

<u>Faktiska resultat</u>:

```
Error "Warning: Undefined array key "column" in SchemaBuilder.php on line 90
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
