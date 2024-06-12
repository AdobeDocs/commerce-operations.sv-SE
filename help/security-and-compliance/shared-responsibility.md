---
title: Delat ansvar, säkerhet och operativ modell
description: Läs mer om säkerhetsansvar för alla parter som deltar i ditt Adobe Commerce i molninfrastrukturprojekt.
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: 76aafb88855f7f41db8e57b06cf0e82370b57302
workflow-type: tm+mt
source-wordcount: '2802'
ht-degree: 0%

---

# Delat ansvar, säkerhet och operativ modell

Adobe Commerce i molninfrastruktur är en lösning för att tillhandahålla en plattform som en tjänst (PaaS) som bygger på en säkerhetsmodell och en driftsmodell för delat ansvar. Dessa ansvarsområden delas mellan Adobe, handlaren, molnleverantören och innehållsleveransnätverkets leverantör (CDN). Varje part har ett tydligt ansvar för att skydda och driva Adobe Commerce-applikationen och den säljarspecifika kod och tillägg som distribueras i molninfrastrukturen.

Denna delade modell gör det möjligt för handlare att utforma och implementera en mycket flexibel, anpassningsbar och skalbar lösning som uppfyller deras verksamhetskrav samtidigt som man minimerar det operativa ansvaret och kostnaderna.

Adobe ansvarar i allmänhet för följande:

- Utveckla och underhålla säker applikationskod
- Upprätthålla plattformens säkerhet
- Säkerställa att plattformen är SOC 2- och PCI-kompatibel och kompatibel med PCI-kompatibla teknikkomponenter (till exempel PHP, Redis)
- Svara på säkerhetsfrågor som rör kärnplattformen
- Samarbeta med leverantörer av molntjänster och CDN-partners för att lösa problem som kan uppstå

Handlarna ansvarar för följande:

- Bevara säkerheten för anpassad kod och integrering med tredjepartsprogram
- Säker programutveckling
- Hämta PCI-certifiering om handlarens betalningsprocessor begär det
- Reagera på och hantera säkerhetsincidenter

## Adobe ansvarsområden

Adobe ansvarar för säkerheten och tillgängligheten för Adobe Commerce i molninfrastrukturen och för kärnlösningens kod. Dessutom ansvarar Adobe för de åtgärder och mekanismer som krävs för att upprätthålla Adobe Commerce säkerhet när det gäller molninfrastrukturslösningen, inklusive:

- Tillämpa säkerhetsfunktioner och korrigeringsfiler på servernivå för program som stöds av Adobe Commerce i molninfrastrukturen, som molndatalagring och sökfunktioner
- Genomföra penetrationstestning och skanning av Adobe Commerce kärnkod i molninfrastrukturkoden
- Genomföra halvårsvisa granskningar och granskningar av de offentliga molntjänstleverantörernas lösningar för identitets- och åtkomsthantering (IAM) och behörighetshantering (PCI-kompatibilitetskrav)
- Genomföra halvårsvisa granskningar och revisioner av behöriga användare, inklusive anställda och underleverantörer i Adobe (krav på efterlevnad av PCI)
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

Adobe underhåller PCI-certifiering för den infrastruktur och de tjänster som används för Adobe Commerce-lösningen.  Handlarna ansvarar för att den egna koden, systemet och nätverksprocesserna samt organisationen är kompatibla.

Adobe garanterar också att det finns tillgång till handlarens infrastruktur enligt vad som överenskommits i tillämpligt SLA.

## Handläggaransvar

Handlaren ansvarar för följande säkerhetsrutiner för sin specifika, anpassade instans av Adobe Commerce i molninfrastrukturslösningen:

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
  >För att minimera de områden som måste granskas bygger PCI-kompatibiliteten för handlaren på PCI-certifieringarna för Adobe Commerce och molnleverantören.

- Köra PCI ASV-sökningar och åtgärdar problem i Adobe Commerce-kärnan i molninfrastrukturkoden och -plattformen
- Övervaka alla programaktiviteter som kan avslöja ett potentiellt säkerhetshot, inklusive penetrationstestning, sårbarhetsinskannningar och loggar
- Övervaka och hantera säkerhetsincidenter, inklusive kriminalteknik, reparationer och rapportering som rör handlarens Adobe Commerce om molninfrastrukturslösningar och användarkonton
- Hämta en DNS-provider och konfigurera och underhålla alla säljarspecifika DNS-poster
- Köra prestandatester på det anpassade programmet
- Skydda åtkomst till plattformskonton, instansåtkomst och program
- Testning och kvalitetskontroll av det anpassade programmet
- Upprätthålla säkerheten i alla system och nätverk som handlaren ansluter till Adobe Commerce i molninfrastrukturapplikationen

## Leverantörens ansvar

Adobe förlitar sig på väletablerade molntjänsteleverantörer för att vara värd för Adobe Commerce molnserverinfrastruktur i molninfrastrukturen. Dessa leverantörer ansvarar för säkerheten i nätverket, inklusive routning, växling och perimeternätverkssäkerhet via brandväggssystem och system för intrångsdetektering (IDS). Tjänsteleverantörer i molnet ansvarar också för den fysiska säkerheten i datacenter som är värdar för Adobe Commerce på molninfrastrukturslösningen och för datacentrets miljösäkerhet.

Molntjänsteleverantörer ansvarar också för:

- Underhåll PCI DSS-, SOC 2- och ISO 27001-certifieringar för deras molntjänster
- Skydda hypervisorn
- Skydda datacentret, inklusive både fysisk åtkomst och nätverksåtkomst

## CDN-leverantörsansvar

Adobe Commerce lösning för molninfrastruktur använder CDN-leverantörer för att snabba upp sidinläsningen, cachelagra innehåll och omedelbart rensa bort föråldrat innehåll. Dessa leverantörer ansvarar också för säkerhetsfrågor som har direkt samband med eller påverkar deras CDN samt för att definiera och underhålla CDN WAF-regler.

## Sammanfattning av säkerhetsansvar

>[!BEGINSHADEBOX]

I följande sammanfattande tabell används RACI-modellen för att visa säkerhetsansvar som delas mellan Adobe, handlaren och molntjänstleverantören:

**R** — Ansvarig
**A** — Konto
**C** — Konsulterad
**I** - Informerad

>[!ENDSHADEBOX]

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
    <td>Tillämpa korrigeringsfiler på stödtjänster<br>(Till exempel Nginx eller MySQL.)</td>
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
    <td>Skalning (Banor och stödraster)</td>
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
    <td>Konfigurera källdatabasen<sup>1</sup></td>
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
    <td>Testa det anpassade programmet</td>
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
    <td>Konfigurera New Relic APM- och infrastrukturprogram</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installera New Relic APM- och infrastrukturprogram</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Stöd för New Relic APM- och infrastrukturapplikationer</td>
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
    <td>Hämta en DNS-provider (endast Pro)</td>
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
      <p><sup><strong>3</strong></sup> Handlaren ansvarar för alla Ngnix-kontroller som de konfigurerar för sina program.</p>
      <p><sup><strong>4</strong></sup> För PCI delas kraven på penetrationstestning mellan Adobe och handlaren.</p>
    </td>
  </tr>
</tfoot>
</table>

## Sammanfattning av operativt ansvar

>[!BEGINSHADEBOX]

Följande sammanfattande tabeller klargör det operativa ansvaret för Adobe och Merchants vid utveckling, driftsättning, underhåll och säkring av Adobe Commerce i molninfrastruktur.

>[!ENDSHADEBOX]

### Kodning och utveckling

#### Adobe Commerce Core-kod

|     | Adobe | Merchant |
| --- | --- | --- |
| Publicera uppdateringar och patchar till Adobe Commerce Core | R |     |
| Filsystemets tillgänglighet och korrigering | R |  |
| Publicera uppdateringar och patchar till ECE-Tools | R |     |
| Adobe Commerce programkvalitet | R |     |

{style="table-layout:auto"}

#### Koddatabas

|     | Adobe | Merchant |
| --- | --- | --- |
| repo.magento.com | R |     |
| Tillgänglighet för Adobe Commerce på Git-servern i molnet | R |     |
| Andra koddatabaser som valts av återförsäljaren (GitHub, Bitbucket, värdbaserad Git-server) |     | R |

{style="table-layout:auto"}

#### Cloud Docker

|     | Adobe | Merchant |
| --- | --- | --- |
| Göra Cloud Docker-behållare tillgängliga för hämtning | R |   |
| Driftsättning och installation av Cloud Docker (tillval) |     | R |
| Andra lokala utvecklingsinställningar |     | R |

{style="table-layout:auto"}

#### COMMERCE CLOUD CLI

|     | Adobe | Merchant |
| --- | --- | --- |
| Kontinuerlig kvalitet och uppdatering av ECE-verktyg | R |   |
| Installera den senaste versionen av ECE-verktyg |     | R |

{style="table-layout:auto"}

#### Anpassningar

|  | Adobe | Merchant |
| --- | --- | --- |
| Anpassade Adobe Commerce-moduler och -kod |     | R |
| Tillägg |     | R |
| Anpassade integreringar |     | R |

{style="table-layout:auto"}

#### Distributioner

|     | Adobe | Merchant |
| --- | --- | --- |
| Tillgänglighet till infrastruktur för att bygga och driftsätta kod | R |   |
| Konfiguration av befintlig kvalitet för byggprocess och driftsättning av infrastruktur | R |   |
| Konfiguration av byggbaserad och statisk innehållsdistribution |     | R |
| Bygga och köra distributionsstyrningsprocess: villkor och ändringshantering |     | R |
| Distribuera till mellanlagringsmiljön |     | R |
| Distribuera till produktionsmiljö |     | R |
| Produktionsåterställningar |     | R |

{style="table-layout:auto"}

#### Synkroniserar miljöer

Handlarna ansvarar för att synkronisera data mellan olika miljöer.

#### Lappa

|     | Adobe | Merchant |
| --- | --- | --- |
| Installera uppdateringar och patchar till ECE-Tools |     | R |
| Installera uppdateringar och patchar i Adobe Commerce Core |     | R |

#### Webbplatstillgänglighet

|  | Adobe | Merchant |
| --- | --- | --- |
| Anpassade Adobe Commerce-program och tillhörande webbplatser |     | R |

#### Prestanda

|     | Adobe | Merchant |
| --- | --- | --- |
| Programjustering och optimering | R |   |
| Anpassad kodjustering och optimering |     | R |
| Anpassad Adobe Commerce-kod |     | R |
| Läs in testning |     | R |
| Prestandatestning |     | R |

{style="table-layout:auto"}


#### Loggar och övervakning

|     | Adobe | Merchant |
| --- | --- | --- |
| Roterande loggar | R |   |
| Anpassat Adobe Commerce-program | | R |
| Tillgång till New Relic tjänster:<br>APM-applikationer och agentintegration, infrastrukturapplikation,<br>Loggning och integrering | R |   |
| Konfigurera New Relic Alerts |     | R |
| Distribuera New Relic Agent på PaaS-servrar |     | R |

{style="table-layout:auto"}

#### Felsökning och isolering av problem

|     | Adobe | Merchant |
| --- | --- | --- |
| Felsökning och isolering av problem | R | R |
| Stöd för felsökning i rätt tid och isoleringsprocess för problem |     | R |

{style="table-layout:auto"}

### Program- och tjänstkonfiguration

#### Commerce

|     | Adobe | Merchant |
| --- | --- | --- |
| Programkonfiguration |     | R |
| Lägga till domäner i Adobe Commerce-programmet (bas-URL:er) |     | R |
| Konfigurera PaaS för att använda tjänstversioner som stöds av den distribuerade Adobe Commerce-versionen<br><br>Olika Commerce-versioner är till exempel kompatibla med specifika versioner av PHP, Redis och så vidare. |     | R |

{style="table-layout:auto"}

#### Schemaläggning av uppgifter med cron-jobb

|     | Adobe | Merchant |
| --- | --- | --- |
| Tillgänglighet för standardcron-jobb | R | |
| Kontinuerlig kvalitet på anpassade cron-jobb |  | R |

{style="table-layout:auto"}

#### Meddelandeansvarig för meddelandeköramverket

|     | Adobe | Merchant |
| --- | --- | --- |
| RabbitMQ-tjänstens tillgänglighet | R |   |
| Konfiguration av RabbitMQ standardinställningar | R |   |
| Kontinuerlig kvalitet och patchning av RabbitMQ | R |   |
| Skicka en begäran om att få installera en RabbitMQ-version som är kompatibel med den installerade Adobe Commerce-versionen |   | R |

{style="table-layout:auto"}

#### PHP-tjänst

|     | Adobe | Merchant |
| --- | --- | --- |
| PHP-tillgänglighet | R |   |
| Konfiguration av PHP-standardinställningar | R |     |
| Konfiguration av anpassade PHP-inställningar |     | R |
| Konfiguration av YAML-fil för anpassning av PHP-versioner som är kompatibla med den installerade Adobe Commerce-versionen |    | R |

{style="table-layout:auto"}

#### Databastjänster

|     | Adobe | Merchant |
| --- | --- | --- |
| Tillgång till tjänsterna Galera och MariaDB | R | |
| Fortlöpande underhåll av standarddatabasinställningar<br><br>(indexera och optimera huvudtabeller, optimera standardinställningar för systemadministratörer) | R |   |
| Löpande underhåll av handlardata och ändrade inställningar<br><br>(konfigurera normaliserade och platta tabeller, indexera och optimera anpassade tabeller och tabeller från tredje part, arkivera eller ta bort data, konfigurera systemadministrationsinställningar) |     | R |
| Konfiguration av Galera och MySQL | R |   |
| Fortlöpande kvalitet och patchning av Galera och MariaDB | R |   |
| Kontinuerlig infrastrukturoptimering | R |   |
| Identifiera och korrigera långsamma frågor |     | R |
| Skicka en begäran om att få installera en MariaDB-version som är kompatibel med den installerade Adobe Commerce-versionen |     | R |
| Inställning och underhåll av affärsspecifika regler för datalagring (Adobe principer för datalagring definieras i handelsavtalet) |     | R |

{style="table-layout:auto"}

#### CDN-tjänst

|     | Adobe | Merchant |
| --- | --- | --- |
| CDN:s tillgänglighet och kvalitet | R |   |
| Snabb tjänstkonfiguration (via tillägg/API) |     | R |
| Snabb tilläggskvalitet | R |   |
| Snabb integrering av VCL-kodfragment (medföljer den snabba utökningen) | R |   |
| Optimering av sidcache |     | R |
| Lägga till domäner till tjänster, CDN och infrastruktur | R |   |
| Anpassade VCL-kodfragment |     | R |
| WAF- och WAF-regler | R |   |

{style="table-layout:auto"}

#### Cache-tjänst

|     | Adobe | Merchant |
| --- | --- | --- |
| Tillgång till Redis-tjänsten | R |   |
| Konfiguration av standardinställningar för Redis | R |   |
| Fortsatt kvalitet och patchning av Redis | R |   |
| Skicka en begäran om att få installera en Redis-version som är kompatibel med den installerade Adobe Commerce-versionen |     | R |

{style="table-layout:auto"}

#### Söktjänst

|     | Adobe | Merchant |
| --- | --- | --- |
| Elasticsearch är tillgängligt | R |   |
| Konfiguration av standardinställningar för Elasticsearch | R |   |
| Skicka en begäran om att få installera en Elasticsearch-version som är kompatibel med den installerade Adobe Commerce-versionen |  | R |

{style="table-layout:auto"}

#### E-posttjänst

|     | Adobe | Merchant |
| --- | --- | --- |
| E-posttjänsten SendGrid och dess integrering är tillgängliga | R |   |
| Övervaka handlarens SendGrid-användning mot begränsningar | R |   |
| Merchant ansvarar endast för att använda tjänsten för utgående transaktionsmeddelanden<br>Tjänsten stöder inte sändning av e-post för marknadsföring. |     | R |
| Konfigurera valfria e-posttjänster från tredje part |     | R |

{style="table-layout:auto"}

#### Tredjepartstjänster

|     | Adobe | Merchant |
| --- | --- | --- |
| Tillgång till och kvalitet på tredjepartstjänster |     | R |

{style="table-layout:auto"}

### Commerce Services-tillägg

#### Förhandsrapportering

|     | Adobe | Merchant |
| --- | --- | --- |
| Tillgång till den avancerade rapporteringstjänsten | R |   |
| Konfiguration av avancerad rapportering uppfyller villkoren för avancerad rapportering |     | R |

{style="table-layout:auto"}

#### Commerce Intelligence

|     | Adobe | Merchant |
| --- | --- | --- |
| Tillgänglighet för Adobe Commerce Business Intelligence | R |   |
| MBI-datasynkroniseringsprocesser | R |   |
| Identifiera MBI-synkroniseringsproblem | R |   |
| Konfigurera MBI-datasynkronisering till Adobe Commerce Cloud Pro, Starter, On Premises eller andra program än Adobe Commerce<br>(API, datakvalitet och dataformatering, handlarnätverk,<br>DB-anslutningar både innanför och utanför Adobe Commerce Cloud DB, över datatrösklar) |     | R |
| Konfigurerar MBI-datasynkronisering till Adobe Commerce Cloud Pro<br>(Adobe Commerce Cloud databaskonfiguration) | R |   |

{style="table-layout:auto"}

#### Recommendations

|     | Adobe | Merchant |
| --- | --- | --- |
| Tillgång till tjänsten Recommendations Product | R |   |

{style="table-layout:auto"}

### Nätverkstjänster

#### Bildoptimering

|     | Adobe | Merchant |
| --- | --- | --- |
| Tillgänglighet och kvalitet för bildoptimering | R |  |
| Konfiguration av bildoptimering |     | R |

{style="table-layout:auto"}

#### SSL-certifikat

|     | Adobe | Merchant |
| --- | --- | --- |
| SSL-dedikerat certifikat - utgångsdatum | R |  |
| Etablerar SSL-certifikat | R |  |
| Inköp och underhåll av EV/specifikt SSL-certifikat (annat än standardvärden) och tillhandahålls Adobe |     | R |

{style="table-layout:auto"}

#### Brandvägg för webbaserade program (WAF)

|     | Adobe | Merchant |
| --- | --- | --- |
| Tillgänglighet och konfiguration av WAF | R |  |
| Som vänder sig till falskt positiva värden för WAF-regel | R | |
| Felaktiga positiva rapporter i WAF-regel |     | R |
| WAF-regeljustering (STÖDS INTE) |     |     |
| WAF/CDN-loggar |     | R |

{style="table-layout:auto"}

#### DOS

|     | Adobe | Merchant |
| --- | --- | --- |
| Proaktiv IP-blockering |     | R |
| Punktskydd |     | R |
| DDOS-identifiering - lager 3-4 | R |   |
| DDOS-identifiering - lager 7 |     | R |
| DDOS-svar | R |   |
| Konfiguration av Snabb begränsning av utökningshastighet och punktskydd (begränsat) |     | R |

{style="table-layout:auto"}

#### Privat länk

|     | Adobe | Merchant |
| --- | --- | --- |
| Konfigurera och underhålla PrivateLink-anslutningar (om de används) med en VPC som ägs av Adobe | R |   |
| Konfigurera och underhålla PrivateLink-anslutningar (om de används) med en företagsägd VPC |     | R |
| SSH-tillgänglighet (icke-privat länk) | R |   |
| Konfiguration av PrivateLink inkommande till Adobe Commerce Cloud tjänstslutpunkt | R |   |
| Godkännande av PrivateLink inkommande till Adobe Commerce Cloud tjänstslutpunkt |     | R |
| Konfiguration av PrivateLink inkommande till Merchants VPC-tjänstslutpunkt |     | R |
| Godkännande av PrivateLink inkommande till Merchants VPC-tjänstslutpunkt | R |   |
| Konfiguration av PrivateLink-integreringar (slutpunkt till konto) |     | R |
| Konfiguration av handelsägd VPC för PrivateLink-slutpunkt<br><br> (inklusive eventuella VPN-anslutningar) |     | R |

{style="table-layout:auto"}

### System och infrastruktur

#### App Server

|     | Adobe | Merchant |
| --- | --- | --- |
| Nginx-tillgänglighet | R |   |
| Konfiguration av Nginx | R |   |
| Kontinuerlig kvalitet och patchning av Nginx | R |   |

{style="table-layout:auto"}

#### Operativsystem

|     | Adobe | Merchant |
| --- | --- | --- |
| Operativsystemets tillgänglighet | R |   |
| Kontinuerlig kvalitet och korrigering av operativsystem | R |   |

{style="table-layout:auto"}

#### Säkerhetskopiering, hög tillgänglighet och failover

|     | Adobe | Merchant |
| --- | --- | --- |
| Tillgång till ögonblicksbild och säkerhetskopieringsprocess | R |   |
| Schemalägga säkerhetskopieringar för miljöer med molnbaserad testning och -produktion | R |   |
| Schemalägga säkerhetskopieringar för miljöer med molnstart och Pro-integrering |     | R |
| Tillgänglighet för HA/failover | R |   |

{style="table-layout:auto"}

#### Molnservrar och skalning

|     | Adobe | Merchant |
| --- | --- | --- |
| Tillgänglighet för processorresurser, datacenter, diskutrymme | R |   |
| Tillgång till och genomförande av överkapacitet eller nöduppgradering | R |   |
| Begär överkapacitet |     | R |
| Övervaka vCPU-användning mot begränsningarna | R |   |

{style="table-layout:auto"}
