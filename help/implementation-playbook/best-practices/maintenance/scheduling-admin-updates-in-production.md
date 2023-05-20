---
title: Schemalägga administratörsuppdateringar på produktionsplatser
description: Lär dig de bästa sätten att schemalägga viktiga uppdateringar till Adobe Commerce för att förhindra långsamma prestanda och avbrott.
role: Admin, User
feature: Best Practices
feature-set: Commerce
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# Bästa tillvägagångssätt för att schemalägga administratörsuppdateringar på produktionsplatser

Schemalägg viktiga uppdateringar och åtgärder på era Adobe Commerce-sajter under kontorstid utan belastning för att förhindra långsamma prestanda och driftavbrott på produktionsplatserna.

Exempel på viktiga åtgärder:

- Administratörskonfigurationen ändras, till exempel när du uppdaterar ett produktattribut eller flyttar en produktunderkategori till en annan kategori
- Import eller export av data

Kritiska åtgärder leder till cachelagring av ogiltiga och omindexerade åtgärder, vilket avsevärt ökar svarstiden och kan orsaka webbplatsavbrott.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Ytterligare information

- [Metodtips för cachelagring](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [Privat innehåll: Gör privat innehåll ogiltigt](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [Maskinvarurekommendationer: Cacheminnen](../../../performance/hardware.md#caches)
- [Avancerad konfiguration: Konfigurera Redis](../../../performance/advanced-setup.md#set-up-redis)
