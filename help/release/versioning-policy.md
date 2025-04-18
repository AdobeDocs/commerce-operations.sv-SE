---
title: Versionspolicy
description: Läs mer om de olika versionerna av Adobe Commerce.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: 0ea8c2bfffe81d27547c0330abdd75fc078542cf
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---

# Versionspolicy för Adobe Commerce

Adobe Commerce använder [semantisk versionshantering](https://semver.org/) på den enskilda modulnivån (till exempel `magento/framework 101.1.1`), men inte för marknadsföringsversionsnumret. Exempel:

- **STÖRSTA VERSIONEN**—2
- **MINOR release**—2.4
- **PATCH-version**—2.4.8
   - **SÄKERHETSkorrigeringsversion**—2.4.8-p1
      - Säkerhetsfelkorrigering
      - Säkerhetsförbättring
- **ALPHA patch release**—2.4.8-alpha1
- **BETA patch release**—2.4.8-beta1
- **Utbyggbarhet, infrastruktur och tjänster**
- **Programfix**
- **Individuell korrigering**
- **Egen korrigering**

## MINDRE frisläppning

Följande riktlinjer gäller för mindre releaser:

- Det går att göra ändringar. Kod som skrivits för Adobe Commerce 2.2.x fungerar eventuellt inte längre med Adobe Commerce 2.3.x. Mindre versioner kan till exempel ge stöd för större systemkrav och beroenden, som PHP.
- Modulversionerna kan variera. Vissa moduländringar införs till exempel i en ny korrigering medan andra införs i en mindre version.
- Mindre versioner kan innehålla nya funktioner som kan kräva ytterligare arbete av dig eller din partner under en uppgradering för att säkerställa kompatibilitet.
- Mindre releaser kan innehålla korrigeringar av säkerhets- och kvalitetsproblem.

## PATCH release

Patch-releaser är främst inriktade på att leverera säkerhets-, prestanda-, efterlevnads- och högprioriterade kvalitetskorrigeringar som hjälper dig att få webbplatserna att prestera maximalt.

Följande riktlinjer gäller för korrigeringsversioner:

- Den senaste delversionen som stöds får fullständiga funktionsförbättringar och korrigeringar av kvalitet.
- Ändringar som kan bryta tillägg eller kodkompatibilitet undviks. Kod som skrivits för version 2.2.0 bör till exempel fortfarande fungera med version 2.2.7.
- I undantagsfall kan ändringar eller ytterligare patchar eller programfixar släppas för att åtgärda säkerhets- eller kompatibilitetsproblem och högkvalitativa problem. På modulnivå är dessa ändringar oftast PATCH-nivå, ibland MINOR-nivå.

### Säkerhetsuppdatering

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## ALPHA patch release

Utgåvor av Adobe Commerce-funktioner från före Beta görs tillgängliga för alla Adobe Commerce-kunder och Adobe-partners. Alpha-releaser är avsedda för snabb feedback och utvärdering av funktioner som fortfarande är under utveckling. Dessa releaser ger möjlighet till tidig testning och integreringsplanering före Beta och de allmänna tillgänglighetsreleaserna.

Alpha-utgåvor kan vara ofullständiga och innehåller sannolikt defekter. De tillhandahålls i befintligt skick utan någon garanti av något slag. Adobe har ingen skyldighet att upprätthålla, korrigera, uppdatera, ändra, modifiera eller på annat sätt ge support (via Adobe Support Services eller på annat sätt) för Alpha. Kunderna bör inte förlita sig på att Alpha-releaser eller tillhörande dokumentation eller material fungerar som de ska. Användningen av Alpha-releaser är helt på kundens egen risk.

## BETA patch release

Pre-General Availability-versioner av Adobe Commerce-funktioner är tillgängliga för alla Adobe Commerce-kunder och Adobe-partners. Det ger extra tid innan den allmänna tillgängligheten kan granska kod och komponenter som påverkas.

Beta-releaser kan innehålla defekter och tillhandahålls i befintligt skick utan någon garanti av något slag. Adobe har ingen skyldighet att upprätthålla, korrigera, uppdatera, ändra, modifiera eller på annat sätt ge support (via Adobe Support Services eller på annat sätt) för Beta. Kunderna bör inte förlita sig på att Beta-releaser eller tillhörande dokumentation eller material fungerar som de ska. Därför är all användning av Beta Releases helt och hållet riskerad för kunden.

## Funktioner, molninfrastruktur och utbyggbarhet

Molninfrastruktur och funktionsreleaser innehåller nya funktioner och funktionsuppdateringar som levereras som fristående tjänster, utöver korrigeringsutgåvor. Exemplen omfattar, men är inte begränsade till:

- Uppdateringar av molntjänster och infrastruktur
- B2B
- SaaS-produkter (katalogtjänst, dataanslutning, produktrekommendationer och Live Search)
- Utbyggandeteknik (Admin UI SDK, API Mesh, App Builder Starter Kits, Eventing och Webhooks)

## Hotfix

Programfixar är korrigeringar som innehåller effektiva säkerhets- eller kvalitetskorrigeringar, t.ex. korrigeringar av noll-dagars sårbarheter, som påverkar många handlare. Adobe släpper snabbkorrigeringar (efter behov) för Adobe Commerce-versioner som stöds när viktiga säkerhets- eller kvalitetsproblem påverkar dem. Programfixar publiceras i avsnittet [Kända fel](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) i kunskapsbasen. Dessa korrigeringar ingår i nästa planerade korrigeringsversion.

>[!NOTE]
>
>Snabbkorrigeringar kan innehålla ändringar som är inkompatibla bakåt.

## Enskild patch

Enskilda korrigeringsfiler innehåller korrigeringar av låg kvalitet för ett specifikt problem. Dessa korrigeringar tillämpas på de mindre versioner av Adobe Commerce som stöds. Adobe släpper enskilda korrigeringsfiler efter behov för Adobe Commerce i enlighet med [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Enskilda korrigeringsfiler innehåller inte ändringar som är bakåtkompatibla.

## Isolerad patch

Isolerade patcharInnehåller en fristående korrigering som ingår i den senaste patchen med endast säkerhet eller en kommande säkerhetskorrigering som släpps separat för snabbare implementering.

## Egen korrigering

Skapas av icke-Adobe-personal för att åtgärda ett problem eller ändra Adobe Commerce-koden av olika anledningar. Anpassade korrigeringsfiler levereras via [kvalitetskorrigeringsverktyget](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
