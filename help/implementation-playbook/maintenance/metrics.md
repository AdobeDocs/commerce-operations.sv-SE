---
title: Supportmått
description: Övervaka support- och underhållsarbete för implementeringen av Adobe Commerce med hjälp av gemensamma mätvärden.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Supportmått

I följande diagram visas typiska mått/KPI:er som samlats in och rapporterats för L1-funktioner:

![Diagram som visar SLA-mått](../../assets/playbooks/sla-metrics.svg)

Mätning och rapportering av L2-tjänster (förbättringar och valfria tjänster) liknar utvecklingsprojekt. L2-teamets resultat och framsteg mäts i mått som hastighet, kodkvalitet, testeffektivitet och produktivitet.

| Mätning av nyckelprestanda | Måttenhet | Rapporterade mått |
|------------------------------|---------------------|------------------------------------------------------------------------------------|
| Hastighet | Nummer | Nej. berättelser som teamet kunde leverera för tidningen |
| Effektivitet vid Sprint-åtagande | Procent | Totalt antal av Story Points allokerade mot Levererade för en Sprint |
| Sprint Burn down | Nummer | Diagram (Rapport, spårar slutförandet av arbetet genom hela tidningen) |
| Kodkvalitet | Siffror, procent | Komplexitet, LoC, Felaktiga radbyten, Kodtäckning för fjädringen |
| Kravens volatilitet | Nummer | Antal krav som ändras/totalt Antal krav för skrivaren |
| Defekt densitet | Procent | [Nej. av giltiga defekter/totalt antal testfall som utförts]*100 för sprint |
| Testeffektivitet | Procent | [Giltiga defekter upphöjda/(Giltiga defekter upphöjda+ Avvisade defekter)]*100 för fjädringen |
| Produktivitet | Antal (trend) | Artikelpunkter per källa/kapacitet |