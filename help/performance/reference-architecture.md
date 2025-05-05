---
title: Referensarkitektur
description: Granska diagram över den rekommenderade referensarkitekturen för Adobe Commerce-distributioner.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Referensarkitektur

I det här avsnittet beskrivs en allmän rekommenderad konfiguration för Adobe Commerce-instanser med vanliga servrar som är fysiskt värdbaserade i ett datacenter (inte virtualiserade) där resurser inte delas med andra användare. Din värdleverantör, särskilt om den är specialiserad på Commerce högpresterande värdtjänster, kan rekommendera en annan konfiguration som är lika eller mer effektiv för dina behov.

Information om Adobe Commerce i molninfrastrukturmiljöer finns i [Startarkitektur](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/architecture/starter-architecture).

## [!DNL Commerce] referensarkitekturdiagram

Referensarkitekturdiagrammet [!DNL Commerce] representerar den bästa metoden för att konfigurera en skalbar [!DNL Commerce]-plats.

Färgen på varje element i diagrammet anger om elementet är en del av Magento Open Source eller Adobe Commerce och om det behövs.

* Orange-element krävs för Magento Open Source
* Grå element är valfria för Magento Open Source
* Blå element är valfria för Adobe Commerce

![Commerce referensarkitekturdiagram](../assets/performance/images/ref-architecture-2.3.png)

I följande avsnitt ges rekommendationer och överväganden för varje avsnitt i Commerce referensarkitekturdiagram.

### [!DNL Varnish]

* Ett [!DNL Varnish]-kluster kan skalas till trafik på en plats
* Justera instansstorleken baserat på antalet cachesidor som behövs
* På en webbplats med hög trafik använder du en [!DNL Varnish]-mallsida för att säkerställa att en begäran (högst) rensas på cachen per webbnivå

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

### Rekommenderad referensarkitektur för [!DNL Varnish]

Magento har stöd för flera cachelagringsmotorer för helsidesdata (Arkiv, Memcache, Redis, [!DNL Varnish]) som finns i paketet, tillsammans med utökad täckning via tillägg. [!DNL Varnish] är den rekommenderade helsidescachemotorn.  [!DNL Commerce] stöder många olika [!DNL Varnish]-konfigurationer.

För webbplatser som inte kräver hög tillgänglighet rekommenderar vi att du använder en enkel [!DNL Varnish]-konfiguration med Nginx SSL-avslutning.

![Enkel [!DNL Varnish] konfiguration med SSL-avslutning](../assets/performance/images/single-varnish-with-ssl-termination.png)

För platser som kräver hög tillgänglighet rekommenderar vi att du använder en [!DNL Varnish]-konfiguration på två nivåer med en SSL som avslutar belastningsutjämnaren.

![Konfiguration med hög tillgänglighet på två nivåer [!DNL Varnish] med SSL som avslutar belastningsutjämnaren](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
