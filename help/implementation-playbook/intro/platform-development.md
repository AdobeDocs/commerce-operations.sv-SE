---
title: Principer för plattformsutveckling
description: Förstå grundläggande principer för plattformsutveckling när du arbetar med Adobe Commerce.
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Principer för plattformsutveckling

I den här spelboken fördjupar vi oss i några av de viktigaste standarderna för Adobe Commerce-utveckling, bland annat:

- Funktionell och teknisk omfattning i linje med utvecklingsprocessen
- Utveckla bästa praxis som är anpassad till MVC-arkitekturen
- Arkitektöverväganden, inklusive GRA
- Säkerhetsstandarder mot skript och explosioner
- Bästa praxis för utveckling av tillägg
- Webb-API-integrering med REST, SOAP och GraphQL
- Prestandaförbättringar för kodning och infrastruktur
- Testverktyg, strategier och metoder

Vissa implementerare kan ha egna preferenser när det gäller de metoder, processer och verktyg som används i ett implementeringsprojekt, men den här spelboken fokuserar på allmänt vedertagna bästa metoder och metoder som kan delas av de flesta implementeringar.

Precis som alla andra stora IT-projekt bygger Adobe Commerce på kodningsstandarder som utnyttjar bästa praxis och standardiseringar för underliggande tekniker (till exempel PHP/Zend, Symfony, JavaScript, jQuery och HTML), samt standarder som har upprättats inom Adobe Commerce Code Standard. Att följa dessa standarder är ett absolut måste för att eliminera buggar och förbättra kvaliteten på och underhållet i skräddarsydd kod.

## Adobe Commerce i molninfrastruktur

Adobe Commerce i molninfrastruktur är en hanterad, automatiserad värdplattform för Adobe Commerce. Adobe Commerce i molninfrastruktur har en mängd andra funktioner som skiljer den från lokala Adobe Commerce- och Magento Open Source-implementeringar:

![Adobe Commerce-komponentinfografik](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce i molninfrastruktur erbjuder en företablerad infrastruktur som omfattar PHP-, MySQL-, Redis-, RabbitMQ- och Elasticsearch-teknik. Ett Git-baserat arbetsflöde med automatiska bygg- och driftsättningsåtgärder för effektiv snabb utveckling och kontinuerlig driftsättning varje gång kodändringar görs i en plattformsmiljö som en tjänst-miljö (PaaS). mycket anpassningsbara filer och verktyg för miljökonfiguration, och AWS hosting som erbjuder en skalbar och säker miljö för onlineförsäljning och detaljhandel.

![Adobe Commerce-komponentinfografik](../../assets/playbooks/cloud-tech-stack.svg)
