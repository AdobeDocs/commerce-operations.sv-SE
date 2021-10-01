---
title: Effektiv cacheplanering
description: Se rekommenderade riktmärken för cachelagring för att säkerställa att webbplatsen som läses in fungerar som den ska.
source-git-commit: 41c0ba17b3d731a82ad6ecd8b16fac151a597e75
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# Planerar effektiv cachelagring för lyckad e-handel under inläsning

Att leverera en shoppingupplevelse under belastning kräver en välplanerad cachningsstrategi. Inledningsvis kan det vara så att företagsintressenter alltid visar produktdata i realtid för kunder, men det är inte en optimal användning av systemresurser, och effekterna av slutanvändarnas webbplatsprestanda skulle bli betydligt större än fördelarna med att konsekvent visa realtidsinformation.

Det inledande steget i cachningsstrategin bör därför vara att tillsammans med berörda intressenter definiera en matris med godtagbara tidsangivelser för cachning för olika delar av webbplatsen, till exempel:

| Cacheområde | Hur ofta ändras? | Inverkan om inaktuellt innehåll hanteras från cache | Godtagbar cachelagring av TTL (time-to-live)? |
|---------------------------------------------------------------|--------------------|-------------------------------------------|-----------------------------------------------------|
| HTML-sidor med webbplatsinnehåll, uppdaterade via CMS | Ovanligt | Låg | 1 dag |
| Mallmedier/resurser för webbplatsinnehåll - logotyp, CSS-design, bilder | Ovanligt | Låg | 1 vecka |
| Produktlistsidor (PLP) | Ovanligt | Medel | 1 dag |
| Produktinformationssida (PDP) | Ibland | Medel | 1 timme |
| Produktkategorier | Ovanligt | Medel | 1 dag |
| Priser | Ofta | Hög | Ingen cache |
| Lager/lager | Ofta | Hög | Ingen cache |
| Webbplatssökning | De flesta användare är unika | Medel | Cachelagra resultat från de 100 främsta sökfraserna under en dag |
| Utcheckning | Alla unika användare | Mycket hög | Ingen cache |
| Kundvagn | Alla unika användare | Mycket hög | Ingen cache |
| Betalningssidor | Alla unika användare | Mycket hög | Ingen cache |

När den här inledande planeringen är klar kan den tekniska konfigurationen börja användas för att konfigurera cacheminnen baserat på dessa krav.

Även om innehållet uppdateras och behöver göras tillgängligt i den cachelagrade TTL-nivån är det i de flesta fall möjligt att manuellt rensa cacheminnet för AEM avsändare och Adobe Commerce-cachen selektivt för det innehållet, vilket innebär att brådskande ändringar omedelbart kommer att återspeglas. Processen runt manuell cacherensning bör också planeras och testas i förväg, så om det behövs att manuellt framtvinga en uppdatering av visst innehåll, dokumenteras den i en körningsbok för webbplatsoperationer och klargör hur och vem som behöver göra detta. Här visas ett exempel på en manuell cacherensningsåtgärd för AEM och Adobe Commerce.
