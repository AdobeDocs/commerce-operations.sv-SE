---
title: 'ACSD-52801: GraphQL produktfilterfråga visar inte delvisa matchningsresultat'
description: Använd korrigeringsfilen ACSD-52801 för att åtgärda Adobe Commerce-problemet där GraphQL produktfilterfråga inte visar partiella matchningsresultat.
feature: Products
role: Admin, Developer
exl-id: 946a7189-60b2-4812-92ca-ed7ba35b2488
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-52801: GraphQL produktfilterfråga visar inte delvisa matchningsresultat

>[!NOTE]
>
>En uppdaterad korrigering ([ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md)) har släppts för att lösa samma problem för versionerna 2.4.6-2.4.6-p8. Den ersätter patchen ACSD-52801 för version 2.4.6 och framåt. Mer information finns i [ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md).

Korrigeringen ACSD-52801 åtgärdar ett problem där GraphQL produktfilterfråga inte visar partiella matchningsresultat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 har installerats. Korrigerings-ID är ACSD-52801. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2, 2.4.5-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL produktfilterfråga visar inte delvisa matchningsresultat.

<u>Steg som ska återskapas</u>:

1. Installera en ren instans med exempeldata.
1. Kör följande GraphQL-fråga.

```GraphQL
{
  products(
    filter: { name: { match: "Life" } }
    sort: { position: ASC }
    pageSize: 100
    currentPage: 1
  ) {
    total_count
    items {
      url_key
      sku
      name
      meta_title
    }
  }
}
```

<u>Förväntade resultat</u>:

Det tillåter liknande matchningsresultat som i framåtriktad sökning i bakgrunden genom att lägga till attributet `match_type` ([!UICONTROL PARTIAL], [!UICONTROL FULL]) för att kontrollera de resultat som krävs. [!UICONTROL FULL] matchar fullständiga ord och [!UICONTROL PARTIAL] matchar partiella ord som livstid i hela livet.

<u>Faktiska resultat</u>:

Produktfilterfrågan returnerar inte resultat av partiella matchningar för söknyckelord.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
