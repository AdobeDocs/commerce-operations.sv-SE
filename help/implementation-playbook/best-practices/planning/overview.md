---
title: Implementeringsplaneringsfas
description: Lär dig mer om de effektivaste strategierna för implementering i planeringsfasen av Adobe Commerce-projekt.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Planeringsfas

Planeringsfasen omfattar följande verksamheter:

- Arkitektur
- Katalogdesign
- Extension purchasing
- Projektomfång
- Insamling av krav
- Försäljning och marknadsföring

Följande avsnitt innehåller information om god praxis för planeringsfasen.

## Insamling av krav

<table>
<thead>
  <tr>
    <th>Bästa praxis</th>
    <th>Beskrivning</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="2"><em>Programkonfiguration</em></td>
  </tr>
  <tr>
    <td><a href="sites-stores-store-views.md">Konfigurera platser, butiker och butiksvyer</a></td>
    <td>Konfigurera webbplatser, butiker och butiksvyer för att maximera webbplatsens prestanda.</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">Vanliga konfigurationsproblem</a></td>
    <td>Åtgärda och förhindra de fem vanligaste konfigurationsproblemen för Adobe Commerce webbplatser.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html">Cachning</a></td>
    <td>Använd verktygen för cachehantering för att förbättra platsens prestanda.</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">Cachelagring</a></td>
    <td>Lär dig hur du arbetar med publika data när du implementerar cachning i ditt Adobe Commerce-tillägg.</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">OPcache-minnesstorlek</a></td>
    <td>Undvik prestandaförsämring med specifika inställningar för OPcache-minnesförbrukning.</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">Konfigurera rapportering</a></td>
    <td>Optimera webbplatsens prestanda genom att ta bort rapportmodulen om du inte använder den.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Databaskonfiguration</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">Konfigurera databasen för molndistributioner</a></td>
    <td>Konfigurera databas- och programinställningar för att förbättra prestandan när du distribuerar Adobe Commerce i molninfrastrukturprojekt.</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">Konfigurera MySQL</a></td>
    <td>Lär dig hur MySQL-utlösare och slavanslutningar påverkar webbplatsens prestanda och hur du använder dem effektivt.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Tjänstkonfiguration</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html">Konfigurera snabbt</a></td>
    <td>Konfigurera snabbtjänster för ditt Adobe Commerce i molninfrastrukturprojekt.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html">Konfigurera meddelandekanaler för New Relic</a></td>
    <td>Få tillgång till din New Relic-kontrollpanel och analysera data från din Adobe Commerce i molninfrastrukturprojekt.</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">Konfigurera Redis</a></td>
    <td>Förbättra cacheprestanda genom att använda den utökade Redis-cacheimplementeringen för Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Cachestorlek för Realpath</a></td>
    <td>Optimera prestanda genom att uppdatera cachekonfigurationen för PHP-lässökvägen så att den använder de rekommenderade inställningarna.</td>
  </tr>
</tbody>
</table>

## Katalogdesign

| Bästa praxis | Beskrivning |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [Kategorikonfiguration](catalog-management.md#category-limits) | Konfigurera produktkategorier för optimala prestanda. |
| [Produktkonfiguration &#x200B;](catalog-management.md#product-sku-limits) | Konfigurera SKU:er för optimala prestanda. |
| [Produktvariantkonfiguration](catalog-management.md#product-variations) | Konfigurera produktvariationer för optimala prestanda. |
| [Konfiguration av produktalternativ](catalog-management.md#product-options) | Konfigurera produktalternativ för optimala prestanda. |
| [Konfigurationen av produktattribut &#x200B;](catalog-management.md#product-attributes) | Konfigurera produktattribut för optimala prestanda. |
| [Sidbrytningskonfiguration för produktlistor](catalog-management.md#product-listing-pagination) | Konfigurera sidnumrering i produktlistor för optimala prestanda. |

## Tillägg

| Bästa praxis | Beskrivning |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [Använda tillägg från tredje part i Adobe Commerce](extensions.md) | Lär dig hur du undviker prestandaproblem som orsakas av Adobe Commerce-tillägg från tredje part. |

## Projektomfång

| Bästa praxis | Beskrivning |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [Partnereskaleringar](partner-escalation.md) | Förbered dig för eskalering av ett partnerproblem med ett Adobe-kontoteam eller lär dig hur du undviker eskalering. |
| [Betalningslagringsbearbetning](payment-processing-storage.md) | Bearbeta och lagra betalningsinformation på ett säkert sätt. |

## Försäljning och marknadsföring

| Bästa praxis | Beskrivning |
|------------------------------------------------------------|--------------------------------------------------------------|
| [Begränsningar för produktvarukorgen](catalog-management.md#cart-limits) | Hantera kundvagnsbegränsningar för optimala prestanda. |
| [Konfigurerar kampanjer](catalog-management.md#promotions) | Konfigurera försäljning och kampanjer för artiklar i en kundvagn. |
