---
title: Versionspolicy
description: Läs mer om de olika typerna av Adobe Commerce-utgåvor, inklusive smärre utgåvor, korrigeringsfiler, säkerhetskorrigeringar, funktioner, snabbkorrigeringar, enskilda korrigeringsfiler och anpassade korrigeringsfiler.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# Versionspolicy för Adobe Commerce

Adobe Commerce använder [semantisk versionshantering](https://semver.org/) på den enskilda modulnivån (till exempel `magento/framework 101.1.1`), men inte för versionsnumret. Exempel:

- **STÖRRE UTGÅVA**—2
- **MINDRE frisläppning**—2.4
- **PATCH release**—2.4.5
   - **Säkerhetsuppdatering**—2.4.5-p1
      - Säkerhetsfelkorrigering
      - Säkerhetsförbättring
- **BETA patch**—2.4.7-beta2
- **Utbyggbarhet, infrastruktur och tjänster**
- **Hotfix**
- **Enskild patch**
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

{{$include /help/_includes/security-patch-release-overview.md}}

## BETA patch

Tillgänglighetsreleaser av Adobe Commerce-funktioner är tillgängliga för alla Adobe Commerce-kunder och Adobe-partners. Det ger extra tid innan den allmänna tillgängligheten kan granska kod och komponenter som påverkas.

Betaversioner kan innehålla defekter och tillhandahålls i befintligt skick utan garanti av något slag. Adobe har ingen skyldighet att upprätthålla, korrigera, uppdatera, ändra, modifiera eller på annat sätt ge support (via Adobe Support Services eller på annat sätt) för betaversioner. Kunderna rekommenderas att vara försiktiga och inte på något sätt förlita sig på att betaversionerna och/eller tillhörande dokumentation eller material fungerar korrekt eller fungerar korrekt. Därför är all användning av betaversioner helt och hållet på kundens egen risk.

## Utbyggbarhet, infrastruktur och tjänster

Funktionsreleaser som innehåller nya funktioner och funktionsuppdateringar som levereras som fristående tjänster, åtskilda från patch-releaser. Exemplen omfattar utökningsteknik som API Mesh och Eventing, SaaS-produkter som Product Recommendations och Live Search, oberoende moduler som B2B och PWA Studio samt uppdateringar av våra molntjänster och vår infrastruktur.

## Hotfix

Programfixar är korrigeringar som innehåller effektiva säkerhets- eller kvalitetskorrigeringar, t.ex. korrigeringar av noll-dagars sårbarheter, som påverkar många handlare. Adobe släpper snabbkorrigeringar för Adobe Commerce-versioner som fortfarande stöds och påverkas av viktiga säkerhets- eller kvalitetsproblem efter behov. Programfixar publiceras på [Avsnittet Kända fel](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) i vår kunskapsbas. Dessa korrigeringar ingår i nästa planerade korrigeringsversion.

>[!NOTE]
>
>Snabbkorrigeringar kan innehålla ändringar som är inkompatibla bakåt.

## Enskild patch

Enskilda korrigeringsfiler innehåller korrigeringar av låg kvalitet för ett specifikt problem. Dessa korrigeringar tillämpas på de mindre versioner av Adobe Commerce som stöds. Adobe släpper enskilda patchar efter behov för Adobe Commerce i enlighet med våra [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Enskilda korrigeringsfiler innehåller inte ändringar som är inkompatibla bakåt.

## Egen korrigering

Skapas av annan personal än Adobe för att åtgärda ett problem eller ändra Adobe Commerce-koden av olika anledningar. Anpassade patchar levereras via [Verktyget Kvalitetspatchar](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## Relaterade ämnen

- [Versioner](https://developer.adobe.com/commerce/php/development/versioning/)
- [Kommande versioner](schedule.md)
- [Software Lifecycle Policy](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
