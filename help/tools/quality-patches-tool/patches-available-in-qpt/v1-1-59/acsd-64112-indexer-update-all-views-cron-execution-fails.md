---
title: 'ACSD-64112: Körning av kron "indexer_update_all_views" misslyckas när "MAGE_INDEXER_THREADS_COUNT" har angetts'
description: Använd korrigeringsfilen ACSD-64112 för att åtgärda Adobe Commerce-problemet där körningen av kron "indexer_update_all_views" misslyckas när "MAGE_INDEXER_THREADS_COUNT" har angetts.
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: c95f179d-5291-481f-b655-08a9db608513
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-64112: Körning av kron `indexer_update_all_views` misslyckas när `MAGE_INDEXER_THREADS_COUNT` anges

>[!NOTE]
>
>Den här korrigeringen har ersatts med [ACP2E-3705](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3705-fixes-an-issue-where-the-indexer.md) för Adobe Commerce-versioner över 2.4.7.

Korrigeringen ACSD-64112 åtgärdar ett problem där körningen av kron `indexer_update_all_views` misslyckas när `MAGE_INDEXER_THREADS_COUNT` anges. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 har installerats. Korrigerings-ID är ACSD-64112. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p10

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p10

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Körningen av kron `indexer_update_all_views` misslyckas när `MAGE_INDEXER_THREADS_COUNT` har ett värde som är större än 2, vilket specifikt påverkar [!UICONTROL Customer Segments]-indexeraren med B2B aktiverat.

<u>Steg som ska återskapas</u>:

1. Installera en ren instans med B2B.
1. Aktivera **[!UICONTROL B2B Company]** och **[!UICONTROL Shared Catalog]**.
1. Skapa en kategori.
1. Skapa några produkter och tilldela dem till kategorin.
1. Kör ett fullständigt omindexeringsintervall.
1. Ange följande indexerare till **[!UICONTROL Update on Schedule]**:

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Gå till serverdelen och läs in den nya kategorin.
1. Klicka på **[!UICONTROL Category Permissions]** och skapa en **[!UICONTROL New Permission]** för en befintlig kundgrupp.
1. Kontrollera att indexeraren `catalogpermissions_category` har en eftersläpning. Kör följande kommando för att verifiera detta:

   ```
   bin/magento indexer:status
   ```

1. Ange följande antal för indexerartråd i `env.php`:

   ```php
   'MAGE_INDEXER_THREADS_COUNT' => 8
   ```

1. Kör cron-jobbet:

   ```
   bin/magento cron:run
   ```

<u>Förväntade resultat</u>:

Kronijobbet ska köras utan några problem.

<u>Faktiska resultat</u>:

Kronijobbet `indexer_update_all_views` påträffar följande fel:

```
report.CRITICAL: PDOException: There is no active transaction in /home/vendor/magento/zend-db/library/Zend/Db/Adapter/Pdo/Abstract.php:326
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Ytterligare steg krävs efter installationen av korrigeringsfilen

(Det här avsnittet är valfritt. Det kan finnas åtgärder som krävs efter att du har implementerat korrigeringen för att åtgärda problemet.) 

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
