---
title: Frigör schema
description: Lär dig när specifika versioner av Adobe Commerce är schemalagda för betaversion, förhandsversioner och allmän tillgänglighet.
source-git-commit: 5e02f300bb0b5601c653fdea1dd5b85f4e18ed9c
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---


# Frigör schema

Adobe strävar hela tiden efter att hitta den rätta balansen mellan att göra produktuppgraderingar enkla och förutsägbara och leverera förbättringar och nya funktioner till tidiga användare snabbare. Under det senaste året har vi finslipat hur vi levererar programvara för denna balans. Mer information finns i [versionsprincip](versioning-policy.md).

Adobe släpper säkerhets- och funktionspatchar för alla utgåvor av Adobe Commerce som stöds.

I följande tabell visas datumen för schemalagda releaser (datum kan ändras):

| Frigör | Versioner | Förhandsversion | Allmän tillgänglighet |
|--------------------------------------------------------------------|-------------------------------------------------|--------------------|----------------------|
| Januari 2023-versionen | \-\- | \-\- | 17 januari 2023 |
| Mars 2023 Funktion + patch + säkerhetspatchrelease | 2.4.6<sup>1</sup><br>2.4.5-p2<br>2.4.4-p3 | 28 februari 2023 | 14 mars 2023 |
| Version från april 2023 | \-\- | \-\- | 25 april 2023 |
| Funktion + betatestning + säkerhetspatchrelease från juni 2023 | 2.4.7-beta1<br>2.4.6-p1<br>2.4.5-p3<br>2.4.4-p4 | 30 maj 2023 | 13 juni 2023 |
| Augusti 2023 Feature + Security patch release | 2.4.6-p2<br>2.4.5-p4<br>2.4.4-p5 | 25 juli 2023 | 8 augusti 2023 |
| Oktober 2023 Funktion + betatestning + säkerhetspatchrelease | 2.4.7-beta2<br>2.4.6-p3<br>2.4.5-p5<br>2.4.4-p6 | 26 september 2023 | 10 oktober 2023 |

{style="table-layout:auto"}

<sup>\-\- Anger objekt som inte är tillämpliga i den här versionen.</sup><br>
<sup>1 betaversion planerad till januari 2023</sup><br>

>[!TIP]
>
>Patch and Security Patch Releases är möjligheter att uppgradera kärnkodbasen för att hålla plattformen säker, tillförlitlig och effektiv. Funktionsreleaser sker varannan månad. Funktionsreleaser är oberoende av kärnkodbasen och är tillgängliga via externa moduler eller tillägg. Eventuella uppdateringar av befintliga oberoende funktioner släpps under funktionens releasetider och inträffar inte automatiskt om funktionen redan är implementerad.

## Tidig åtkomst

Förhandsversionen är den allmänna tillgänglighetskoden som är tillgänglig för Adobe Commerce handlare och alla partners två veckor före den allmänna tillgängligheten. Det gör att koden kan driftsättas snabbare än den allmänna tillgängligheten.

Mer information finns i [betaversioner](beta.md).

## Versionstyper

- **Patch releases**- Uppdateringar av Adobe Commerce centrala program som omfattar säkerhets-, kompatibilitets-, prestanda- och högprioriterade kvalitetskorrigeringar.

   >[!IMPORTANT]
   >
   >Adobe kommer att släppa betaversioner (&quot;betaversioner&quot;), som är förhandsversioner av Adobe Commerce-funktioner som är tillgängliga för alla Adobe Commerce-kunder och Adobe-partners. Betaversioner kan innehålla defekter och tillhandahålls i befintligt skick utan garanti av något slag. Adobe har ingen skyldighet att upprätthålla, korrigera, uppdatera, ändra, modifiera eller på annat sätt ge support (via Adobe Support Services eller på annat sätt) för betaversioner. Kunden rekommenderas att iaktta försiktighet och inte på något sätt förlita sig på att betaversionerna och/eller tillhörande dokumentation eller material fungerar korrekt eller fungerar korrekt. Därför är all användning av betaversioner helt på kundens egen risk.

- **Betaversionskorrigeringar**- Icke-generell tillgänglighetskoduppdatering för Adobe Commerce-programmet som innehåller säkerhets-, kompatibilitets-, prestanda- och högprioriterade kvalitetskorrigeringar. Det ger extra tid att granska kod och komponenter som påverkas.
- **Säkerhetsuppdateringar**—Säkerhetsuppdateringar av Adobe Commerce-programmet som släppts för att skydda handlarna och uppfylla kraven.
- **Funktioner**—Nya funktioner och funktionsuppdateringar som levereras som fristående tjänster, separat från korrigeringsfilerna. Exempel är tjänster som Product Recommendations och Live Search, oberoende moduler som PWA Studio och Inventory management (MSI) samt uppdateringar av våra molntjänster och vår infrastruktur.
