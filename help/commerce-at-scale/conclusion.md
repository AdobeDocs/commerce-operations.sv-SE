---
title: Slutsats
description: Läs mer om koncept i guiden Leverera Commerce Experiences på Scale.
source-git-commit: 1cff7359ddb4caeca6773ff74b92048c89676f12
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Slutsats

Innehållet är avsett att vara en guide på hög nivå för att tillhandahålla vissa områden att undersöka inledningsvis när ni förbereder er AEM/CIF/Adobe Commerce environment för laster. Det finns många områden inom Adobe Commerce, CIF och Fastly som inte omfattas av ovanstående handbok, vilket kommer att kräva optimeringar som är specifika för er miljö. Anpassad kod och moduler från tredje part kan dessutom påverka svarstiderna, vilket inte kan beskrivas här.

För att minska risken för att ändringar eller kod införs som kommer att påverka slutanvändarnas svarstider i AEM/CIF/Adobe Commerce bör det säkerställas att en grundlig och upprepningsbar strategi för prestandatestning införs, inklusive fastställande av nyckeltal som kan mätas över tid. Prestandatestning bör utföras inte bara innan du publicerar utan även efter publicering, helst före varje större release eller förändring av produktionsmiljöerna för att mäta eventuella prestandaeffekter.
