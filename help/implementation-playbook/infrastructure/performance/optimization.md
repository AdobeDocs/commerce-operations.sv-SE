---
title: Prestandaoptimering
description: Lär dig allt om prestandaoptimering och åtgärder som ska vidtas för att granska resultatet av implementeringen av Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Prestandaoptimering

Prestanda är ett stort ämne. När en webbplats är långsam eller inte svarar påverkas konverteringen. Vi rekommenderar att du följer dessa steg för att optimera prestanda för din Adobe Commerce när det gäller implementering av molninfrastruktur:

- Utvärdera problemet
- Mät prestanda
- Identifiera en del av systemet som är kritisk för prestandaförbättring
- Ändra en del av systemet för att ta bort flaskhalsen
- Mät prestanda efter ändring
- Om du är bättre kan du använda den eller återställa den

## Vanliga prestandaproblem

The impact of a slow experience is usually defined by two indicators, and each factor can be caused for tons of reasons.

TTFB (High time-to-first-byte) betraktas vanligtvis som en indikator som definierar serverns svarshastighet. The time not only comes from source code execution for handling the request, but it can also be impacted by the following factors:

- DNS-sökning
- Långsam fråga från DB-lager
- CPU-tid från varje programlager
- Minnesbegränsning
- I/O-väntetiden kan påverka både läsning och skrivning av filer, ansluta tjänsten via socket
- Programinställningar (nginx, PHP, MySQL, Redis, Varnish)
- Nätverksbandbredd
- Felaktig cachelagring
- Felaktig kod
- Felaktig integreringsmetod
- Dependency of slow third-party service response
- Arkitektur utan skalbarhet

Långsammare inläsning betraktas vanligtvis som en indikator som definierar den statiska resursen (CSS, JavaScript, bilder, videor, Ajax-anropssvar från tredje part).

Adobe Commerce kan skalas upp med er verksamhet genom sina funktioner:

![Diagram som visar Adobe handels skalbara kapacitet](../../../assets/playbooks/scalable-capabilities.svg)

Det finns också viktiga faktorer som driver på handelns skala, vilket också påverkar det övergripande resultatet.

- Komplex och stor produktkatalog
- Ett stort antal administratörer
- Globala butiker
- Högvarig trafik
- Expanding touchpoints
- Transaktioner med stora volymer

För skalbara och cacheable-arkitekturer kan du använda det här diagrammet som referens.

![Bild som visar hur du använder API:t för GraphQL i Adobe Commerce i en cachebar arkitektur](../../../assets/playbooks/cacheable-architecture.svg)
