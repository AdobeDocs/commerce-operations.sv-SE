---
title: 'ACSD-50260: Sökresultaten för GraphQL-produkter är begränsade'
description: Använd korrigeringsfilen ACSD-50260 för att åtgärda Adobe Commerce-problemet där sökresultaten för GraphQL-produkter begränsas till 10 000 resultat.
feature: Admin Workspace, Categories, GraphQL, Products, Search
role: Admin
exl-id: a9099fab-226d-439b-b2d0-f354d6b5638f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-50260: Sökresultaten för GraphQL-produkter är begränsade

Korrigeringen ACSD-50260 åtgärdar ett problem där sökresultaten för GraphQL-produkter begränsas till 10 000 resultat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 är installerad. Korrigerings-ID är ACSD-50260. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sökresultaten för GraphQL-produkter är begränsade till 10 000 resultat.

<u>Steg som ska återskapas</u>:

1. Generera *[!UICONTROL 15,000 products]* i en kategori.
1. Fråga den kategorin med GraphQL-begäran som bifogas nedan:

```GraphQL
{
  products(
    filter: { category_id: { eq: "{CATEGORY_ID}" } }
    pageSize: 5
    currentPage: 1
  ) {
    total_count
    page_info {
      current_page
      page_size
      total_pages
    }

    aggregations {
      attribute_code
      count
      label
      options {
        label
        value
      }
    }

    items {
      uid
      sku
      is_for_clearance
      categories {
        name
        breadcrumbs {
          category_name
          category_uid
        }
        display_mode
        description
      }
    }
  }
}
```

<u>Förväntade resultat</u>:

`total_count = 15k`

Möjlighet att hämta alla produkter i sökresultatet.

<u>Faktiska resultat</u>:

`total_count = 10k`

Det finns ingen möjlighet att hämta produkter efter denna 10 kB-batch i sökresultaten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
