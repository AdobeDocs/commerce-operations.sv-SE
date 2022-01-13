---
title: Adobe Commerce Microservices
description: Var i stånd att skilja mellan hälsa och mikrotjänster på samma sätt som i Adobe Commerce.
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
source-git-commit: 4e8f6ce05c14195433e7c46e6090a93a76b8b5f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Headless och microservices

Det är viktigt att inte blanda ihop headless med mikrotjänster. Vi hör ofta konversationer om mikrotjänster i samma mening som utan rubrik. De är helt olika saker. De kan användas tillsammans, men de är helt olika koncept.

En mikrotjänstarkitektur är en term som används för att beskriva metoden att dela upp en applikation i en samling av mindre, löst kopplade tjänster. Med mikrotjänsterna kan enskilda backend-tjänster vara:

- **Isolerade från varandra**—Till exempel är prissättningstjänsten inte beroende av katalogtjänsten.

- **Distribuerad en kundvagn**- Kunderna driftsätter endast de delar av programmet som de behöver.

- **Skala oberoende av varandra**—Resurser kan tilldelas till tjänster med hög efterfrågan, t.ex. lagersökning.

- **Autonom utveckling**—Kan utvecklas och driftsättas oberoende av varandra.

Mikrotjänster har ingenting att göra med att hugga av huvudet på e-handelsstacken eller API:erna. När vi tänker på de e-handelstjänster i kärnkoden som finns på Adobe Commerce bakkontor handlar det om att isolera dessa tjänster från varandra. Så en mikrotjänstarkitektur bryter löst upp alla tjänster som prissättnings-, katalogtjänst- och inventeringstjänster och gör var och en isolerad från varandra.

Mikrotjänster kan skalas oberoende och utvecklas självständigt. Microservices liknar en SaaS-utvecklingsprocess för flera innehavare. Många moderna SaaS-produkter med flera innehavare utvecklas med en strategi där flera tjänster används. Även Adobe egna SaaS-produkter, som orderhantering, det nya AI-drivna Recommendations-verktyget och andra SaaS-komponenter i Adobe Commerce, utvecklas med en strategi som bygger på mikrotjänster. För att vara mycket tydlig är Adobe Commerce 2.4.x inte en arkitektur för mikrotjänster utan en headless-arkitektur.
