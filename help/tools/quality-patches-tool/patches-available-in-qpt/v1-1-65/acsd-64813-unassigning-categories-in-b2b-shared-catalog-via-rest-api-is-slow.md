---
title: 'ACSD-64813: Det tar lång tid att frigöra kategorier i  [!DNL B2B] delad katalog via REST API'
description: Använd patchen ACSD-64813 för att åtgärda Adobe Commerce-problemet där det tar lång tid att frigöra kategorier i en  [!DNL B2B] delad katalog via REST API.
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0ed4bde6d78429da5a375a8c50f6b348db5a5ad5
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# ACSD-64813: Det tar lång tid att frigöra kategorier i [!DNL B2B] delad katalog via REST API

Korrigeringen ACSD-64813 åtgärdar ett problem där det tar lång tid att frigöra kategorier i en [!DNL B2B] delad katalog via REST API. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 har installerats. Korrigerings-ID är ACSD-64813. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går långsamt att frigöra kategorier i en [!DNL B2B] delad katalog via REST API.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL B2B]**, **[!UICONTROL Company]** och **[!UICONTROL Shared Catalog]**.
1. Generera 30 000 aktiva produkter i lager.
1. Skapa en [anpassad delad katalog](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls) och tilldela den alla produkter.
1. Skapa en ny kategori under standardrotkategorin och tilldela den några produkter.
1. Använd Admin-token för att anropa REST API-slutpunkten `rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories` med det nya kategori-ID:t.

```
{
  "categories": [
    { "id": <new category id> }
  ]
}
```

1. Bekräfta att svaret är *true*.
1. Kör `bin/magento cron:run` två gånger eller utför en omindexering.
1. Använd Admin-token för att anropa REST API-slutpunkten `rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories` med det nya kategori-ID:t.

```
{
  "categories": [
    { "id": <new category id> }
  ]
}
```

<u>Förväntade resultat</u>:

Operationen bör slutföras inom en rimlig tid (under några minuter).

<u>Faktiska resultat</u>:

Körningen tar ca 30 minuter eller resulterar i ett timeout-fel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
