---
title: Delat ansvar
description: Läs mer om säkerhetsansvar för alla parter som deltar i ditt Adobe Commerce i molninfrastrukturprojekt.
source-git-commit: d216418c69cb972e93c04b5d5cc0a8ab0495653d
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 0%

---


# Säkerhetsmodell för delat ansvar

Adobe Commerce i molninfrastruktur är en lösning för att hantera plattforms-as-service (PaaS) som bygger på en säkerhetsmodell för delat ansvar. Adobe, handlaren, molnleverantören och leverantören av leveransnätverk (CDN) har alla ett tydligt ansvar för att upprätthålla Adobe Commerce säkerhet för molninfrastrukturapplikationer och handlarspecifika koder och tillägg.

Med den här metoden kan handlare utforma och implementera en mycket flexibel, anpassningsbar och skalbar lösning som bäst passar deras verksamhetskrav samtidigt som man minimerar det operativa ansvaret och kostnaderna.

Adobe ansvarar i allmänhet för att utveckla och underhålla säker kärnapplikationskod, upprätthålla säkerheten på plattformen, säkerställa att plattformens SOC 2- och PCI-kompatibilitet och dess kompatibilitet med PCI-kompatibla teknikkomponenter (till exempel PHP, Redis) samt svara på säkerhetsfrågor som rör kärnplattformen. Adobe ansvarar också för samarbetet med molnleverantörer och CDN-partners för att lösa problem som kan uppstå.

Handlarna ansvarar för att upprätthålla säker, anpassad kod och integreringar med tredjepartsprogram, säkerställa säker applikationsutveckling, erhålla PCI-certifiering om handlarens betalningsprocessor begär det samt reagera på och hantera säkerhetsincidenter.

## Adobe ansvarsområden

Adobe ansvarar för säkerheten och tillgängligheten för Adobe Commerce i molninfrastruktursmiljön och för Adobe Commerce kärnkod för molninfrastrukturslösningar. Dessutom ansvarar Adobe för de åtgärder och mekanismer som krävs för att upprätthålla Adobe Commerce säkerhet när det gäller molninfrastrukturslösningen, inklusive:

- Tillämpa säkerhetsfunktioner och korrigeringsfiler på servernivå för program som stöds av Adobe Commerce i molninfrastrukturen, som molndatalagring och sökfunktioner
- Genomföra penetrationstestning och skanning av Adobe Commerce kärnkod i molninfrastrukturkoden
- Genomföra halvårsvisa granskningar/granskningar av den offentliga molntjänstleverantörens lösning för identitets- och behörighetshantering (IAM) och behörighetshantering (PCI-kompatibilitetskrav)
- Genomföra halvårsvisa granskningar/revisioner av behöriga användare, inklusive anställda och entreprenörer i Adobe (krav på efterlevnad av PCI)
- Genomföra årlig testning och dokumentation av funktioner för säkerhetskopiering och återställning
- Konfigurera server- och perimeterbrandväggar
- Ansluta och konfigurera Adobe Commerce i molninfrastrukturdatabasen
- Definiera, testa, implementera och dokumentera katastrofåterställningsplaner (DR) för de områden inom Adobe ansvarsområde
- Definiera brandväggsregler för webbprogram på den globala plattformen (WAF)
- Förbättra operativsystemet
- Implementera och underhålla integreringen av lösningar för nätverk för innehållsdistribution (CDN) och hantering av programprestanda (APM) med Adobe Commerce i molninfrastruktur
- Periodiska säkerhetsuppdateringar och andra uppdateringar för Adobe Commerce om molninfrastrukturkoden (det är handlarens ansvar att tillämpa korrigeringsfiler)
- Hantera support och åtkomstkontroller för handlare (till exempel Zendesk)
- Övervaka, logga och åtgärda säkerhetsincidenter som rör Adobe Commerce om infrastruktur för molninfrastruktur
- Övervaka plattformsdriften och tillhandahålla support dygnet runt för Adobe Commerce på återförsäljare av molninfrastruktur
- Etablera produktions- och stagningsmiljöer
- Utvärdering av potentiella säkerhetshot mot plattformsdrift och infrastruktur
- Skalning av databehandling, lagring, rutnät och andra resurser, enligt beskrivningen i serviceavtalet med handlaren
- Konfigurera DNS (endast Adobe Commerce för infrastruktur i molnet)
- Testa plattformen med avseende på säkerhetsbrister

Medan Adobe upprätthåller PCI-certifiering för den infrastruktur och de tjänster som används i Adobe Commerce drift av molninfrastrukturslösningen ansvarar handlarna för att den anpassade koden, system- och nätverksprocesserna och organisationen följs.

Adobe garanterar också att det finns tillgång till handlarens infrastruktur enligt vad som överenskommits i tillämpligt SLA.

## Handläggaransvar

Handlaren ansvarar för följande säkerhetsrutiner för sin specifika, anpassade instans av Adobe Commerce om molninfrastrukturslösningar och för:

- Lägga till nödvändiga Adobe Commerce i konfigurationsfiler för molninfrastruktur i databasen
- Använda säkerhetsuppdateringar och andra korrigeringsfiler för sina anpassade Adobe Commerce-lösningar för molninfrastruktur omedelbart efter att de släppts av Adobe
- Använda säkerhetsuppdateringar och andra korrigeringsfiler för alla anpassade tillägg och kod, omedelbart efter att de släppts av leverantören
- Skapa, distribuera och testa anpassade VCL-filer för lack
- Utforma, utforma, anpassa, installera, integrera och skydda den anpassade Adobe Commerce-lösningen för molninfrastruktur, inklusive alla anpassade tillägg och kod
- Bevilja och återkalla användaråtkomst till handlarens instans av Adobe Commerce för konfiguration, tillämpning och plattform av molninfrastruktur
- Hantera säkerhetsproblem relaterade till handlarens interna nätverk, servrar, infrastruktur och eventuella anpassade program som bygger på Adobe Commerce på molninfrastrukturplattformen
- Installera Adobe Commerce på kommandoradsverktyget för molninfrastruktur (CLI)
- Upprätthålla PCI-kompatibilitetsnivån för den anpassade applikationen och andra interna processer, enligt riktlinjerna för PCI-DSS

  >[!NOTE]
  >
  >Handlarens PCI-kompatibilitet bygger på PCI-certifieringarna för Adobe Commerce i molninfrastrukturen och molnleverantören för att minimera de områden som måste granskas.

- Köra PCI ASV-sökningar och åtgärdar problem i Adobe Commerce-kärnan i molninfrastrukturkoden och -plattformen
- Övervaka alla programaktiviteter som kan avslöja ett potentiellt säkerhetshot, inklusive penetrationstestning, sårbarhetsinskannningar och loggar
- Övervaka och hantera säkerhetsincidenter, inklusive kriminalteknik, reparationer och rapportering som rör handlarens Adobe Commerce om molninfrastrukturslösningar och användarkonton
- Hämta en DNS-provider och konfigurera och underhålla alla säljarspecifika DNS-poster
- Köra prestandatester på det anpassade programmet
- Skydda åtkomst till plattformskonton, instansåtkomst och program
- Testning och kvalitetskontroll av det anpassade programmet
- Upprätthålla säkerheten i alla system och nätverk som handlaren ansluter till Adobe Commerce i molninfrastrukturapplikationen

## Ansvarsområden för molntjänsteleverantörer

Adobe förlitar sig på väletablerade molntjänsteleverantörer för att vara värd för Adobe Commerce molnserverinfrastruktur i molninfrastrukturen. Dessa leverantörer ansvarar för säkerheten i nätverket, inklusive routning, växling och perimeternätverkssäkerhet via brandväggssystem och system för intrångsdetektering (IDS). Tjänsteleverantörer i molnet ansvarar också för den fysiska säkerheten i datacenter som är värdar för Adobe Commerce på molninfrastrukturslösningen och för datacentrets miljösäkerhet.

Molntjänsteleverantörer ansvarar också för:

- Underhåll PCI DSS-, SOC 2- och ISO 27001-certifieringar för deras molntjänster
- Skydda hypervisorn
- Skydda datacentret, inklusive både fysisk åtkomst och nätverksåtkomst

## CDN-leverantörsansvar

Adobe Commerce lösning för molninfrastruktur använder CDN-leverantörer för att snabba upp sidinläsningen, cachelagra innehåll och omedelbart rensa bort föråldrat innehåll. Dessa leverantörer ansvarar också för säkerhetsfrågor som har direkt samband med eller påverkar deras CDN samt för att definiera och underhålla CDN WAF-regler.

## Diagram över säkerhetsansvarsområden

I följande diagram används RACI-modellen (R - Ansvarig, A - Räkenskaplig, C - Consulted, I - Informated) för att visuellt beskriva varje part i ekosystemets säkerhetsansvar för Adobe Commerce i modellen för delat ansvar för molninfrastruktur:

<table>
<thead>
  <tr>
    <th>Uppgift</th>
    <th>Adobe</th>
    <th>Merchant</th>
    <th>Molntjänstleverantör</th>
    <th>CDN-provider</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Använda Adobe Commerce på molninfrastrukturkorrigeringar</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Tillämpa korrigeringsfiler på stödtjänster<br>(till exempel Nginx, MySQL)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Definiera WAF-ursprungsregler</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Definiera CDN WAF-regler</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Distribuera plattformens WAF-regler</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Distribuera CDN WAF-regler</td>
    <td>A</td>
    <td>I</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Åtgärda kärnfel i Adobe Commerce i molninfrastrukturkoden</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Frigör Adobe Commerce om molninfrastrukturkorrigeringar</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Skalning (beräkning och lagring)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Skala (Banor/rutnät)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Säkerställa åtkomst till källkod, inklusive repo.magento.com</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installera Adobe Commerce i CLI-verktyget för molninfrastruktur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Lägga till Adobe Commerce i konfigurationsfiler för molninfrastruktur i databasen</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Skapa ett projekt för handlaren (startgränssnitt)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Ansluta databaser till Adobe Commerce i molninfrastruktur</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Konfigurerar källdatabasen<sup>1</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Skapa en användare för versionshanteraren (startgränssnitt)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Distribuera kod i produktion</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Distribuera kod till mellanlagring</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Integrera externa program och tillägg</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installera tillägg</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Anpassa Adobe Commerce för molninfrastruktur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Testa prestanda hos anpassade Adobe Commerce-program i molninfrastruktur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Testa anpassade program</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Tema och design för anpassade tillämpningar</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
    <tr>
    <td>Skapa, distribuera och testa anpassade VCL:er för lack</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Konfigurera DNS (endast plattformsinfrastruktur)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Utveckla CDN-tillägg och åtgärda fel</td>
    <td>A</td>
    <td>C</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>CDN för introduktion</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Stöd för CDN<sup>2</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Konfigurera New Relic APM/infrastruktur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installera New Relic APM/infrastruktur</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Stöd för New Relic APM/infrastruktur</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Konfigurerar Nginx<sup>3</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Hämtar DNS-provider (endast Pro)</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Förbättra operativsystemet</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Etablera produktions- och stagningsmiljöer</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Åtkomst till Zendesk för Adobe Commerce i molninfrastruktur</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Lösa säkerhetsproblem för handlare</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Lösa säkerhetsproblem i molninfrastruktur med Adobe Commerce</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Lösa CDN-säkerhetsproblem</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Lösa säkerhetsproblem i APM</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Att bistå Adobe med säkerhetsforskning (programvara)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Att bistå Adobe med säkerhetsforskning (inskannade dokument/revisioner)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Utföra PCI ASV-skanningar</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Reparera Adobe Commerce på PCI-skanningar i molninfrastruktur<sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Reparera PaaS PCI-skanningar</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Hantera operativsystems- och plattformshemligheter</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Hantera Adobe Commerce om krypteringsnycklar för molninfrastruktur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Skanna skräddarsydda Adobe Commerce på molninfrastrukturinstanser</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Övervaka säkerhetsloggar</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Hantera IAM och behörigheter för Adobe Commerce i molninfrastrukturen</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Hantera åtkomstkontroller (Teleport)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Kontrollera stöd och åtkomst för handlare</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Årlig testning och dokumentation av planen för Adobe DR samt säkerhetskopiering och återställning</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Årlig testning och dokumentation av katastrofåterställningsplanen</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup> Endast om Adobe Commerce i molninfrastrukturdatabasen används som huvuddatabas. Handlaren ansvarar själv för att andra externa arkiv används.</p>
      <p><sup><strong>2</strong></sup> Adobe tillhandahåller nivå 1-stöd för problem med CDN-leverantörer.</p>
      <p><sup><strong>3</strong></sup> Vissa Ngnix-kontroller konfigureras av handlaren för deras program och är deras ansvar.</p>
      <p><sup><strong>4</strong></sup> För PCI delas kraven på penetrationstestning mellan Adobe och handlaren.</p>
    </td>
  </tr>
</tfoot>
</table>
