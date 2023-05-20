---
title: Implementeringsplaneringsfas
description: Lär dig mer om de effektivaste strategierna för implementering i planeringsfasen av Adobe Commerce-projekt.
role: Developer, Admin, User
feature: Best Practices
feature-set: Commerce
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '248'
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
   - [Bästa praxis för databaskonfigurering för molndistributioner &#x200B;](database-on-cloud.md)
   - [Konfiguration &#x200B; för MySQL-slavanslutning](configure-mysql-slave-connection-on-cloud.md)
   - [Användning av MySQL-utlösare](mysql-triggers-usage.md)

- **Tjänstkonfiguration**
   - [Konfigurera snabbt](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic - Konfigurera meddelandekanaler](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Bästa tillvägagångssätt för Redis-&#x200B;](redis-service-configuration.md)
   - [Bästa tillvägagångssätt för cachestorlek i Realpath](realpath-cache-size.md)

## **Arkitektur**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [Understanding Global Reference Architecture](../../../implementation-playbook/architecture/global-reference.md)

## **Katalogdesign**

I följande avsnitt beskrivs de effektivaste strategierna för prestandaoptimering när du konfigurerar din Adobe Commerce-katalog, inklusive rekommenderade maximivärden för antal kategorier, produkteffektiva SKU:er, produktvariationer, produktattribut och alternativ med mera.

- [Kategorikonfiguration](category-limits.md)
- [&#x200B;](product-sku-limits.md)
- [Produktvariantkonfiguration](product-variations.md)
- [Konfiguration av produktalternativ](product-options.md)
- [&#x200B; för produktattribut](product-attributes-and-options.md)
- [Sidnumreringskonfiguration för produktlistor](product-listing-pagination.md)

## **Försäljning och marknadsföring**

- [Bästa tillvägagångssätt för produktvagnsgräns](product-cart.md)
- [Bästa tillvägagångssätt för att konfigurera kampanjer](product-cart-promotions.md)

## **Projektomfång**

- [Eskaleringar av partners](partner-escalation.md)
- [Betalningslagringsbearbetning](payment-processing-storage.md)

## **Köptillägg**

- [Bästa tillvägagångssätt för att använda tillägg från tredje part i Adobe Commerce](extensions.md)
