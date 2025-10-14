---
title: 'MDVA-40134: GraphQL returnerar inte relaterade produkter när delad katalog är aktiverad'
description: MDVA-40134-korrigeringen åtgärdar ett problem där GraphQL inte returnerar relaterade produkter när den delade katalogen är aktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 är installerat. Korrigerings-ID är MDVA-40134. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
exl-id: 5d31e042-4396-40ce-8bf1-63ad9a55214d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-40134: GraphQL returnerar inte relaterade produkter när delad katalog är aktiverad

MDVA-40134-korrigeringen åtgärdar ett problem där GraphQL inte returnerar relaterade produkter när den delade katalogen är aktiverad. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 har installerats. Korrigerings-ID är MDVA-40134. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL returnerar inte relaterade produkter när den delade katalogen är aktiverad.

<u>Förutsättningar</u>:

B2B-moduler måste installeras.
Instansen måste vara ren med endast exempeldata.

<u>Steg som ska återskapas</u>:

1. Gå till **Lagrar** > **Konfiguration** > **Allmänt** > **B2B-funktioner** och aktivera **Företag och Delad katalog**.
1. Gå till **Katalog** > **Delad katalog** och lägg till alla produkter i den **allmänna katalogen**.
1. Använd exempeldata och ändra Joust Duffle Bag (SKU 24-MB01).
1. Under **Relaterade produkter** lägger du till de två Duffle-påsarna (ID 7 och 13).
1. Skicka en **Post**-förfrågan:

<pre>&lbrace;
  products(filter: {sku: {eq: "24-MB01"}}, sort: {name: ASC}) &lbrace;
    items &lbrace;
      related_products &lbrace;
        uid
        name
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;</pre>

<u>Förväntade resultat</u>:

Samhörande produkter visas i GraphQL svar.

<u>Faktiska resultat</u>:

Användarna får följande fel:

<pre>Returvärdet för Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() måste vara av typen int, null returnerade &lbrace;"exception":"[object] (GraphQL\\Error\\Error(code: 0): Returvärdet för Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() måste vara av typen int, null returnerat </pre>

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
