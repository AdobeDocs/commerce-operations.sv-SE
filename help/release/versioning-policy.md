---
title: Versionspolicy
description: Läs mer om de olika typerna av Adobe Commerce-utgåvor, inklusive smärre utgåvor, korrigeringsfiler, säkerhetskorrigeringar, funktioner, snabbkorrigeringar, enskilda korrigeringsfiler och anpassade korrigeringsfiler.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Versionspolicy för Adobe Commerce

Adobe Commerce använder [semantisk versionshantering](https://semver.org/) på den enskilda modulnivån (till exempel `magento/framework 101.1.1`), men inte för marknadsföringsversionsnumret. Exempel:

- **STÖRSTA VERSIONEN**—2
- **MINOR release**—2.4
- **PATCH-version**—2.4.5
   - **SÄKERHETSkorrigeringsversion**—2.4.5-p1
      - Säkerhetsfelkorrigering
      - Säkerhetsförbättring
- **BETA patch release**—2.4.7-beta2
- **Utbyggbarhet, infrastruktur och tjänster**
- **Programfix**
- **Individuell korrigering**
- **Egen korrigering**

## MINDRE frisläppning

Följande riktlinjer gäller för mindre releaser:

- Det går att göra ändringar. Kod som skrivits för Adobe Commerce 2.2.x fungerar eventuellt inte längre med Adobe Commerce 2.3.x. Mindre versioner kan till exempel ge stöd för större systemkrav och beroenden, som PHP.
- Modulversionerna kan variera. Vissa moduländringar införs till exempel i en ny korrigering medan andra införs i en mindre version.
- Mindre versioner kan innehålla nya funktioner som kan kräva ytterligare arbete av dig eller din partner under uppgraderingen för att säkerställa kompatibilitet.
- Mindre releaser kan innehålla korrigeringar av säkerhets- och kvalitetsproblem.

## PATCH release

Patch-releaser är främst inriktade på att leverera säkerhets-, prestanda-, efterlevnads- och högprioriterade kvalitetskorrigeringar som hjälper dig att få webbplatserna att prestera maximalt.

Följande riktlinjer gäller för korrigeringsversioner:

- Den senaste delversionen som stöds får fullständiga funktionsförbättringar och korrigeringar av kvalitet.
- Ändringar som kan bryta tillägg eller kodkompatibilitet undviks. Kod som skrivits för version 2.2.0 bör till exempel fortfarande fungera med version 2.2.7.
- I undantagsfall kan ändringar eller ytterligare patchar eller programfixar släppas för att åtgärda säkerhets- eller kompatibilitetsproblem och högkvalitativa problem. På modulnivå är det oftast ändringar på PATCH-nivå, ibland ändringar på MINOR-nivå.

### Säkerhetsuppdatering

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## BETA patch release

Tillgänglighetsreleaser av Adobe Commerce-funktioner är tillgängliga för alla Adobe Commerce-kunder och Adobe-partners. Det ger extra tid innan den allmänna tillgängligheten kan granska kod och komponenter som påverkas.

Beta Releases kan innehålla defekter och tillhandahålls i befintligt skick utan någon garanti av något slag. Adobe har ingen skyldighet att upprätthålla, korrigera, uppdatera, ändra, modifiera eller på annat sätt ge support (via Adobe Support Services eller på annat sätt) för Beta Releases. Kunderna rekommenderas att vara försiktiga och inte på något sätt förlita sig på att Beta-releaserna och/eller tillhörande dokumentation eller material fungerar korrekt eller fungerar korrekt. Därför är all användning av Beta Releases helt och hållet på kundens egen risk.

## Funktioner, molninfrastruktur och utbyggbarhet

Molninfrastruktur och funktionsreleaser innehåller nya funktioner och funktionsuppdateringar som levereras som fristående tjänster, utöver korrigeringsutgåvor. Exempel är uppdateringar av våra molntjänster och vår infrastruktur, B2B-, SaaS-produkter (katalogtjänst, dataanslutning, produktrekommendationer och Live Search) och utökningsteknik (API Mesh, Integration Starter Kit och Eventing).

## Hotfix

Programfixar är korrigeringar som innehåller effektiva säkerhets- eller kvalitetskorrigeringar, t.ex. korrigeringar av noll-dagars sårbarheter, som påverkar många handlare. Adobe släpper snabbkorrigeringar för Adobe Commerce-versioner som fortfarande stöds och påverkas av viktiga säkerhets- eller kvalitetsproblem efter behov. Programfixar publiceras i avsnittet [Kända fel](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) i vår kunskapsbas. Dessa korrigeringar ingår i nästa planerade korrigeringsversion.

>[!NOTE]
>
>Snabbkorrigeringar kan innehålla ändringar som är inkompatibla bakåt.

## Enskild patch

Enskilda korrigeringsfiler innehåller korrigeringar av låg kvalitet för ett specifikt problem. Dessa korrigeringar tillämpas på de mindre versioner av Adobe Commerce som stöds. Adobe släpper enskilda korrigeringsfiler efter behov för Adobe Commerce i enlighet med vår [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Enskilda korrigeringsfiler innehåller inte ändringar som är bakåtkompatibla.

## Isolerad patch

Innehåller en fristående korrigering som ingår i den senaste säkerhetsuppdateringen eller en kommande säkerhetsuppdatering som släpps separat för snabbare implementering.

## Egen korrigering

Skapas av icke-Adobe-personal för att åtgärda ett problem eller ändra Adobe Commerce-koden av olika anledningar. Anpassade korrigeringsfiler levereras via [kvalitetskorrigeringsverktyget](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
