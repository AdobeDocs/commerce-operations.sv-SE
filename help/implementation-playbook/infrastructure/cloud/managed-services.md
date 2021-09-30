---
title: Managed Services
description: Granska ansvarsområdena för Adobes hanterade tjänster, kunder och molntjänsteleverantörer för din Adobe Commerce om implementering av molninfrastruktur.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# Hanterade tjänster

Adobe Commerce för molninfrastrukturhanterade tjänster är som standard säkra.

![Bild som visar Adobe Commerce Managed Services](../../../assets/playbooks/managed-services.svg)

## Delat ansvar

Adobe Commerce Pro-planer bygger på en säkerhetsmodell för delat ansvar. I den här modellen har olika parter olika ansvarsområden för att upprätthålla systemets säkerhet. Med den här metoden kan du både använda och flexibelt molnteknologi av allra högsta klass.

![Diagram som visar modellen för delat ansvar i Adobe Commerce](../../../assets/playbooks/shared-responsibility.svg)

### Adobe Managed Services responsibility

Adobes hanterade tjänster ansvarar för säkerheten och tillgängligheten för molnmiljön i Adobe Commerce Pro, den centrala programkoden för Adobe Commerce Pro samt för de interna handelssystemen. Detta omfattar, men är inte begränsat till:

- Korrigering på servernivå
- Tillhandahålla de tjänster som krävs för att leverera planer för Adobe Commerce Pro
- Sårbarhetstestning
- Loggning och övervakning av säkerhetshändelser
- Ärendehantering
- Operativ övervakning
- Support dygnet runt, alla dagar
- Säkerställa att kundinfrastrukturen är tillgänglig i enlighet med serviceavtal

Adobes hanterade tjänster hanterar även konfigurationer av serverns brandvägg (iptables) och brandväggskonfigurationer för perimetrar (säkerhetsgrupper). Adobe får också regelbundet släppa säkerhetsuppdateringar i kärnapplikationen. Det är kundens ansvar att tillämpa dessa korrigeringsfiler. Dessa områden omfattas alla av PCI-certifieringen av Adobe Commerce för molninfrastruktursystem.

### AWS-ansvarsområden

Adobes hanterade tjänster använder Amazon Web Services (AWS) för molnserverinfrastrukturen. AWS ansvarar för säkerheten i nätverket, inklusive routning, växling och perimeternätverkssäkerhet via brandväggssystem och system för intrångsdetektering (IDS). AWS ansvarar för den fysiska säkerheten för de datacenter som hanterar molnmiljöerna i Adobe Commerce samt för miljösäkerheten för att säkerställa att det finns korrekta kontroller för ström, kylning och mekanism.

Adobe Commerce Pro-planer använder:

- Amazon Elastic Compute Cloud (EC2)
- Amazon Simple Storage Service (S3)
- Amazon Elastic Block Store (EBS)
- Amazon Virtual Private Cloud (VPC)
- Amazon Elastic Load Balancer (ELB)
- Tjänster för spårning i Amazon Cloud.

Amazon har ett omfattande kompatibilitetsprogram som omfattar PCI DSS-, SOC 2- och ISO 27001-certifieringar.

### Partners/kundansvar

Kunden ansvarar i första hand för säkerheten i den anpassade implementeringen av det Adobe Commerce-program som körs i molnmiljön för Adobe Commerce Pro. Detta omfattar följande:

- Säkerställa en säker konfiguration och kodning av applikationen och säkerhetsövervakning, inklusive penetrationstestning och regelbundna säkerhetsinskanningar.

- Säkerheten för alla anpassningar, tillägg, andra program eller integreringar som används i systemet.

- Användarnas säkerhet och beviljandet av åtkomst till deras konfiguration och tillämpning.

- Kunden styr all koddistribution till icke-produktionsmiljöer. Den här kontrollen har också ansvaret för att lägga in programsäkerhetspatchar i Adobe Commerce-programmet, tillägg eller annan anpassad kod.

- Kunden bör göra penetrationstester av sin anpassade tillämpning. Dessa ansvarsområden kan hanteras av tekniska resurser av kund, implementeringspartner eller Adobe Commerce Professional Services.

- Kunderna ansvarar för PCI-kraven för sina anpassade applikationer och sina egna processer. Kundens efterlevnad av PCI bygger på PCI-certifieringarna för AWS och Adobe Commerce för att minimera de områden som måste granskas.
