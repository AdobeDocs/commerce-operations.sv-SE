---
title: Servicenivåavtal
description: Lär dig mer om servicenivåavtal och hur du använder dem för att stödja implementeringen av Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---


# Servicenivåavtal (SLA)

I serviceavtalet (SLA) definieras den servicenivå som en kund från tjänsteleverantören förväntar sig, med enkla mått som tjänsten mäts med, samt eventuella korrigerande åtgärder eller påföljder om de överenskomna servicenivåerna inte skulle uppnås.

SLA:erna för olika typer av incidentkritiska händelser kan avtalas, underhållas och mätas. Svarstypen kan dessutom ha flera standarder (Gold, Platinum), baserat på kundens behov av service.

I följande tabell beskrivs en typisk SLA-metrisk uppdelning med flera tjänstenivåer:

<table>
<thead>
  <tr>
    <th>Ärendetyp</th>
    <th>Effekt</th>
    <th>Exempel</th>
    <th colspan="2">Svars-/återställningstid under kontorstid som stöds</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="3"></td>
    <td>Guld</td>
    <td>Platinum</td>
  </tr>
  <tr>
    <td>P1</td>
    <td>Kritisk påverkan</td>
    <td>Tjänsten är inaktiv eller oanvändbar</td>
    <td>1 timme/4 timmar</td>
    <td>1 timme/4 timmar</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Tjänsten är inte tillgänglig</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Tjänsten är oanvändbar i alla slutanvändare</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P2</td>
    <td>Hög effekt</td>
    <td>Tjänsten är allvarligt skadad</td>
    <td>2 timmar/12 timmar</td>
    <td>2 timmar/8 timmar</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Tjänstprestanda är försämrad</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Tjänsten är tillgänglig, men genererar viktiga felmeddelanden</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P3</td>
    <td>Medelstor påverkan</td>
    <td>Tjänsten är delvis skadad</td>
    <td>8 timmar/16 timmar</td>
    <td>8 timmar/12 timmar</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Felmeddelanden genererade, ingen märkbar effekt för slutanvändaren</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Frågor om funktioner som används vid kundlansering</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

## Täckningsalternativ

Täckningsalternativen för implementerade servicenivåavtal varierar beroende på olika typer av erbjudanden. Vanligtvis ser supporttjänsterna Gold och Platinum ut ungefär så här:

![Infografik som visar alternativ för SLA-täckning](../../assets/playbooks/sla-coverage-options.svg)
