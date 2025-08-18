---
title: 'ACSD-66404: Cron-jobbet kan inte rensa ändringsloggtabeller på grund av  [!DNL Galera Cluster] storleksbegränsningar för transaktioner'
description: Använd korrigeringsfilen ACSD-66404 för att åtgärda Adobe Commerce-problemet där korrigeringsfilen för ändringsloggtabeller inte rensas med ett cron-jobb och  [!DNL Galera Cluster]  kan orsaka problem om datamängden i tabellerna är stor.
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 42bd5934782ca65b891a36f61102083356c92e59
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66404: Kronjobbet kan inte rensa ändringsloggtabeller på grund av [!DNL Galera Cluster] storleksbegränsningar för transaktioner

Korrigeringen ACSD-66404 åtgärdar ett problem där kron-jobbet inte kan rensa ändringstabeller, vilket orsakar [!DNL Galera Cluster] problem vid hantering av stora mängder data. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACSD-66404. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p6, 2.4.7-p6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Cron-jobbet rensar inte ändringstabeller och orsakar [!DNL Galera Cluster] problem om det finns stora mängder data i dessa tabeller.

<u>Steg som ska återskapas</u>:

1. Generera många produkter med prestandaprofiler.
1. Utför en gruppuppdatering för alla produkter i systemet, så det finns många poster i `inventory_cl` DB-tabellen.
1. Kör cron-jobbet `indexer_clean_all_changelogs`.

<u>Förväntade resultat</u>:

Kronjobbet `indexer_clean_all_changelogs` kan utföra rensning av ändringsloggar på stora ändringsloggar (10+ GB) i flera borttagningsfrågor, utan att orsaka [!DNL Galera Cluster]-problem.

<u>Faktiska resultat</u>:

Kronijobbet `indexer_clean_all_changelogs` utför rensning av ändringsloggar på stora ändringsloggar (10+ GB) i en enda raderingsfråga, vilket ger upphov till [!DNL Galera Cluster]-problem.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool]
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden för Commerce om molninfrastruktur

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken
