---
title: Global referensarkitektur
description: Få ut mesta möjliga av er Adobe Commerce-implementering genom att utnyttja en global referensarkitektur.
feature: Deploy
hide: true
hidefromtoc: true
exl-id: a18529a3-da9b-4e1b-8048-0a906e65c740
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Global referensarkitektur (GRA)

>[!VIDEO](https://video.tv.adobe.com/v/3410528/?quality=12&learn=on)

När man driver företag som har flera webbplatser för flera varumärken på flera lokala marknader (med lokaliserade valutor, språk, medier, delade kataloger och unika kundvagnar) och som vill undvika onödiga kostnader för implementering av samma funktioner och integreringar är GRA alltid ett bra alternativ.

![Tabell som förklarar kostnaden för skillnader i arkitektur](../../../assets/playbooks/divergent-architecture.svg)

![Tabell som förklarar kostnaden för konsolidering i arkitektur](../../../assets/playbooks/consolidated-architecture.svg)

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
