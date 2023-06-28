---
title: Managed Services
description: Granska ansvarsområdena för Adobes hanterade tjänster, kunder och molntjänsteleverantörer för din Adobe Commerce när det gäller implementering av molninfrastruktur.
exl-id: b1442e31-06f4-4aa6-b24a-b6cda630d52f
feature: Cloud, Services
source-git-commit: 7c2e2bdabf47e1367ffb6761230d3d43f0f9d0cf
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Hanterade tjänster

Adobe Commerce i molninfrastrukturhanterade tjänster är som standard säkra.

![Bild som visar Adobe Commerce hanterade tjänster](../../../assets/playbooks/managed-services.svg)

## Delat ansvar

Adobe Commerce Pro-planer bygger på en säkerhetsmodell för delat ansvar. I den här modellen har olika parter olika ansvarsområden för att upprätthålla systemets säkerhet. Med den här metoden kan du både använda och flexibelt molnteknologi av allra högsta klass.

![Diagram som visar Adobe Commerce modell för delat ansvar](../../../assets/playbooks/shared-responsibility.svg)

### Adobes hanterade tjänster

Adobes hanterade tjänster ansvarar för säkerheten och tillgängligheten för Adobe Commerce Pro-molnmiljön, Adobe Commerce Pro-programkoden och interna handelssystem. Detta omfattar, men är inte begränsat till:

- Korrigering på servernivå
- tillhandahålla Adobe Commerce Pro-planer
- Sårbarhetstestning
- Loggning och övervakning av säkerhetshändelser
- Ärendehantering
- Operativ övervakning
- Support dygnet runt, alla dagar
- Säkerställa att kundinfrastrukturen är tillgänglig i enlighet med serviceavtal

Adobes hanterade tjänster hanterar även konfigurationer av serverns brandvägg (iptables) och brandväggskonfigurationer för perimetrar (säkerhetsgrupper). Adobe får också regelbundet släppa säkerhetsuppdateringar i kärnapplikationen. Det är kundens ansvar att tillämpa dessa korrigeringsfiler. Dessa områden omfattas alla av PCI-certifieringen av Adobe Commerce i molninfrastruktursystemet.

### AWS ansvarsområden

Adobes hanterade tjänster använder Amazon Web Services (AWS) för molnserverinfrastrukturen. AWS ansvarar för säkerheten i nätverket, inklusive routning, växling och perimeternätverkssäkerhet via brandväggssystem och system för intrångsdetektering (IDS). AWS ansvarar för fysisk säkerhet för de datacenter som hanterar Adobe Commerce molnmiljöer samt för miljösäkerhet för att säkerställa att ström-, kylnings- och mekanismkontroller finns på plats.

Adobe Commerce Pro-planer använder:

- Amazon Elastic Compute Cloud (EC2)
- Amazon Simple Storage Service (S3)
- Amazon Elastic Block Store (EBS)
- Amazon Virtual Private Cloud (VPC)
- Amazon Elastic Load Balancer (ELB)
- Tjänster för spårning i Amazon Cloud.

Amazon har ett omfattande kompatibilitetsprogram som omfattar PCI DSS-, SOC 2- och ISO 27001-certifieringar.

### Partners/kundansvar

Kunden ansvarar främst för säkerheten vid den anpassade implementeringen av Adobe Commerce-programmet som körs i Adobe Commerce Pro-planens molnmiljö. Detta omfattar följande:

- Säkerställa en säker konfiguration och kodning av applikationen och säkerhetsövervakning, inklusive penetrationstestning och regelbundna säkerhetsinskanningar.

- Säkerheten för alla anpassningar, tillägg, andra program eller integreringar som används i systemet.

- Användarnas säkerhet och beviljandet av åtkomst till deras konfiguration och tillämpning.

- Kunden styr all koddistribution till icke-produktionsmiljöer. Den här kontrollen har också ansvaret för att lägga in programsäkerhetspatchar i Adobe Commerce kärnprogram, tillägg eller annan anpassad kod.

- Kunden bör göra penetrationstester av sin anpassade tillämpning. Dessa ansvarsområden kan hanteras av tekniska resurser av kunder, implementeringspartners eller Adobe Commerce professionella tjänster.

- Kunderna ansvarar för PCI-kraven för sina anpassade applikationer och sina egna processer. Kundens PCI-kompatibilitet bygger på PCI-certifieringarna för AWS och Adobe Commerce för att minimera de områden som måste granskas.
