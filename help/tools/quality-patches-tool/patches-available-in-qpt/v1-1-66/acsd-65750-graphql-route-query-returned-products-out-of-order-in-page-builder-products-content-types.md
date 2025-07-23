---
title: 'ACSD-65750: [!DNL GraphQL] "ruttfråga" returnerar produkter i oordning i  [!DNL Page Builder] Innehållstypen Produkter'
description: Använd patchen ACSD-65750 för att åtgärda Adobe Commerce-problemet där GraphQL-frågan returnerar produkter i oordning i  [!DNL Page Builder] produkters innehållstyp.
feature: GraphQL, Page Builder, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 2555327c02985a51e7f34a36dd256227b12b5924
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-65750: [!DNL GraphQL] &quot;route&quot;-frågan returnerar produkter i oordning i [!DNL Page Builder] Products-innehållstyp

Korrigeringen ACSD-65750 åtgärdar ett problem där frågan [!DNL GraphQL] &quot;route&quot; returnerar produkter som inte är i ordning i innehållstypen [!DNL Page Builder] Products. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 har installerats. Korrigerings-ID är ACSD-65750. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p1 - 2.4.8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Frågan [!DNL GraphQL] &quot;route&quot; returnerar inte produkter i rätt sorteringsordning när innehållstypen [!DNL Page Builder] Products används.

<u>Steg som ska återskapas</u>:

1. Skapa en ny kategori och vissa produkter i katalogen och länka produkterna till den här kategorin.
1. Navigera till **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**, redigera den skapade kategorin och öppna fliken **[!UICONTROL Products in Category]**.
1. Ange anpassad **[!UICONTROL Position]** för varje produkt i den här kategorin.
1. Spara kategorin och kör omindexering.
1. Navigera till **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]** och klicka på **[!UICONTROL Add New Page]**.
1. Utöka fliken **[!UICONTROL Content]** och klicka sedan på **[!UICONTROL Edit with Page Builder]**.
1. Dra ett **[!UICONTROL Row]**-element till innehållsområdet och dra sedan ett **[!UICONTROL Products]** -element inuti raden.
1. Konfigurera elementet Produkter enligt följande:
   * **[!UICONTROL Select Products By]**: *Kategori*
   * **[!UICONTROL Category]**: *Välj den nya kategorin*
   * **[!UICONTROL Sort By]**: *Position*
1. Växla till fliken **[!UICONTROL Search Engine Optimization]** och ställ in **[!UICONTROL URL Key]** på *test-widget*.
1. Spara sidan.
1. Gör följande [!DNL GraphQL]-förfrågan:

```
query {
  route(url: "/test-widget") {
    relative_url
    redirect_code
    type
    ... on CmsPage {
      identifier
      content
      __typename
    }
    ... on ProductInterface {
      uid
      __typename
    }
    ... on CategoryInterface {
      uid
      __typename
    }
    __typename
  }
}
```

<u>Förväntade resultat</u>:

Systemet returnerar produkter i den ordning som definieras av deras kategoriposition.

<u>Faktiska resultat</u>:

Systemet returnerar produkter i en ordning som inte stämmer överens med deras kategoriposition i GraphQL-svaret.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
