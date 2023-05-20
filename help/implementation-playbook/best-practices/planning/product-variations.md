---
title: Bästa praxis för konfiguration av produktvariationer
description: Lär dig hur du optimerar Adobe Commerce prestanda genom att begränsa antalet konfigurerade produktvariationer.
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: a19dd8b4-23b8-498f-be51-a0adfcd12a11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Bästa tillvägagångssätt för att konfigurera produktvarianter

För bästa prestanda bör du konfigurera maximalt 50 varianter per produkt.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Minska antalet produktvariationer

Använd följande strategier för att minska antalet produktvariationer för bästa webbplatsprestanda:

- Strukturera om katalogen genom att distribuera antalet variationer mellan olika produkter.
- Ta bort konfigurerbara attributalternativ som inte finns i lager.
- Hantera variationer med alternativa funktioner som anpassade alternativ, kategorier, relaterade produkter, grupperade produkter och paketprodukter.

## Potentiell inverkan på prestanda

Om du överskrider det rekommenderade antalet produktvariationer kan det påverka webbplatsens prestanda på följande sätt:

- Långa efterfrågnings- och renderingstider för produktinformation och kategorisidor som innehåller komplexa produkter.
- Ökad svarstid för att slutföra Spara-åtgärder i administratören.
- Längre tid för att återge redigeringsformuläret.
- Långsam utcheckning.

## Ytterligare information

- [Skapa konfigurerbara produkter](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [Skapa en produkt](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- Utbildning—[Hantera kataloger och produkter med Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
