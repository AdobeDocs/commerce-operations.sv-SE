---
title: 'ACSD-49973: Förbättrad prestanda vid hämtning av paketerade produkter via  [!DNL GraphQL]'
description: Använd patchen ACSD-49973 för att åtgärda Adobe Commerce-problemet där prestandaförsämringar inträffar när paketerade produkter hämtas via  [!DNL GraphQL].
feature: GraphQL, Products
role: Admin
exl-id: d4817522-65dd-4ac8-8759-8518818684ed
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-49973: Förbättrad prestanda vid hämtning av paketerade produkter via [!DNL GraphQL]

ACSD-49973-korrigeringen förbättrar prestandahämtningen av paketerade produkter via [!DNL GraphQL]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 är installerad. Korrigerings-ID är ACSD-49973. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Prestandaförsämring inträffar när paketerade produkter hämtas via [!DNL GraphQL].

<u>Förutsättningar</u>:

Skapa 2000-paketprodukter med [Performance toolkit](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html?lang=sv-SE).

<u>Steg som ska återskapas</u>:

1. Aktivera [!DNL DB]-frågeloggaren:

   ```
   bin/magento dev:query-log:enable
   ```

1. Kör följande [!DNL GraphQL]-fråga:

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Kontrollera `var/log/db.log` om det finns förfrågningar till tabellen `catalog_product_bundle_selection`.

<u>Förväntade resultat</u>:

Begäranden till tabellen `catalog_product_bundle_selection` får inte finnas i `var/log/db.log`.

<u>Faktiska resultat</u>:

Det finns 2000 begäranden till tabellen `catalog_product_bundle_selection` som aktiveras samtidigt, vilket leder till prestandaförsämringar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool]
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i guiden för Commerce om molninfrastruktur

## Relaterad läsning

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool]
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
