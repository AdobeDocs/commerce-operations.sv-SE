---
title: Produkterna begränsar de bästa metoderna
description: Lär dig de bästa sätten att konfigurera produktlagringsenheter (SKU) för att maximera webbplatsens prestanda.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Bästa tillvägagångssätt för SKU-konfiguration av produkter

För att maximera prestandan rekommenderas ett maximum på 10 miljoner för effektiva produktlagringsenheter (SKU). Detta produktmaximum beräknas som:

`Effective SKU = N\[SKUs\] * Stores/Websites * Customer Groups`

Om du har fler än det maximala antalet aktiva SKU:er tar det längre tid att hämta produktdata och slutföra administratörsåtgärder.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Minska antalet produkter

Använd följande strategier för att minska antalet produkter (SKU):

- Minimera multiplikatorer—
   - Flyttade butiker eller webbplatser minskar multiplikatorn. Om ni har 50 000 SKU:er, tio webbplatser och tio kundgrupper är antalet SKU:er 5 miljoner. Genom att ta bort fem kundgrupper minskas antalet effektiva SKU:er till 2,5 miljoner.
   - Använd alternativa produktfunktioner för anpassade priser för att ersätta delade kataloger och kundgruppmultiplikatorer.
- Strukturera om katalogen—
   - Minska antalet produkter som tilldelas kategorier.
   - Minska antalet SKU genom att minska antalet butiker, webbplatser, kundgrupper eller produktantal.
- Skapa fler produktvarianter genom att använda anpassade alternativ istället för att skapa separata produkter.
- Inaktivera eller ta bort oanvända systemkomponenter som moduler. (Se  [Avinstallera moduler](../../../installation/tutorials/uninstall-modules.md).)
- Hantera produkter i ett externt plattformshanteringssystem (PMS).

## Ytterligare information

- [Skapa en produkt](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Produkttilldelningar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- Molninfrastruktur: [Konfigurera flera webbplatser och butiker](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- Lokalt: [Flera webbplatser eller butiker](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce om molninfrastruktur: Bästa tillvägagångssätt för butikskonfiguration](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
