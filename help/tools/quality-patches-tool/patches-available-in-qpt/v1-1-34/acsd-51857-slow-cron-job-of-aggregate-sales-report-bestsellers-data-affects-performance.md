---
title: '"ACSD-51857: Det långsamma kronjobbet för "aggregat_sales_report_bestsellers_data" påverkar prestandan."'
description: Använd patchen ACSD-51857 för att åtgärda Adobe Commerce-problemet där långsamma cron-jobb "aggregate_sales_report_bestsellers_data" påverkar stora databastabeller av typen "sales_order" och "sales_order_item".
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-51857: Det långsamma kronijobbet för `aggregate_sales_report_bestsellers_data` påverkar prestandan

Korrigeringen ACSD-51857 åtgärdar ett problem där det långsamma cron-jobbet `aggregate_sales_report_bestsellers_data` påverkar stora `sales_order` - och `sales_order_item` databastabeller. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34 har installerats. Korrigerings-ID är ACSD-51857. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kronjobbsprestandan för `aggregate_sales_report_bestsellers_data` är långsam på databastabeller för `sales_order` och `sales_order_item`.

För att lösa detta har huvuddatafrågan som hämtar data för rapporten skrivits om till ett mer effektivt format. Nu används en underfråga för att fastställa datadelmängden.

För att underfrågan ska fungera så snabbt som möjligt lades ett nytt index till för databastabellen `sales_order`: `SALES_ORDER_STORE_STATE_CREATED` baserat på kolumnerna `store_id`, `state` och `created_at`.

<u>Förutsättningar</u>

Säkerställ ett stort antal order varje dag.

<u>Steg som ska återskapas</u>

1. Kör cron-jobbet `aggregate_sales_report_bestsellers_data`.
1. Kontrollera de data som ska visas på Admin Dashboard på fliken **[!UICONTROL Bestsellers]**.

<u>Förväntade resultat</u>:

*[!UICONTROL Quantity per source]* under fliken **[!UICONTROL Configuration]** får inte vara tom.

<u>Faktiska resultat</u>:

*[!UICONTROL Quantity per source]* under fliken **[!UICONTROL Configuration]** är tom.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.