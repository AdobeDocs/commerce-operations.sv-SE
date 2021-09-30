---
title: Cloud Infrastructure Technologies
description: Ta en närmare titt på den samling teknik vi använder för Adobe Commerce om molninfrastruktur.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Technologies

Som vi har nämnt utnyttjar Adobe Commerce ett antal programlösningar för att stödja plattformen. Vi har i synnerhet, eftersom det gäller produktion, delat upp några av de tekniska lösningar och funktioner som ingår i Adobe Commerce för molninfrastruktur som hjälper er att få ut det mesta av er produktionsmiljö.

![Diagram som visar Adobe Commerce on cloud Infrastructure technology](../../../assets/playbooks/infrastructure-technology.svg)

## Software solutions

- **Nginx**—Web server using PHP-FPM. There is one instance with multiple workers.

- **GlusterFS**—File server for managing all static file deployments and synchronization with four directory mounts:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis**—One server per VM with only one active and the other two as replicas.

- **Elasticsearch** - Sök efter Adobe Commerce version 2.2.x och senare.

- **Galera** - Databaskluster med en MariaDB MySQL-databas per nod med en autostegsinställning på tre för unika ID:n i alla databaser.

## Funktioner och fördelar

- With three dedicated instances in a VPC, there is an elastic load balancer across three separate availability zones or data centers.

- Högre återhämtningsgrad ges mot händelser som kan göra att en enda instans misslyckas. Exempel: ett avbrott i en hel AWS-tillgänglighetszon eller datacenter.

- Zero downtime scaling across the entire stack, including web, caching, search, and database, in less than 15 minutes.
