---
title: Bästa praxis för kategorikonfiguration
description: Lär dig de bästa sätten att maximera webbplatsens prestanda genom att begränsa antalet kategorier i katalogen.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# Bästa tillvägagångssätt för kategorikonfiguration

För bästa prestanda bör du inte konfigurera fler än det högsta rekommenderade antalet kategorier för Adobe Commerce-webbplatser.

- Konfigurera högst 6 000 kategorier för Adobe Commerce version 2.4.2 och senare
- För Adobe Commerce version 2.3.x och 2.4.0 till 2.4.1-p1, konfigurera maximalt 3 000 kategorier

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Minska antalet produkter

Använd följande strategier för att minska antalet kategorier:

- Hantera unika produktfunktioner med attribut och anpassade alternativ
- Ta bort inaktiva kategorier
- Optimera katalogdjup i navigeringen

## Potentiella resultateffekter

Om du har fler än det rekommenderade maximala antalet kategorier kan det påverka webbplatsens prestanda på följande sätt:

- En påtaglig ökning av svarstiden för icke-cachelagrade katalogsidor
- Lång körning och tidsgränser vid hantering av kategorier från administratören
- Ökad storlek på motsvarande databastabeller
- Större indextabeller ökar den tid som krävs för att slutföra indexeringen för `[category/product relation index\]`
- Ökad bearbetningstid för att slutföra åtgärder för att bygga kategorier, hämta menyer och hantera kategoriregler

## Ytterligare information

- [Översikt över kategorier](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [Översikt över navigering](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [Produkttilldelningar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce om molninfrastruktur: Bästa tillvägagångssätt för butikskonfiguration](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
