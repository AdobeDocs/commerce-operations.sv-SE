---
title: Produkterna begränsar de bästa metoderna
description: Lär dig de bästa sätten att konfigurera produktlagringsenheter (SKU) för att maximera webbplatsens prestanda.
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 37af7b92-05ac-4a4f-9009-11e8d9f95c2f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# Bästa tillvägagångssätt för SKU-konfiguration av produkter

För att maximera prestandan rekommenderas ett maximum för effektiv produktlagringsenhet (SKU) på 242 miljoner. Denna gällande produkt-SKU-maxgräns beräknas som:

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

Var:

- N står som antalet objekt i den kategorin
- Kundgrupper inkluderar delade kataloger eftersom de skapar ytterligare en kundgrupp.

Om du har fler än det maximala antalet aktiva SKU:er tar det längre tid att hämta produktdata och slutföra åtgärder eller indexeringar på administratörspanelen.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Minska antalet produkter

Använd följande strategier för att minska antalet produkter (SKU):

- Minimera multiplikatorer—
   - Konsolidering av webbplatser minskar multiplikatorn. Om ni har 50 000 SKU:er, tio webbplatser och tio kundgrupper är antalet SKU:er 5 miljoner. Genom att ta bort fem kundgrupper minskas antalet effektiva SKU:er till 2,5 miljoner.
   - Använd alternativa produktfunktioner för anpassade priser för att ersätta delade kataloger och kundgruppmultiplikatorer.
   - Både kundgrupper och delade kataloger fungerar som multiplikatorer för antalet aktiva SKU:er i en butik.
- Strukturera om katalogen—
   - Minska antalet produkter som tilldelas kategorier.
   - Minska antalet SKU:er genom att minska antalet webbplatser, kundgrupper, delade kataloger, antalet produkter eller antalet konfigurerbara produktalternativ
- Skapa fler produktvarianter genom att använda anpassade alternativ istället för att skapa separata produkter.
- Med tanke på att en effektiv SKU kan innehålla ett antal möjliga permutationer av priserna, eftersom priserna kan anges olika för varje butik eller kundgrupp.
- Inaktivera eller ta bort oanvända systemkomponenter som moduler. (Se  [Avinstallera moduler](../../../installation/tutorials/uninstall-modules.md).)
- Hantera produkter i ett externt plattformshanteringssystem (PMS).

## Ytterligare information

- [Skapa en produkt](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Produkttilldelningar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Arbeta med delade kataloger](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- Molninfrastruktur: [Konfigurera flera webbplatser och butiker](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- Lokalt: [Flera webbplatser eller butiker](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce om molninfrastruktur: Bästa tillvägagångssätt för butikskonfiguration](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
