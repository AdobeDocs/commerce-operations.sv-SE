---
title: Bästa tillvägagångssätt för sidnumrering av produktlistor
description: Lär dig hur du optimerar Adobe Commerce prestanda genom att hantera antalet produkter som visas på varje sida i storefront-katalogen.
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Bästa tillvägagångssätt för sidnumrering av produktlistor

Bästa prestanda får du om du visar högst 48 produkter per sida.

Du kan konfigurera Adobe Commerce så att kunderna kan se alla kategoriprodukter på en enda sida. Om antalet kategoriprodukter överstiger 48 produkter uppdaterar du katalogkonfigurationen för storefront-sidnumreringskontroller.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Uppdatera produktlistekonfigurationen

Om du har fler än 48 produkter i en kategori kan du uppdatera katalogkonfigurationen för storefront för att inaktivera alternativet att **Tillåt alla produkter per sida**.

När du har inaktiverat det här alternativet använder Adobe Commerce sidnumreringskontrollerna för att hantera antalet produkter som visas i butikskomponenter. Instruktioner finns i [Konfigurera sidnumreringskontroller](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Ytterligare information

- [Konfigurera produktlistor](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
