---
title: 'ACSD-59083: Det gick inte att hitta fel i bastabellen eller vyn vid samtidiga vyuppdateringar'
description: Använd korrigeringsfilen ACSD-59083 för att åtgärda Adobe Commerce-problemet där vissa databasuppdateringsåtgärder misslyckas med felet "Bastabellen eller vyn hittades inte".
feature: System
role: Admin, Developer
exl-id: a0fa2ac9-e61f-43d5-81ff-edf178b1abc0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-59083: *Bastabellen eller vyn hittades inte* fel under samtidiga `mview` uppdateringar

Korrigeringen ACSD-59083 åtgärdar ett problem där vissa databasuppdateringsåtgärder misslyckas med felet &quot;Bastabell eller vy hittades inte&quot; när `mview` uppdateringar körs samtidigt. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 är installerad. Korrigerings-ID är ACSD-59083. Observera att problemet har åtgärdats i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.5-p5

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Vissa databasuppdateringsåtgärder resulterar i fel av typen &quot;Bastabell eller vy hittades inte&quot; när `mview` uppdateringar körs samtidigt.

<u>Steg som ska återskapas</u>:

1. Ställ in indexeringsläget på **[!UICONTROL Update on Schedule]**.
1. Infoga poster i `cl`-tabeller med följande SQL-kommandon:

   ```
   INSERT INTO catalogrule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogsearch_fulltext_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_category_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_attribute_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_category_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_price_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO customer_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO design_config_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO salesrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_product_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_rule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   ```

1. Installera profilen `setup/performance-toolkit/profiles/ce/small.xml`.
1. Lägg till en brytpunkt i filen `magento2ee/lib/internal/Magento/Framework/ForeignKey/Config/DbReader.php` på rad 72.
1. Rensa cachen.
1. Klicka på **[!UICONTROL Add to Cart]** för valfri produkt.
1. Starta cron-jobbet när körningen når brytpunkten.
1. Återuppta processen när kron-jobbet har startats.

<u>Förväntade resultat</u>:

Databasåtgärderna kan köras utan fel.

<u>Faktiska resultat</u>:

Ett fel inträffar under körningen:

```
SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento24.design_config_dummy_cl__tmp663bb682960345_17794892' doesn't exist in /www/magento24/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
