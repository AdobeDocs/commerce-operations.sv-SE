---
title: Beta-versioner
description: Läs mer om betaversioner av Adobe Commerce och hur du deltar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 17397fe91806c22272e426d615b11fd383602798
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 0%

---

# Adobe Commerce betaversioner

Adobe Commerce betaprogram är ett sätt för handlare att få tillgång till betaversionsfunktioner och -kod, ge feedback och vägleda Adobe Commerce framtid. Det finns två typer av betaprogram:

- Offentlig Beta: Ett offentligt betaversionsprogram är tillgängligt för alla Adobe Commerce kunder och partners
- Private Beta: Ett privat betaprogram kan kräva ett godkännande baserat på kvalificeringskriterier för deltagande

>[!IMPORTANT]
>
>Beta-releaser kan innehålla defekter och tillhandahålls i befintligt skick utan någon garanti av något slag. Adobe har ingen skyldighet att upprätthålla, korrigera, uppdatera, ändra, modifiera eller på annat sätt ge support (via Adobe Support Services eller på annat sätt) för betaversioner. Kunderna rekommenderas att iaktta försiktighet och att inte på något sätt förlita sig på att betaversionerna och/eller tillhörande dokumentation eller material fungerar korrekt eller fungerar korrekt. Funktioner och API:er i betaversionen kan ändras utan föregående meddelande. Därför är all användning av betaversioner helt och hållet på kundens egen risk.

## Fördelar

Genom att få tidig tillgång till funktioner som Adobe utvecklar kan kunder och partners ge feedback, utforma produktutvecklingen och förbereda sig för att använda nya funktioner innan de blir allmänt tillgängliga.

## Beta-program

I följande avsnitt finns en lista med aktiva betaprogram.

### Semantisk sökning: smartare, sammanhangsberoende shoppingupplevelser (privat beta)

Semantisk sökning är en teknik för e-handelssökning som förstår *innebörden* bakom en kunders fråga, inte bara de exakta orden. Till skillnad från traditionell nyckelordsbaserad sökning, som ofta misslyckas när frågor innehåller okända eller felstavade termer, tolkar denna AI-baserade metod avsikter med att använda naturlig språkbearbetning och sammanhang för att leverera mer relevanta resultat.

Den här tekniken åtgärdar en stor begränsning i traditionell sökning: nollresultatsidor som inträffar när kunderna använder ord som inte finns i katalogen. Med hjälp av AI-baserade tekniker mappas användarfrågor och produktdata till ett delat semantiskt utrymme. Systemet känner till exempel igen att &quot;löpskor&quot; och &quot;joggingskor&quot; avser samma typ av produkt, vilket möjliggör:

- Synonymegenkänning
- Sammanhangsberoende relevans
- Intelligent hantering av vaga, felstavade eller sammansatta frågor
- Förståelse av naturligt, konversationsspråk

Om du vill begära en inbjudan till betaprogrammet skickar du ett e-postmeddelande till [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com). Adobe-teamet kommer att följa nästa steg och uppfyller behörighetskraven.

### Patcheringstjänst för molnautomatisering (Private Beta)

[Tjänsten ](../tools/caps-tool/intro.md) Creative Cloud Automation Patching automatiserar processen för att tillämpa isolerade säkerhetspatchar i [Adobe Commerce på molninfrastrukturen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview) -miljöer.

I oktober 2025 kommer betaversionen av Cloud Automation Patching Service att läggas till på kontrollpanelen för [Site-Wide Analysis-verktyget](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard). Den här tjänsten stöder Commerce projektadministratörer med ett smidigt arbetsflöde för patchning som innefattar:

- Automatiserad installation av korrigeringsfiler
- Återställning
- Verifiering efter distribution.

Tjänsten säkerställer att du kan upprätthålla säkra, stabila och uppdaterade miljöer med minimal manuell insats och risk.

Betaversionen innehåller följande funktioner:

- **Automatisera installation av korrigeringsfiler**: Förenkla och automatisera processen att åtgärda kritiska säkerhetsluckor i olika miljöer.
- **Minimera risken**: Förhindra webbplatsavbrott med hälsokontroll och återställningsfunktioner efter distributionen.

>[!NOTE]
>
>Eftersom tjänsten Cloud Automation Patching automatiskt tillämpar isolerade säkerhetspatchar måste du ha rollen [Contributor eller Project Admin](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access) för att kunna använda den.

Om du vill delta i den här betaversionen fyller du i och skickar [Cloud Automation Patching Service - Beta Sign-formulär](https://forms.office.com/r/3Wfxj5nPdB).

### IBM Sterling Order Management System Integration (Private Beta)

Integrationsacceleratorn för IBM Sterling Order Management gör det möjligt för Adobe Commerce-kunder att komma igång med avancerade orderhanteringsfunktioner som bygger på IBM Sterling OMS. Med den här integreringen får handlare:

- Synlighet i realtid av lagernivåer och korrekta leveransdatum för era kunder.
- Automatiserad anskaffning för beställningar baserat på konfigurerbara regler, så att ni kan optimera ert leveransnätverk och lager.
- En universell vy över beställningar över flera kanaler från en enda kontrollpanel så att era supportteam kan leverera utomordentliga tjänster och snabbt identifiera och hantera undantag.
- Ett mallat returhanteringsflöde som förenklar returhanteringen.

Om du vill delta i betaversionen skickar du en e-postförfrågan till [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Adobe Commerce Foundation (offentlig Alpha/Beta)

Alla Adobe Commerce Foundation alfa- och betaversioner innehåller alla ändringar som levereras till Adobe Commerce kärnkod före det planerade releasedatumet, inklusive, men inte begränsat till, följande funktionsområden:

- Senaste säkerhetskorrigeringar
- Prestandaförbättringar
- Förbättringar i GraphQL
- Allmänna felkorrigeringar av kvalitet
- Bidrag från gemenskapen
- Ändringar som krävs för kompatibilitet med [Adobe Commerce-tjänster](https://experienceleague.adobe.com/en/docs/commerce/user-guides/home)

#### Namngivningskonvention och schema

Adobe släpper normalt alfa- och betatestningar flera gånger per år.

Alpha-versionspaket har suffixet `-alphaX`. Följande namnkonvention används till exempel i alfabetet för Adobe Commerce 2.4.7:

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Beta-versionspaket har suffixet `-betaX`. I betaversionspaketen för Adobe Commerce 2.4.7 används till exempel följande namnkonvention:

- `2.4.7-beta1`
- `2.4.7-beta2`

I [releaseplanen](schedule.md) finns en lista över kommande allmänna alfa- och betaversionsdatum.

#### Frigör åtkomst

Adobe Commerce alfa- och betaversioner distribueras på samma sätt som andra Adobe Commerce-korrigeringsutgåvor: som Composer-metapaket på `https://repo.magento.com`. Källkoden är tillgänglig på [GitHub](https://github.com/magento/magento2).

Mer information finns i [Snabbstart för installation av disposition](../installation/composer.md).

#### Ärenderapportering

Adobe tillhandahåller inte Adobe standardsupport för alfa- och betaversioner.

Om du vill skicka feedback om alfa- och betaversioner följer du det [regelbundna rapportflödet](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) på [GitHub](https://github.com/magento/magento2).

Adobe övervakar alla kritiska problem som rapporteras mot den senaste alfa- eller betaversionen och prioriterar dem så att de kan lösas före GA-releasedatum.
