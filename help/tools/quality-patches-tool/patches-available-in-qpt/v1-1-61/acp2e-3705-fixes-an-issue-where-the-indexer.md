---
title: 'ACP2E-3705: "indexer_update_all_views" kan inte köras när "MAGE_INDEXER_THREADS_COUNT" har angetts'
description: Använd programfixen ACP2E-3705 för att åtgärda Adobe Commerce-problemet där körningen av kron "indexer_update_all_views" misslyckas när "MAGE_INDEXER_THREADS_COUNT" är inställd.
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: 111325fa-8ed5-45f9-9e68-b52f4425d253
source-git-commit: 7ef772510274bc8681c395656437d64f8b40e70a
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACP2E-3705: `indexer_update_all_views` kron körning misslyckas när `MAGE_INDEXER_THREADS_COUNT` anges

>[!NOTE]
>
>Den här korrigeringen ersätter [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md) för version 2.4.7 och senare.

Korrigeringen ACP2E-3705 åtgärdar ett problem där körningen av kron `indexer_update_all_views` misslyckas när `MAGE_INDEXER_THREADS_COUNT` har angetts. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 har installerats. Korrigerings-ID är ACP2E-3705. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Körningen av kron `indexer_update_all_views` misslyckas när `MAGE_INDEXER_THREADS_COUNT` har ett värde som är större än **, vilket specifikt påverkar indexeraren [!UICONTROL Customer Segments] med B2B aktiverat.

<u>Steg som ska återskapas</u>:

1. Använd QPT-korrigeringen [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md).
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]**.
1. Aktivera **[!UICONTROL Category Permissions]**.
1. Ställ in följande indexerare till läget **[!UICONTROL Update on Schedule]**:

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Skapa några produkter och tilldela dem till en kategori.
1. Kör ett fullständigt omindexeringsintervall.
1. Gå till en kategori och ange **[!UICONTROL Category Permissions]**.
1. Kör `indexer_update_all_views` cron-jobb med `MAGE_INDEXER_THREADS_COUNT` inställt på *8*.

<u>Förväntade resultat</u>:

Indexeringen har slutförts utan fel.

<u>Faktiska resultat</u>:

Kronijobbet `indexer_update_all_views` påträffar följande fel:

```
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: Uppgraderingar och korrigeringar > Tillämpa korrigeringar i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
