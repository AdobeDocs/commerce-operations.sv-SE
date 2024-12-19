---
title: 'ACSD-62577: Prestandaoptimering för Storefront-sökning'
description: Använd korrigeringsfilen ACSD-62577 för att åtgärda Adobe Commerce-problemet där sökprestanda för butiker försämras på grund av långsam frågekörning orsakad av en stor tabell av typen "search_query".
feature: Search
role: Admin, Developer
source-git-commit: dbb185fb44b491b9e8d12290d75538d98c911eac
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-62577: Prestandaoptimering för Storefront-sökning

Korrigeringen ACSD-62577 åtgärdar problemet med långsam prestanda för sökfrågor i butiker genom att optimera både fråga- och tabellindex. Den här korrigeringen är tillgänglig med [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. Korrigerings-ID är ACSD-62577. Observera att problemet var planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.6, 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Stora `search_query`-tabeller gör att sökningar i butiker går långsammare, vilket ökar svarstiderna i frontend på grund av ineffektiva frågor och brist på optimerade tabellindex.

<u>Steg som ska återskapas</u>:

1. Konfigurera Adobe Commerce Developer med prestandaverktygen `small.xml`.
1. Gå till SQL-kommandoraden och ta bort tabellen `search_query` med följande kommandon:

   ```
   SET FOREIGN_KEY_CHECKS = 0;  
   DROP TABLE search_query;  
   SET FOREIGN_KEY_CHECKS = 1;  
   ```

1. Fyll i tabellen `search_query` med ett stort antal poster, t.ex. 4 miljoner poster.
1. Utlös omindexering och tömning av cacher.

   ```
   bin/magento indexer:reindex  
   bin/magento c:c  
   bin/magento c:f  
   ```

1. Aktivera felsökningsloggar för databaser:

   ```
   bin/magento dev:query-log:enable  
   ```

1. Sök efter en term i sökfältet för butiker, t.ex.
   `http://your_magento_instance/default/catalogsearch/result/?q=test.`
1. Kontrollera `db.log` för frågekörningstiden för följande SQL:

   ```
   SELECT COUNT(*) FROM (  
   SELECT DISTINCT `main_table`.`query_text`  
   FROM `search_query` AS `main_table`  
   WHERE (main_table.store_id IN (1))  
   AND (main_table.num_results > 0)  
   ORDER BY `main_table`.`popularity` DESC  
   LIMIT 100  ) AS `result` WHERE (result.query_text = 'test')  
   ```

<u>Förväntade resultat</u>:

Frågekörningstiden är optimerad, vilket resulterar i en mindre signifikant ökning av svarstiden när stora `search_query` tabeller bearbetas.

<u>Faktiska resultat</u>:

Frågekörningstiden ökar avsevärt på grund av ineffektiv hantering av den stora `search_query`-tabellen:

```
TIME: 10.8520 seconds  
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
