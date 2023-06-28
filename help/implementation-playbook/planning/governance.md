---
title: Projektledning
description: Använd våra rekommendationer för projektstyrning i er implementering av Adobe Commerce.
exl-id: adf53a2a-1673-441a-84d3-4cdda47d6aa5
feature: Best Practices
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# Projektstyrning

Projektstyrning är en tillsynsfunktion som är anpassad till organisationens styrningsstruktur och omfattar projektets livscykel. Det ger projektledaren och teamet struktur, processer, beslutsmodeller och verktyg för att hantera och styra projektet, samtidigt som man ser till att projektet genomförs korrekt. Projektstyrning är en viktig faktor, särskilt för komplexa och strategiska projekt.

I styrningsmodellen definieras, dokumenteras och kommuniceras anpassade och effektiva rutiner för att tillhandahålla en heltäckande metod för att styra projektet och ge periodisk synlighet på alla nivåer för att säkerställa framgång. Det innehåller en ram för beslutsfattande. Definiera roller, ansvar och ansvar för projektets genomförande. och styr effektiviteten. Styrningsstrukturen samlas i ledningsgruppen hela vägen till den verkställande ledningen, där man definierar aktiviteter, rapportering, eskalering och informationsflöde.

![Infografik om projektstyrning](../../assets/playbooks/project-governance.svg)

På olika nivåer undersöker teamen specifika käpp- och projektmått för att förstå framstegen och vidta nödvändiga åtgärder. Dessa värden för Sprint-nivå kan omfatta hastigheten och nedbränningen av varje sprint.

## Regelbunden mötesinformation

- Kvartalsvis affärsöversyn

   - Diskutera strategier för eskalering av tillväxt

   - Markera aktuella framgångar och mål

   - Justera efter önskade resultat för de kommande kvartalen

- Månatlig styrkommitté

   - Koordinera och granska projektförloppet

   - Beslutsfattande om viktiga påverkansfaktorer (om sådana finns)

   - Drömttheten säkerställer att kundnöjdheten och farhågorna registreras och åtgärdas

- Projektkommitté varje vecka

   - besluta om mål, plan, organisation för veckan

   - Fatta arkitekturbeslut efter behov

   - Granska och agera på projektstatusrapporter

   - Demonstrera plattform och funktioner

   - Eskalera förfrågningar/problem/förslag

- Dagligt möte

   - Diskutera och följ upp konkreta saker, inklusive aktuella tidningar/ritytor/utestående biljetter

   - Övervaka projektförlopp

## KPI:er för prestanda

Förutom Sprint-mätvärdena är det också viktigt att mäta nyckeltal för projekt- och kvalitetsprestanda. Detta bidrar inte bara till att säkerställa kvalitetsnivån i hela planen, det håller teamet på rätt spår och förhindrar att projektet rullar av.

## Storyboard och hastighet

![Exempel på Kanban-tavla](../../assets/playbooks/kanban-board-chart.svg)

## Sprint- och release-bränning

![Exempeldiagram över nedladdning av tidpunkter](../../assets/playbooks/sprint-release-burndown.svg)

Utmaningar eller förändringar inträffar under hela projektet. Att ge rätt personer i organisationen möjlighet att spåra, mäta och vrida när en utmaning är klar ökar sannolikheten för att du kommer ut ur projektet när du har nått dina mål och är nöjd med resultatet.

<table>
<thead>
  <tr>
    <th>Mätning av nyckelprestanda</th>
    <th>Måttenhet</th>
    <th>Rapporterade mått</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Testtäckning</td>
    <td>%</td>
    <td>Antal testbara krav som täcks av provningsfall VS Totalt antal testbara grundtester</td>
  </tr>
  <tr>
    <td>Defekt densitet</td>
    <td>%</td>
    <td>Antal giltiga fel som påträffats VS Totalt antal testfall som körts</td>
  </tr>
  <tr>
    <td>Defekt läckage till SIT/UAT/produktion</td>
    <td>%</td>
    <td>Defekter rapporterade i produktion VS Defekter rapporterade i produktion + Defekter rapporterade av QA+UAT</td>
  </tr>
  <tr>
    <td>Testeffektivitet</td>
    <td>%</td>
    <td>Giltiga defekter upphöjda/giltiga defekter upphöjda nekade defekter</td>
  </tr>
  <tr>
    <td>Kodkvalitet</td>
    <td># + %</td>
    <td>Komplexitet, LoC, Felaktiga radbyten, Kodtäckning för fjädringen</td>
  </tr>
</tbody>
</table>
