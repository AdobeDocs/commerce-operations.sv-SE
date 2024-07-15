---
title: Prestandaoptimering
description: Lär dig allt om prestandaoptimering och steg som krävs för att se hur din Adobe Commerce-implementering fungerar.
exl-id: 506ef2cc-c6fd-4401-afa5-a71e7b9871e6
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Prestandaoptimering

Prestanda är ett stort ämne. När en webbplats är långsam eller inte svarar påverkas konverteringen. Vi rekommenderar att du följer de här stegen för att optimera prestanda för din Adobe Commerce när det gäller implementering av molninfrastruktur:

- Utvärdera problemet
- Mät prestanda
- Identifiera en del av systemet som är kritisk för prestandaförbättring
- Ändra en del av systemet för att ta bort flaskhalsen
- Mät prestanda efter ändring
- Om du är bättre kan du använda den eller återställa den

## Vanliga prestandaproblem

Effekten av en långsam upplevelse definieras vanligen av två indikatorer, och varje faktor kan orsakas av många olika anledningar.

TTFB (High time-to-first-byte) betraktas vanligtvis som en indikator som definierar serverns svarshastighet. Tiden kommer inte bara från körning av källkod för att hantera begäran, utan kan också påverkas av följande faktorer:

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
- Beroende av långsam service från tredje part
- Arkitektur utan skalbarhet

Långsammare inläsning betraktas vanligtvis som en indikator som definierar den statiska resursen (CSS, JavaScript, bilder, videor, Ajax-anropssvar från tredje part).

Adobe Commerce kan byggas ut med verksamheten genom sina funktioner:

![Diagram som visar de skalbara funktionerna i Adobe Commerce](../../../assets/playbooks/scalable-capabilities.svg)

Det finns också viktiga faktorer som driver på handelns skala, vilket också påverkar det övergripande resultatet.

- Komplex och stor produktkatalog
- Ett stort antal administratörer
- Globala butiker
- Högvarig trafik
- Expandera kontaktytor
- Transaktioner med stora volymer

För skalbara och cacheable-arkitekturer kan du använda det här diagrammet som referens.

![Diagram som visar hur du använder Adobe Commerce GraphQL API i en tillgänglig arkitektur](../../../assets/playbooks/cacheable-architecture.svg)
