---
title: Implementeringsplaneringsfas
description: Lär dig mer om de effektivaste strategierna för implementering i planeringsfasen av Adobe Commerce-projekt.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 9cda88a4aeb4cc58d8ec9c4417e3107885a6cdb8
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Planeringsfas

Planeringsfasen omfattar följande verksamheter:

- Insamling av krav
- Arkitektur
- Katalogdesign
- Projektomfång
- Kontoetablering
- Användaråtkomst
- Extension purchasing

Följande avsnitt innehåller information om god praxis för planeringsfasen.

## Insamling av krav

- **Programkonfiguration**
   - [Bästa tillvägagångssätt för att konfigurera webbplatser, butiker och butiksvyer (molninfrastruktur)](sites-stores-store-views.md)
   - [Hur man förhindrar - och åtgärdar - de fem vanligaste konfigurationsproblemen för Adobe Commerce webbplatser](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [Metodtips för cachelagring](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [Cachelagring av hela sidor](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [OPcache-minnesstorlek](opcache-memory-size.md)
   - [Rapporteringskonfiguration](reporting-configuration.md)

- **Databaskonfiguration**
   - [Bästa praxis för databaskonfigurering för &#x200B; i molnet](database-on-cloud.md)
   - [&#x200B; för MySQL-konfiguration](mysql-configuration.md)

- **Tjänstkonfiguration**
   - [Konfigurera snabbt](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic - Konfigurera meddelandekanaler](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Bästa tillvägagångssätt för Redis-&#x200B;](redis-service-configuration.md)
   - [Bästa tillvägagångssätt för cachestorlek för Realpath](realpath-cache-size.md)

## **Arkitektur**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [Understanding Global Reference Architecture](../../../implementation-playbook/architecture/global-reference/overview.md)

## **Katalogdesign**

I följande avsnitt beskrivs de effektivaste strategierna för prestandaoptimering när du konfigurerar din Adobe Commerce-katalog, inklusive rekommenderade maximivärden för antal kategorier, produkteffektiva SKU:er, produktvariationer, produktattribut och alternativ med mera.

- [Kategorikonfiguration](catalog-management.md#category-limits)
- [&#x200B; för produktkonfiguration](catalog-management.md#product-sku-limits)
- [Produktvariantkonfiguration](catalog-management.md#product-variations)
- [Konfiguration av produktalternativ](catalog-management.md#product-options)
- [&#x200B; för produktattribut](catalog-management.md#product-attributes)
- [Sidnumreringskonfiguration för produktlistor](catalog-management.md#product-listing-pagination)

## **Försäljning och marknadsföring**

- [Bästa tillvägagångssätt för produktvagnsgräns](catalog-management.md#cart-limits)
- [Bästa tillvägagångssätt för att konfigurera kampanjer](catalog-management.md#promotions)

## **Projektomfång**

- [Eskaleringar av partners](partner-escalation.md)
- [Betalningslagringsbearbetning](payment-processing-storage.md)

## **Köptillägg**

- [Bästa tillvägagångssätt för att använda tillägg från tredje part i Adobe Commerce](extensions.md)
