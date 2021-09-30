---
title: Adobe Commerce Microservices
description: Be able to differentiate between healdess and microservices as it pertains to Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---


# Headless and microservices

Det är viktigt att inte blanda ihop headless med mikrotjänster. A lot of the time, we hear conversations about microservices in the same sentence as headless. They are completely different things. They can be used together, but they’re completely different concepts.

A microservices architecture is a term used to describe the practice of breaking up an application into a collection of smaller, loosely coupled services. Med mikrotjänsterna kan enskilda backend-tjänster vara:

- **Isolated from one another**—For exmaple, the pricing service has no dependency on the catalog service.

- **Driftsatt en kundvagn** - Kunderna driftsätter endast de delar av applikationen som de behöver.

- **Scale independently**—Resources can be assigned to high-demand services, such as inventory lookup.

- **Autonom utveckling** - Kan utvecklas och driftsättas oberoende av varandra.

Mikrotjänster har ingenting att göra med att hugga av huvudet på e-handelsstacken eller API:erna. När vi tänker på de handelstjänster i kärnkoden som ligger i Adobe Commerce handlar det om att isolera dessa tjänster från varandra. Så en mikrotjänstarkitektur bryter löst upp alla tjänster som prissättnings-, katalogtjänst- och inventeringstjänster och gör var och en isolerad från varandra. På så sätt kan du vara säker på att de är en vanlig kundvagn så att du inte behöver köpa och driftsätta all Adobe Commerce på en gång.

Microservices can be scaled independently and developed autonomously. Microservices liknar en SaaS-utvecklingsprocess för flera innehavare. Många moderna SaaS-produkter med flera innehavare utvecklas med en strategi där flera tjänster används. Även Adobe egna SaaS-produkter, som orderhantering, det nya AI-drivna Recommendations-verktyget och andra SaaS-komponenter i Adobe Commerce utvecklas med hjälp av en strategi med mikrotjänster. För att vara mycket tydlig är Adobe Commerce 2.4.x inte en arkitektur för mikrotjänster, utan snarare en headless-arkitektur.
