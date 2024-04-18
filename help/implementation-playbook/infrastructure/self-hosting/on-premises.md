---
title: Lokal infrastruktur
description: Läs om Adobe Commerce lokala infrastruktur och molntjänster från tredje part.
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
feature: Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Lokal infrastruktur hos Adobe Commerce

Det finns många skäl att starta en ny Adobe Commerce-implementering eller flytta en befintlig lokal Adobe Commerce-implementering till molnet, men de vanligaste strategiska faktorerna är att minska kapitalutgifter, minska de löpande kostnaderna, förbättra skalbarheten och elasticiteten, förbättra time-to-market och uppnå förbättringar i säkerhet och regelefterlevnad.

I följande diagram visas referensarkitekturen för driftsättning av Adobe Commerce lokalt i AWS infrastruktur. Andra molnleverantörer som Azure, Google Cloud och Alibaba Cloud delar en liknande infrastrukturdesign och homologa tjänster.

![Bild som visar Adobe Commerce-infrastruktur för värdtjänster på molntjänster från tredje part](/help/assets/playbooks/on-premises-infrastructure.svg)

Låt oss fördjupa oss i rollerna och funktionerna i varje aspekt av den infrastruktur som visas ovan:

1. Amazon Route 53 tillhandahåller DNS-konfiguration.

1. AWS WAF är en brandvägg för webbapplikationer som skyddar Adobe Commerce mot vanliga webbexplosioner.

1. Amazon CloudFront är ett snabbt leveransnätverk (CDN) som snabbar upp distributionen av statiskt och dynamiskt webbinnehåll.

1. Den första Elastic Load Balancing-programmet för belastningsutjämning fördelar trafik mellan olika instanser i en AWS-grupp för automatisk skalning i flera tillgänglighetszoner.

1. Finska cacheminnet är en webbprogramsaccelerator som cachelagrar HTTP-omvänd proxy. Enterprise-versionen, som finns på AWS Marketplace, rekommenderas eftersom den har bättre funktioner för molnbaserade backends och cache-rensning över dynamiska värdar.

1. Den andra belastningsutjämnande programmet Elastic Load Balancing fördelar trafik från Varnish Cache över AWS Auto Scaling-gruppen av Adobe Commerce-instanser i flera tillgänglighetszoner.

1. Installera den senaste versionen av Adobe Commerce på Amazon EC2-instanser. Installationen består av Adobe Commerce-programmet, Nginx-webbservern och PHP. Bygg Amazon Machine Image (AMI) för att starta nya instanser i en grupp för autoskalning.

1. Amazon Elasticsearch Service är en hanterad Elasticsearch-tjänst för katalogsökning i Adobe Commerce.

1. Amazon ElastiCache for Redis innehåller ett cachelagringslager för databasen.

1. Använd Amazon Aurora eller AmazonRDS för att förenkla databasadministrationen (inklusive hög tillgänglighet och multikörningskonfiguration).

1. EFSMount Target underlättar mappningen av Amazon elastic File System (AmazonEFS) till instanser i Varnish och Adobe Commerce.

1. Använd Amazon EFS för att få åtkomst till delad konfiguration i lack och delade medieresurser i Adobe Commerce-instanser.

## Molntjänster

Förutom att tillhandahålla en stödjande teknikplattform för att möjliggöra DevOps-processer på AWS i hela Adobe Commerce-miljön erbjuder AWS en samling tjänster som kan tillhandahålla (i avsaknad av) eller förstärka era befintliga lösningar för programkonfigurationshantering (SCM). Detta inkluderar AWSCodeCommit, AWSCodeBuild, AWSCodePipeline och AWSCodeDeploy, som möjliggör en hanterad källkontroll, bygge, kontinuerlig integrering/kontinuerlig driftsättning (CI/CD) och driftsättningstjänster.

## Molnmigrering

Prisvärda erbjudanden för migrering av Adobe Commerce till AWS förbättras ytterligare genom att det finns flera tjänster som ger driftsinsikter och flexibilitet. Vad vi menar är operativ insikt i plattformen inte bara ur ett tekniskt perspektiv (till exempel förfrågningar per timme) utan även ur ett affärsmässigt perspektiv (till exempel order per timme), särskilt när de två uppsättningarna data kan vara gifta. Detta ger en inramning i realtid av kampanjresultat, kostnader för plattformsdrift och ett nästan oändligt antal andra indikatorer.

Adobe Commerce-installation på AWS kan ersätta specifika programberoenden med fullt hanterade alternativ som finns i molnet. I stället för att ha en relationsdatabas direkt på EC2-instanser kan databasen för många program enkelt ersättas med Amazon Relational Database Service (AmazonRDS). Fördelen med denna strategi är att driftansvaret för de olika komponenterna kan överföras till AWS utan att man behöver göra några större förändringar i kärnapplikationen.

Det finns flera distributionsalternativ för att köra Adobe Commerce på AWS. Det lämpligaste valet beror på era krav på kostnad, storlek, tillgänglighet och flexibilitet, liksom på organisationens kunskaper inom AWS och Adobe Commerce.

{{$include /help/_includes/hosting-related-links.md}}
