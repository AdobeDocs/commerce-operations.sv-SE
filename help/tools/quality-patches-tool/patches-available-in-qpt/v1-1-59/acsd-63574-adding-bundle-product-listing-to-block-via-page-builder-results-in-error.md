---
title: 'ACSD-63574: Om [!UICONTROL Bundle Product]-lista läggs till i block via  [!DNL Page Builder] uppstår ett fel'
description: Använd korrigeringsfilen ACSD-63574 för att åtgärda Adobe Commerce-problemet där det uppstår ett fel om du lägger till alternativen **[!UICONTROL Bundle Product]** med kryssrutan eller Flera val till ett block via [!DNL Page Builder] .
feature: Page Builder, Page Content
role: Admin, Developer
source-git-commit: b2e6a3a61dbd3cd3b76e968ff8cdad664663fc4b
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-63574: Om [!UICONTROL Bundle Product]-listning läggs till i block via [!DNL Page Builder] uppstår ett fel

Korrigeringen ACSD-63574 åtgärdar ett problem där ett fel uppstår om du lägger till **[!UICONTROL Bundle Product]** med alternativen `Checkbox` eller `Multi Select` till ett block via [!DNL Page Builder]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 har installerats. Korrigerings-ID är ACSD-63574. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.4-p10

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du lägger till **[!UICONTROL Bundle Product]** i ett block med [!DNL Page Builder] bryts förhandsgranskningen av produktwidgeten och felmeddelandet *Ett fel uppstod när det här innehållet genererades*. Problemet inträffar specifikt när paketprodukten innehåller `Checkbox` eller `Multi Select` alternativtyper och `indexer dimension mode` är inställd på `website_and_customer_group`. Undantagsloggen innehåller följande fel:

    &quot;
    report.CRITICAL: PDOException: SQLSTATE[42S02]: Bastabellen eller vyn hittades inte: 1146 Tabellen &#39;db_name.catalog_product_index_price_cg0&#39; finns inte i /home/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
    &quot;

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Expandera **[!UICONTROL Catalog]** i den vänstra panelen och välj **[!UICONTROL Catalog]** bland alternativen nedan.
1. Rulla ned till avsnittet **[!UICONTROL Price]** och ange **[!UICONTROL Catalog Price Scope]** till **[!UICONTROL Global]**.
1. Ange `Indexer dimension mode` till `website_and_customer_group` med kommandot nedan:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website_and_customer_group`

1. Skapa en **[!UICONTROL Bundle Product]** med en paketalternativtyp `Checkbox` eller `Multi Select` och tilldela produkten till en kategori.
1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Blocks]** > **[!UICONTROL Edit Content with Page Builder]**.
1. Välj den kategori som den skapade produkten är tilldelad till och försök **[!UICONTROL Save]**.

<u>Förväntade resultat</u>:

Produkten har lagts till utan fel.

<u>Faktiska resultat</u>:

Det går inte att lägga till en produkt via [!DNL Page Builder] när alternativtypen **[!UICONTROL Bundle Product]** är `Checkbox` eller `Multi Select` och `indexer dimension mode` är inställd på `website_and_customer_group`. Felet genereras: *Ett fel uppstod när innehållet* genererades.


## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
