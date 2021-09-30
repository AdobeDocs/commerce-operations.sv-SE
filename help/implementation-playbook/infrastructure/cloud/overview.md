---
title: Översikt över molninfrastruktur
description: Läs om Adobe Commerce om molninfrastruktur.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---


# Översikt

En av de vanligaste värdalternativen för Adobe Commerce på AWS erbjuds av Adobe Commerce. Adobe Commerce on cloud infrastructure är en helhanterad automatiserad värdplattform för Adobe Commerce-programmet.

Adobe Commerce on cloud infrastructure är ett paket för att plattforms-as-service (PaaS) som möjliggör snabb driftsättning av fullt anpassningsbara, säkra och skalbara webbutiker i kombination med en ledande infrastruktur för hosting och hanterade tjänster. Det finns två planer med olika infrastrukturer. Adobe Commerce Starter passar bäst för mindre butiker med mindre komplexitet och mindre kataloger. Adobe Commerce Pro är byggt för större butiker med större komplexitet, större produktkataloger eller trafik som når ända fram. Adobe Commerce kommer att fastställa lämplig arkitektur med synpunkter från partners.

Adobe Commerce är molnklar med en helt redundant hosting-infrastruktur i flera moln som ger optimerade prestanda, flexibilitet och elastisk skalbarhet. Du kan effektivt köra din handelsplattform på Fastly&#39;s content delivery network (CDN), och med New Relic för övervakning och hantering kan du få din butiksmiljö att fungera smidigt.

Adobe Commerce erbjuder alla fördelar med modern cloud computing som vanligtvis är kopplade till SaaS-lösningar: elastisk skalbarhet, hög motståndskraft och tillgänglighet, PCI-kompatibilitet och global tillgänglighet och automatiserad korrigering, samtidigt som den flexibilitet i programvaruanpassningen som våra handlare kräver bibehålls.

![Diagram som visar arkitektoniska element i Adobe Commerce om molninfrastruktur](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Fördelar

Andra fördelar med Adobe Commerce är:

- **Optimerat för Adobe Commerce**. Adobe Commerce-utvecklade byggskript och tjänstekonfigurationer säkerställer att alla instanser är korrekt justerade och konfigurerade för optimala handelsprestanda.

- **Enhetliga, säkra releaser**. Alla koddistributioner är Git-baserade för konsekvens och repeterbarhet, med skrivskyddade produktionsmiljöer för ökad säkerhet.

- **Flexibilitet för partners**. Ett fullt REST API och ett skriptbart kommandoradsgränssnitt gör det enkelt att integrera med externa system och kompatibiliteten med befintliga arbetsflöden för kodhantering.

- **Flexibla verktyg** för driftsättning. Snabb snurra upp, sammanfoga, klona och slipp obegränsade miljöer efter behov för utvecklingsuppgifter, kvalitetstestning eller diagnos av produktionsproblem.

- **Kontinuerlig molnleverans**. Gå tryggt direkt från utveckling till UAT till produktion, på ett kontinuerligt sätt mellan olika kodgrenar och utvecklingsteam.

## Tredjepartstjänster

Låt oss också titta på programvaran som gör Adobe Commerce till verklighet.

![Bild som visar Adobe Commerce i molninfrastrukturens teknikstack](../../../assets/playbooks/cloud-tech-stack.svg)

- Snabb CDN: När kunderna kommer in på er webbplats och i era butiker går förfrågningarna igenom snabbt för att läsa in cachelagrade sidor snabbare. Snabbt erbjuder WAF även DDoS-skyddstjänster.

- Med New Relic får du en komplett bild av dina program och din operativmiljö. Ni kan kombinera viktiga mätvärden från mobil- och webbläsarapplikationer med stödtjänster, datalager och värdar så att ni kan optimera prestandan på ett enhetligt sätt och se till att alla initiativ blir framgångsrika.

- Composer hanterar beroenden och uppgraderingar i Adobe Commerce och ger kontext om de inkluderade paketen, vad paketen gör och hur de passar ihop.

- Git är din kod i databaser. Det ger lokal förgrening, praktiska mellanlagringsplatser och flera arbetsflöden med automatisk konstruktion och driftsättning för snabb utveckling och kontinuerlig driftsättning.

- Platform-as-a-Service (PaaS) tillhandahåller en förprovisionerad infrastruktur som omfattar PHP, MySQL, Redis, RabbitMQ och Elasticsearch.

- AWS eller Azure’s cloud hosting driver den underliggande Infrastructure-as-a-Service (IaaS), som erbjuder en skalbar och säker miljö för onlineförsäljning och webbutik.
