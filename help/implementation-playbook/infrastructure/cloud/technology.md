---
title: Cloud Infrastructure Technologies
description: Ta en närmare titt på vår samling av teknik för Adobe Commerce i molninfrastruktur.
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
source-git-commit: 683ce0a72aca0319ade2e4ccfd7a8e541a228156
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Technologies

Som vi har nämnt utnyttjar Adobe Commerce ett antal programlösningar för att stödja plattformen. Vi har i synnerhet, eftersom det gäller produktion, delat upp några av de tekniska lösningar och funktioner som ingår i Adobe Commerce i molninfrastrukturen som hjälper er att få ut det mesta av er produktionsmiljö.

![Bild som visar Adobe Commerce om molninfrastruktursteknik](../../../assets/playbooks/infrastructure-technology.svg)

## Programvarulösningar

- **Nginx**—Webbserver med PHP-FPM. Det finns en instans med flera arbetare.

- **GlusterFS**—Filserver för hantering av alla statiska fildistributioner och synkronisering med fyra kataloginstallationer:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis**—En server per VM med endast en aktiv och de andra två som repliker.

- **Elasticsearch**—Sök efter Adobe Commerce version 2.2.x och senare.

- **OpenSearch**—Sök efter Adobe Commerce version 2.4.6 och senare.

- **Galera**—Databaskluster med en MariaDB MySQL-databas per nod med en inställning för automatisk ökning på tre för unika ID:n i alla databaser.

## Funktioner och fördelar

- Med tre dedikerade instanser i en VPC finns en elastisk belastningsutjämnare över tre separata tillgänglighetszoner eller datacenter.

- Högre återhämtningsgrad ges mot händelser som kan göra att en enda instans misslyckas. Exempel: ett driftstopp i en hel tillgänglighetszon eller ett helt datacenter i AWS.

- Ingen nedtidsskalning över hela stacken, inklusive webb, cachning, sökning och databas, på mindre än 15 minuter.
