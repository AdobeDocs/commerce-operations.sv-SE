---
title: 'MDVA-43601: Utlösare tas bort från tabellen "catalogrle_product_price" efter fullständig indexering'
description: Korrigeringen MDVA-43601 åtgärdar ett problem där utlösare tas bort från tabellen "catalogrle_product_price" efter en fullständig indexering av "catalogrle_rule" eller "catalogrle_product". Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 är installerat. Korrigerings-ID är MDVA-43601. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Catalog Management, Orders, Products
role: Admin
exl-id: b9580806-ac35-4c86-8eee-c9f16d654171
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-43601: Utlösare tas bort från tabellen &quot;catalogrle_product_price&quot; efter fullständig indexering

Korrigeringen MDVA-43601 åtgärdar ett problem där utlösare tas bort från tabellen `catalogrule_product_price` efter en fullständig indexering av `catalogrule_rule` eller `catalogrule_product`. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 är installerat. Korrigerings-ID är MDVA-43601. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Utlösare tas bort från tabellen `catalogrule_product_price` efter en fullständig omindexering av `catalogrule_rule` eller `catalogrule_product`.

<u>Steg som ska återskapas</u>:

1. Ställ in alla indexerare till *Uppdatera enligt schema*.
1. Kontrollera utlösarna som har skapats för tabellen `catalogrule_product_price` genom att köra följande SQL-begäran:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Indexera om `catalogrule_rule` eller `catalogrule_product` manuellt med följande kommando: `bin/magento indexer:reindex catalogrule_rule`
1. Kontrollera utlösarna för tabellen `catalogrule_product_price` igen.

<u>Förväntade resultat</u>:

Utlösare i tabellen `catalogrule_product_price` bevaras efter en fullständig omindexering.

<u>Faktiska resultat</u>:

Inga utlösare hittades för tabellen `catalogrule_product_price`.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
