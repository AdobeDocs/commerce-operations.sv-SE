---
title: 'ACSD-50817: Optimerar sälj_ren_offerter för seriejobb så att körningen går snabbare'
description: Använd korrigeringsfilen ACSD-50817 för att optimera cron-jobbet "sales_clean_quotes" så att det körs snabbare genom att lägga till ett sammansatt index i kolumnerna "store_id" och "updated_at" i citattabellen.
feature: Quotes
role: Admin
exl-id: b6cd412f-2f37-438b-9abc-d45de6ed54d6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-50817: Optimerar kronjobbet `sales_clean_quotes` så att det körs snabbare

Korrigeringen ACSD-50817 optimerar kron-jobbet `sales_clean_quotes` så att det körs snabbare genom att ett sammansatt index läggs till i kolumnerna `store_id` och `updated_at` i citattabellen. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.31 har installerats. Korrigerings-ID är ACSD-50817.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kronjobbet `sales_clean_quotes` är för långsamt. Med den här korrigeringen har den optimerats så att den körs snabbare genom att ett sammansatt index läggs till i kolumnerna `store_id` och `updated_at` i citattabellen.

<u>Steg som ska återskapas</u>:

1. Generera 50-80M citattecken med `updated_at` inställt som &lt; 30 dagars period.
1. Kör cron-jobbet `sales_clean_quotes` eller följande fråga i offerttabellen:

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>Förväntade resultat</u>

Kronjobbet `sales_clean_quotes` optimeras för att köras snabbare genom att ett sammansatt index läggs till i kolumnerna `store_id` och `updated_at` i citattabellen.

<u>Faktiska resultat</u>

Frågan är för långsam.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
