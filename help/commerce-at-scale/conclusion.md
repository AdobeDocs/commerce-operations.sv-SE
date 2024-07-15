---
title: Slutsats
description: Läs mer om koncepten i guiden Leverera Commerce Experience at Scale.
exl-id: a5d5c398-451f-4283-b787-d16c7486e824
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Slutsats

Det här innehållet är avsett att vara en guide på hög nivå som ger dig möjlighet att undersöka vissa områden i början när du förbereder din AEM/CIF/Adobe Commerce-miljö för hög belastning. Det finns många områden i Adobe Commerce, CIF och Fastly som inte omfattas av guiden ovan, vilket kräver optimeringar som är specifika för just din miljö. Anpassad kod och moduler från tredje part kan dessutom påverka svarstiderna, vilket inte kan beskrivas här.

För att minska risken för att ändringar eller kod införs som negativt påverkar AEM/CIF/Adobe Commerce-slutanvändarnas svarstider bör det säkerställas att en grundlig och upprepningsbar strategi för prestandatestning införs, inklusive definition av nyckeltal som kan mätas över tid. Prestandatestning bör utföras inte bara innan du publicerar utan även efter publicering, helst före varje större release eller förändring av produktionsmiljöerna för att mäta eventuella prestandaeffekter.
