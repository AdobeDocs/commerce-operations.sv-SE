---
title: Referensarkitektur
description: Granska diagram över den rekommenderade referensarkitekturen för Adobe Commerce och Magento Open Source.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Referensarkitektur

I det här avsnittet beskrivs en allmän rekommenderad konfiguration för Adobe Commerce- och Magento Open Source-instanser med vanliga servrar som lagras fysiskt i ett datacenter (inte virtualiserat) där resurser inte delas med andra användare. Din värdleverantör, särskilt om den specialiserar sig på Commerce High Performance Hosting, kan rekommendera en annan konfiguration som är lika eller mer effektiv för dina behov.

Information om Adobe Commerce i molninfrastrukturmiljöer finns på [Startarkitektur](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] Referensarkitektur

The [!DNL Commerce] Diagram över referensarkitektur representerar den bästa metoden för att skapa en skalbar [!DNL Commerce] webbplats.

Färgen på varje element i diagrammet anger om elementet är en del av Magento Open Source eller Adobe Commerce och om det behövs.

* Orange-element krävs för Magento Open Source
* Grå element är valfria för Magento Open Source
* Blå element är valfria för Adobe Commerce

![Diagram över referensarkitektur för handel](../assets/performance/images/ref-architecture-2.3.png)

I följande avsnitt ges rekommendationer och överväganden för varje avsnitt i referensarkitekturdiagrammet för Commerce.

### [!DNL Varnish]

* A [!DNL Varnish] kluster kan skalas till trafik på en plats
* Justera instansstorleken baserat på antalet cachesidor som behövs
* Använd en [!DNL Varnish] Använd mallen för att tömma en begäran (högst) per webbskikt

### Webb

* Aktivera nodskala för trafik och redundans
* En nod är master och kör cron
* Du kan också använda en dedikerad administratör och arbetsnoder

### Cache

* Överväg att implementera en separat Redis-instans för sessioner
* Du kan ha en Redis-instans per cache
* Ändra storlek på instansen så att den innehåller den största förväntade cachestorleken

### Databas och köer

* Högtrafikplatser kan finjustera databasprestanda med slave DB och dela DB för order/carts (i Adobe Commerce)
* Överväg att använda en slave DB för snabb återställning och säkerhetskopiering av data
* Platser med låg trafik kan lagra bilder i databasen

### Sök {#search-heading}

* Justera antalet instanser baserat på söktrafik

### Lagring

* Överväg att använda GFS eller GlusterFS för pub/media-lagring
* Du kan också använda DB-lagring för platser med låg trafik

### Rekommenderas [!DNL Varnish] referensarkitektur

Magento stöder flera helsidescachningsmotorer (File, Memcache, Redis, [!DNL Varnish]) direkt i paketet, tillsammans med utökad täckning via tillägg. [!DNL Varnish] är den rekommenderade motorn för helsidescache.  [!DNL Commerce] stöder många olika [!DNL Varnish] konfigurationer.

För webbplatser som inte kräver hög tillgänglighet rekommenderar vi att du använder en [!DNL Varnish] konfiguration med Nginx SSL-avslutning.

![Enkel [!DNL Varnish] Konfiguration med SSL-avslut](../assets/performance/images/single-varnish-with-ssl-termination.png)

För webbplatser som kräver hög tillgänglighet rekommenderar vi att du använder en [!DNL Varnish] konfiguration med en SSL som avslutar belastningsutjämnaren.

![Hög tillgänglighet i två nivåer [!DNL Varnish] konfiguration med SSL som avslutar belastningsutjämnaren](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
