---
title: 'ACSD-62332: Produktlista GraphQL-fråga begränsad till 10 000 produkter och  [!DNL Live Search] anger den aktuella sidan till 1'
description: Använd patchen ACSD-62332 för att åtgärda Adobe Commerce-problem där GraphQL-frågan är begränsad till totalt 10 000 produkter och där  [!DNL Live Search] anger den aktuella sidan till *1* istället för sidan *2* i sökvillkoren när den efterfrågas via GraphQL.
feature: GraphQL, Products, Search
role: Admin, Developer
source-git-commit: 276fe6ca8d1166a8f4254aca5d49cbb4b1aa607b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-62332: Produktlista GraphQL-fråga begränsad till 10 000 produkter och [!DNL Live Search] anger den aktuella sidan till 1

>[!NOTE]
>
>Den här korrigeringen är en uppdaterad version av [ACSD-55100](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md) och ersätter [ACSD-52801](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md) i 2.4.6-2.4.6-p8-versioner. Mer information finns i motsvarande artiklar.

Korrigeringen ACSD-62332 åtgärdar problem där GraphQL-produktlistans fråga är begränsad till `total_count` av 10 000 produkter och där [!DNL Live Search] anger den aktuella sidan till *1* i stället för sidan *2* i sökvillkoren när den efterfrågas via GraphQL. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 är installerad. Korrigerings-ID är ACSD-62332. Observera att problemen korrigerades i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktlistans GraphQL-fråga är begränsad till totalt_antal på 10 000 produkter och där [!DNL Live Search] anger den aktuella sidan till **&#x200B; i stället för sidan &#x200B;** i sökvillkoren när den efterfrågas via GraphQL.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
