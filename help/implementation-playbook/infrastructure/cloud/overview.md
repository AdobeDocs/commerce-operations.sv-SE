---
title: Översikt över molninfrastruktur
description: Läs mer om Adobe Commerce om molninfrastruktur.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---


# Ökning

Ett av de populäraste värdalternativen för Adobe Commerce på AWS erbjuds av Adobe Commerce. Adobe Commerce i molninfrastruktur är en helhanterad automatiserad värdplattform för Adobe Commerce-program.

Adobe Commerce i molninfrastruktur är en lösning för att hantera plattforms-as-service (PaaS) som möjliggör snabb driftsättning av fullt anpassningsbara, säkra och skalbara webbutiker i kombination med en ledande hosting- och Managed Services-infrastruktur. Det finns två planer med olika infrastrukturer. Adobe Commerce [Starter](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#starter-projects) passar bäst för mindre butiker med mindre komplexitet och mindre kataloger. Adobe Commerce [Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#pro-projects) Planerna är utformade för större butiker med större komplexitet, större produktkataloger eller trafik som når toppar. Adobe fastställer lämplig arkitektur med synpunkter från partners.

Adobe Commerce är molnklart med en helt redundant hosting-infrastruktur i flera moln som ger optimerade prestanda, flexibilitet och elastisk skalbarhet. Du kan effektivt köra din handelsplattform på Fastly&#39;s content delivery network (CDN), och med New Relic för övervakning och hantering kan du få din butiksmiljö att fungera smidigt.

Adobe Commerce erbjuder alla fördelar med modern molnbaserad datoranvändning som vanligtvis är kopplad till SaaS-lösningar samtidigt som man behåller flexibiliteten i programvaruanpassningen:

- Elastisk skalbarhet
- Hög motståndskraft och tillgänglighet
- PCI-kompatibilitet
- Global tillgänglighet och automatiserad korrigering

![Bild som visar arkitektoniska element i Adobe Commerce på molninfrastruktur](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Fördelar

Andra fördelar med Adobe Commerce är:

- **Optimerat för Adobe Commerce**. Adobe Commerce-utvecklade byggskript och tjänstekonfigurationer säkerställer att alla instanser är korrekt justerade och konfigurerade för optimala handelsprestanda.

- **Enhetliga, säkra releaser**. Alla koddistributioner är Git-baserade för konsekvens och repeterbarhet, med skrivskyddade produktionsmiljöer för ökad säkerhet.

- **Flexibilitet för partners**. Ett fullt REST API och ett skriptbart kommandoradsgränssnitt säkerställer enkel integrering med externa system och kompatibilitet med befintliga arbetsflöden för kodhantering.

- **Flexibla verktyg för driftsättning**. Snabb snurra upp, sammanfoga, klona och slipp obegränsade miljöer efter behov för utvecklingsuppgifter, kvalitetstestning eller diagnos av produktionsproblem.

- **Kontinuerlig molnleverans**. Gå tryggt direkt från utveckling till UAT till produktion, på ett kontinuerligt sätt mellan olika kodgrenar och utvecklingsteam.

## Tredjepartstjänster

I det här avsnittet sammanfattas viktiga tredjepartstjänster och verktyg för Adobe Commerce i projekt för molninfrastruktur. Se [Teknikstack](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/tech-stack.html) i _Molnguide_ för mer information.

- **Snabb CDN**: När kunderna kommer åt er webbplats och era butiker går förfrågningarna igenom snabbt för att läsa in cachelagrade sidor snabbare. WAF erbjuder snabbt även en DDoS-skyddstjänst.

- **New Relic**: Ger en fullständig bild av dina program och din operativmiljö. Med New Relic kan ni kombinera viktiga mätvärden från mobil- och webbläsarapplikationer med stödtjänster, datalager och värdar så att ni kan optimera prestandan på ett enhetligt sätt och se till att alla initiativ blir framgångsrika.

- **Disposition**: Hanterar beroenden och uppgraderingar i Adobe Commerce och ger innehåll om de inkluderade paketen, vad paketen gör och hur de passar ihop.

- **Git**: Tillhandahåller källkodshantering. Git möjliggör lokal förgrening, bekväma mellanlagringsplatser och flera arbetsflöden med automatisk konstruktion och driftsättning för snabb utveckling och kontinuerlig driftsättning.

- **Platform-as-a-Service (PaaS)**: Tillhandahåller en förprovisionerad infrastruktur som omfattar PHP, MySQL, Redis, [!DNL RabbitMQ]och OpenSearch eller Elasticsearch.

- **AWS eller Azure&#39;s cloud hosting**: Powers the underliggande Infrastructure-as-a-Service (IaaS), which offers a scalable and secure environment for online sales and retailing.
