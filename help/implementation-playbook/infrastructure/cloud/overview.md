---
title: Översikt över molninfrastruktur
description: Läs om Adobe Commerce i molninfrastruktur.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Ökning

Ett av de populäraste värdalternativen för Adobe Commerce på AWS erbjuds av Adobe Commerce. Adobe Commerce i molninfrastruktur är en helhanterad automatiserad värdplattform för Adobe Commerce-program.

Adobe Commerce i molninfrastruktur är en lösning för att hantera plattforms-as-service (PaaS) som möjliggör snabb driftsättning av fullt anpassningsbara, säkra och skalbara webbutiker i kombination med en ledande infrastruktur för värdtjänster och hanterade tjänster. Det finns två planer med olika infrastrukturer. Adobe Commerce Starter passar bäst för mindre butiker med mindre komplexitet och mindre kataloger. Adobe Commerce Pro är skapat för större butiker med större komplexitet, större produktkataloger eller trafik som når ända fram. Adobe Commerce kommer att fastställa lämplig arkitektur med synpunkter från våra partners.

Adobe Commerce är molnklart med en helt redundant hosting-infrastruktur i flera moln som ger optimerade prestanda, flexibilitet och elastisk skalbarhet. Du kan effektivt köra din handelsplattform på Fastly&#39;s content delivery network (CDN), och med New Relic för övervakning och hantering kan du få din butiksmiljö att fungera smidigt.

Adobe Commerce erbjuder alla fördelar med modern molnbaserad datoranvändning som vanligtvis är kopplad till SaaS-lösningar: elastisk skalbarhet, hög återhämtningsförmåga och tillgänglighet, PCI-kompatibilitet samt global tillgänglighet och automatiserad korrigering, samtidigt som vi behåller flexibiliteten i den programvaruanpassning som våra handlare kräver.

![Bild som visar arkitektoniska element i Adobe Commerce på molninfrastruktur](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Fördelar

Andra fördelar med Adobe Commerce är:

- **Optimerat för Adobe Commerce**. Adobe Commerce-utvecklade byggskript och tjänstekonfigurationer säkerställer att alla instanser är korrekt justerade och konfigurerade för optimala handelsprestanda.

- **Enhetliga, säkra releaser**. Alla koddistributioner är Git-baserade för konsekvens och repeterbarhet, med skrivskyddade produktionsmiljöer för ökad säkerhet.

- **Flexibilitet för partners**. Ett fullt REST API och ett skriptbart kommandoradsgränssnitt gör det enkelt att integrera med externa system och kompatibiliteten med befintliga arbetsflöden för kodhantering.

- **Flexibla verktyg för driftsättning**. Snabb snurra upp, sammanfoga, klona och slipp obegränsade miljöer efter behov för utvecklingsuppgifter, kvalitetstestning eller diagnos av produktionsproblem.

- **Kontinuerlig molnleverans**. Gå tryggt direkt från utveckling till UAT till produktion, på ett kontinuerligt sätt mellan olika kodgrenar och utvecklingsteam.

## Tredjepartstjänster

Låt oss också titta på programmet som gör Adobe Commerce förmåner till verklighet.

![Bild som visar Adobe Commerce i molninfrastrukturens teknikstack](../../../assets/playbooks/cloud-tech-stack.svg)

- Snabbt CDN: När kunderna kommer åt er webbplats och era butiker går förfrågningarna igenom snabbt för att läsa in cachelagrade sidor snabbare. Snabbt erbjuder WAF även DDoS-skyddstjänster.

- New Relic ger dig en komplett bild av dina program och din operativmiljö. Ni kan kombinera viktiga mätvärden från mobil- och webbläsarapplikationer med stödtjänster, datalager och värdar så att ni kan optimera prestandan på ett enhetligt sätt och se till att alla initiativ blir framgångsrika.

- Composer hanterar beroenden och uppgraderingar i Adobe Commerce och ger kontext om de inkluderade paketen, vad paketen gör och hur de passar ihop.

- Git är din kod i databaser. Det ger lokal förgrening, praktiska mellanlagringsplatser och flera arbetsflöden med automatisk konstruktion och driftsättning för snabb utveckling och kontinuerlig driftsättning.

- Platform-as-a-Service (PaaS) tillhandahåller en förprovisionerad infrastruktur som inkluderar PHP, MySQL, Redis, [!DNL RabbitMQ]och OpenSearch eller Elasticsearch.

- AWS eller Azure:s molnhosting driver den underliggande infrastruktur-som-en-Service (IaaS), som erbjuder en skalbar och säker miljö för onlineförsäljning och -detaljhandel.
