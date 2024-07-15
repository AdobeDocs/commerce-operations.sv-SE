---
title: Principer för plattformsutveckling
description: Förstå grundläggande principer för plattformsutveckling när du arbetar med Adobe Commerce.
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
feature: Cloud
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Principer för plattformsutveckling

Det här avsnittet går djupare in i några av de viktigaste standarderna för Adobe Commerce utveckling, bland annat:

- Funktionell och teknisk omfattning i linje med utvecklingsprocessen
- Utveckla bästa praxis som är anpassad till MVC-arkitekturen
- Arkitektöverväganden, inklusive GRA
- Säkerhetsstandarder mot skript och explosioner
- Bästa praxis för utveckling av tillägg
- Web API-integrationer med REST, SOAP och GraphQL
- Prestandaförbättringar för kodning och infrastruktur
- Testverktyg, strategier och metoder

Vissa implementerare kan ha egna preferenser för metoder, processer och verktyg, men den här spelboken fokuserar på vedertagna bästa metoder och metoder som kan delas i de flesta implementeringar.

Precis som alla andra stora IT-projekt bygger Adobe Commerce på kodningsstandarder som använder bästa praxis och standardiseringar samt standarder som har upprättats i Adobe Commerce [Coding Standard](https://developer.adobe.com/commerce/php/coding-standards/). Att följa dessa standarder är viktigt för att eliminera buggar och förbättra kvaliteten och underhållet i skräddarsydd kod.

## Adobe Commerce i molninfrastruktur

Adobe Commerce i molninfrastruktur är en hanterad, automatiserad värdplattform för Adobe Commerce. Adobe Commerce i molninfrastruktur har olika funktioner som skiljer den från lokala Adobe Commerce-implementeringar. Se [molnguiden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/overview.html).
