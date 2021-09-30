---
title: Principles of Platform Development
description: Understand fundamental platform development principles when working with Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Principles of platform development

I den här spelboken fördjupar vi oss i några av de viktigaste standarderna för utveckling av Adobe Commerce, bland annat:

- Funktionell och teknisk omfattning i linje med utvecklingsprocessen
- Utveckla bästa praxis som är anpassad till MVC-arkitekturen
- Arkitektöverväganden, inklusive GRA
- Säkerhetsstandarder mot skript och explosioner
- Bästa praxis för utveckling av tillägg
- Web API integrations with REST, SOAP, and GraphQL
- Prestandaförbättringar för kodning och infrastruktur
- Testverktyg, strategier och metoder

While some solution implementers may have their own preferences when it comes to the methodologies, processes, and tools used throughout an implementation project, this playbook focuses on generally accepted best practices and methodologies that can be shared across the majority of implementations.

Precis som alla andra stora IT-projekt bygger Adobe Commerce på kodningsstandarder som utnyttjar bästa praxis och standardiseringar för underliggande tekniker (till exempel PHP/Zend, Symfony, JavaScript, jQuery och HTML), samt standarder som har upprättats inom Adobe Commerce Coding Standard. Att följa dessa standarder är ett absolut måste för att eliminera buggar och förbättra kvaliteten på och underhållet i skräddarsydd kod.

## Adobe Commerce on cloud infrastructure

Adobe Commerce on cloud infrastructure is a managed, automated hosting platform for the Adobe Commerce software. Adobe Commerce on cloud infrastructure comes with a variety of additional features that sets it apart from on-premises Adobe Commerce and Magento Open Source implementations:

![Komponentgrafik i Adobe Commerce](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce on cloud infrastructure tillhandahåller en företablerad infrastruktur som omfattar PHP-, MySQL-, Redis-, RabbitMQ- och Elasticsearch-teknik. Ett Git-baserat arbetsflöde med automatiska bygg- och driftsättningsåtgärder för effektiv snabb utveckling och kontinuerlig driftsättning varje gång kodändringar görs i en plattformsmiljö som en tjänst-miljö (PaaS). mycket anpassningsbara filer och verktyg för miljökonfiguration, och AWS som erbjuder en skalbar och säker miljö för onlineförsäljning och -detaljhandel.

![Komponentgrafik i Adobe Commerce](../../assets/playbooks/cloud-tech-stack.svg)
