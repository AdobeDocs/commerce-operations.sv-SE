---
title: Frigör schema
description: Lär dig när specifika versioner av Adobe Commerce är schemalagda för betaversion, förhandsversioner och allmän tillgänglighet.
source-git-commit: 261aecd7d217e5c2e22f1a6c97242baa2923af60
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# Frigör schema

Adobe strävar hela tiden efter att hitta den rätta balansen mellan att göra produktuppgraderingar enkla och förutsägbara och leverera förbättringar och nya funktioner till tidiga användare snabbare. Under det senaste året har vi finslipat hur vi levererar programvara för denna balans. Mer information finns i [versionsprincip](versioning-policy.md).

Adobe släpper säkerhets- och funktionspatchar för alla utgåvor av Adobe Commerce och Magento Open Source som stöds.

I följande tabell visas datumen för schemalagda releaser (datum kan ändras):

| Frigör | Versioner | Adobe Commerce Beta | Adobe Commerce Pre-release | Adobe Commerce &amp; Magento Open Source<br>Allmän tillgänglighet |
|-----------------------------------------------------------------|-------------------------------------------------------|---------------------------|----------------------------------|---------------------------------------------------------------------|
| Mars 2022<br>Funktion + patch + säkerhetspatchrelease | 2.4.4<br>2.4.3-p2<br>2.3.7-p3 | Oktober 2021 och pågående | 29 mars 2022 | 12 april 2022 |
| April 2022<br>Funktionsrelease | \-\- | \-\- | \-\- | 26 april 2022 |
| Juni 2022<br>Funktionsrelease | \-\- | \-\- | \-\- | 21 juni 2022 |
| Augusti 2022<br>Funktion + patch + säkerhetspatchrelease | 2.4.5<br>2.4.4-p1<br>2.4.3-p3<br>2.3.7-p4<sup>1</sup> | \-\- | 26 juli 2022 | 9 augusti 2022 |
| Oktober 2022<br>Funktion + säkerhetsuppdatering | 2.4.5-p1<sup>2</sup><br>2.4.4-p2 | \-\- | 27 september 2022 | 11 oktober 2022 |
| Januari 2023<br>Funktionsrelease | \-\- | \-\- | \-\- | 17 januari 2023 |
| Mars 2023<br>Funktion + patch + säkerhetspatchrelease | 2.4.6<br>2.4.5-p2<br>2.4.4-p3 | Januari 2023 | 28 februari 2023 | 14 mars 2023 |

<sup>\-\- Anger objekt som inte är tillämpliga i den här versionen.</sup><br>
<sup>1 Detta är den sista korrigeringsversionen för version 2.3.x. Versionslinjen för 2.3.x når slutet av supporten (EOS) i september 2022.</sup><br>
<sup>2 Det finns ingen fullständig patch-version i oktober 2022.</sup><br>

>[!TIP]
>
>Patch and Security Patch Releases är möjligheter att uppgradera kärnkodbasen för att hålla plattformen säker, tillförlitlig och effektiv. Funktionsreleaser sker varannan månad. Funktionsreleaser är oberoende av kärnkodbasen och är tillgängliga via externa moduler eller tillägg. Eventuella uppdateringar av befintliga oberoende funktioner släpps under funktionens releasetider och inträffar inte automatiskt om funktionen redan är implementerad.

## Tidig åtkomst

Förhandsversionen är den allmänna tillgänglighetskoden som är tillgänglig för Adobe Commerce handlare och alla partners två veckor före den allmänna tillgängligheten. Det gör att koden kan driftsättas snabbare än den allmänna tillgängligheten.

Beta är en icke-generell tillgänglighetskod som är tillgänglig för alla partner. Det ger extra tid att granska kod och komponenter som påverkas.

Mer information finns i [Betaprogram](beta-program.md).

## Versionstyper

- **Patch releases**- Uppdateringar av Adobe Commerce och Magento Open Source som innehåller säkerhets-, kompatibilitets-, prestanda- och högprioriterade kvalitetskorrigeringar.
- **Säkerhetsuppdateringar**- Säkerhetsuppdateringar för Adobe Commerce och Magento Open Source har släppts för att säkerställa att handlarna följer gällande regelverk.
- **Funktioner**—Nya funktioner och funktionsuppdateringar som levereras som fristående tjänster, separat från korrigeringsfilerna. Exempel är tjänster som Product Recommendations och Live Search, oberoende moduler som PWA Studio och Inventory management (MSI) samt uppdateringar av våra molntjänster och vår infrastruktur.
