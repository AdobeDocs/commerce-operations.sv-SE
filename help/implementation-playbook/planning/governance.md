---
title: Projektledning
description: Använd våra rekommendationer för projektstyrning i implementeringen av Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---


# Projektstyrning

Projektstyrning är en tillsynsfunktion som är anpassad till organisationens styrningsstruktur och omfattar projektets livscykel. Det ger projektledaren och teamet struktur, processer, beslutsmodeller och verktyg för att hantera och styra projektet, samtidigt som man ser till att projektet genomförs korrekt. Projektstyrning är en viktig faktor, särskilt för komplexa och strategiska projekt.

The governance model defines, documents, and communicates custom and effective practices to provide a comprehensive method of controlling the project and providing periodic visibility at every level to ensure success. It contains a framework for making decisions; defines roles, responsibilities, and liabilities for the accomplishment of the project; and governs the effectiveness. Styrningsstrukturen samlas i ledningsgruppen hela vägen till den verkställande ledningen, där man definierar aktiviteter, rapportering, eskalering och informationsflöde.

![Infografik om projektstyrning](../../assets/playbooks/project-governance.svg)

På olika nivåer undersöker teamen specifika käpp- och projektmått för att förstå framstegen och vidta nödvändiga åtgärder. Dessa värden för Sprint-nivå kan omfatta hastigheten och nedbränningen av varje sprint.

## Regular meeting details

- Quarterly business review

   - Discuss growth escalation strategies

   - Highlight current success &amp; goals

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

   - Escalate requests/issues/suggestions

- Dagligt möte

   - Discuss and follow up on action items, including current sprint/boards/outstanding tickets

   - Övervaka projektförlopp

## KPI:er för prestanda

Förutom Sprint-mätvärdena är det också viktigt att mäta nyckeltal för projekt- och kvalitetsprestanda. Detta bidrar inte bara till att säkerställa kvalitetsnivån i hela planen, det håller teamet på rätt spår och förhindrar att projektet rullar av.

## Storyboard and velocity

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
    <td>Test Coverage</td>
    <td>%</td>
    <td>Antal testbara krav som täcks av provningsfall VS Totalt antal testbara grundtester</td>
  </tr>
  <tr>
    <td>Defekt densitet</td>
    <td>%</td>
    <td># of valid Defects found VS Total of Test cases executed</td>
  </tr>
  <tr>
    <td>Defect Leakage to SIT/ UAT / Production</td>
    <td>%</td>
    <td>Defects reported in Production VS Defects reported in Production + Defects reported by QA+UAT</td>
  </tr>
  <tr>
    <td>Test Effectiveness</td>
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
