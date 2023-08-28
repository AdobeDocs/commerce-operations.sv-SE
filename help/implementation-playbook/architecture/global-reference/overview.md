---
title: Global referensarkitektur
description: Få ut mesta möjliga av er Adobe Commerce-implementering genom att utnyttja en global referensarkitektur.
exl-id: a18529a3-da9b-4e1b-8048-0a906e65c740
feature: Deploy
source-git-commit: d33d1e24c38984d0abf0c7f8f5ad2eb804ff621d
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Global referensarkitektur (GRA)

>[!VIDEO](https://video.tv.adobe.com/v/3410528/?quality=12&learn=on)

När man driver företag som har flera webbplatser för flera varumärken på flera lokala marknader (med lokaliserade valutor, språk, medier, delade kataloger och unika kundvagnar) och som vill undvika onödiga kostnader för implementering av samma funktioner och integreringar är GRA alltid ett bra alternativ.

![Tabell som förklarar kostnaderna för skillnader i arkitektur](../../../assets/playbooks/divergent-architecture.svg)

![Tabell som förklarar kostnaden för konsoliderad arkitektur](../../../assets/playbooks/consolidated-architecture.svg)

GRA är:

- En implementeringsstrategi
- En distributionsstrategi
- En processstyrningsmodell

GRA är inte:

- En&quot;funktion&quot;
- Unikt för alla handelsplattformar
- Endast för globala affärssyften

GRA-effekter:

- Hur koden levereras

   - Bygg runt specifikt avsedda kodarkiv, som levererar olika upplevelser.

- Hur affärssystemen är integrerade

   - Konsoliderar kopplingar till affärssystem per varumärke och/eller region.

- Hur anpassning utvecklas och underhålls

   - Ser till att anpassningarna är centraliserade och domänspecifika så att all anpassning görs ur ett helhetsperspektiv för företaget.

- Hur nya marknader aktiveras

   - Förenklar lanseringen av flera kanaler och marknader som annars skulle kosta betydligt mer tid och pengar.

>[!TIP]
>
>Se [GRA-exempel](examples.md).
