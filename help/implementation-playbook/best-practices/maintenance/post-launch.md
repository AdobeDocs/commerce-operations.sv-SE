---
title: Support och underhåll efter lansering
description: Säkerställ optimala prestanda och säkerhet i din Adobe Commerce-butik med vår omfattande support och våra bästa rutiner för underhåll efter lanseringen.
role: Admin, User, Developer
feature: Best Practices
exl-id: f02a13ca-c851-4508-a2bd-e5bc196a330c
source-git-commit: 60444d3ef7208d12af3f06af6e3cab2cae93700b
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---

# Support och underhåll efter lanseringen av Adobe Commerce

Support och underhåll efter lanseringen är avgörande för att din Adobe Commerce Store ska fungera smidigt, fungera bra, förbli säker och fortsätta uppfylla dina verksamhetsmål. Den här fasen omfattar kontinuerlig övervakning, optimering, felkorrigering, uppdateringar och användarsupport. I följande avsnitt delas **support efter start** in i nyckelkategorier:

## Regelbunden övervakning och prestandaoptimering av webbplatser

### Prestandaövervakning

- **Webbplatshastighet och belastningstestning**: Adobe Commerce kan vara resurskrävande, så regelbunden prestandaövervakning är avgörande.

   - **Verktyg som ska användas**: Alla Adobe Commerce i molninfrastrukturprojekt innehåller tillgång till New Relic, som hjälper till att övervaka prestanda och utreda händelser i Commerce program- och molninfrastruktur. Bland de andra verktygen finns Google PageSpeed Insights och GTMetrix.

   - **Så här övervakar du**: Här är de viktigaste objekten som ska övervakas för Adobe Commerce i molninfrastruktur:

      - **Hälsomeddelanden**: Varningar om diskutrymme och miljöhälsa.

      - **Observation**: Omfattande övervakning som kombinerar loggdata från flera källor för effektiv platshantering.

      - **New Relic-tjänst**: Övervakar prestanda i staging och produktion med fokus på nyckeltal.

      - **Princip för hanterade aviseringar**: Spårar mått med fördefinierade tröskelvärden för att utlösa aviseringar för infrastruktur- eller programproblem som påverkar prestanda.

  >[!TIP]
  >
  >Se [prestandaövervakning](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/monitor/performance) i _molnguiden_.


- **Optimera databasprestanda**: Så här optimerar du databasprestanda i Adobe Commerce Cloud:

   - **Övervaka och optimera MySQL-frågor**: Identifiera och matcha långsamma frågor, vilket kan göras med kommandona VISA FULL PROCESSLIST och EXPLAIN i MySQL. För mer komplexa konfigurationer kan Pro-arkitekturanvändare använda Percona Toolkit för att analysera frågeloggar för prestandaproblem.

   - **Indexhantering**: Kontrollera att alla tabeller har en primärnyckel och ta bort alla dubblettindex, eftersom dessa kan minska effektiviteten och leda till konflikter vid samtidig skrivning.

   - **Kronjobboptimering**: Kronjobb ska schemaläggas under tider med låg belastning för att minimera påverkan på prestandan, särskilt om bakgrundsuppgifter som indexering är vanligt.

  >[!TIP]
  >
  >Se [metodtips för att lösa databasprestandaproblem](resolve-database-performance-issues.md).

- **Bildskärms-CDN**: Om du vill övervaka CDN-prestanda snabbt i Adobe Commerce Cloud kan du utföra följande åtgärder:

   - **Utnyttja New Relic för övervakning**: Adobe Commerce erbjuder New Relic för att övervaka prestanda snabbt och andra mätvärden för testnings- och produktionsmiljöer. Det här verktyget ger insikter om serverhälsa, CDN-cachning och nätverksbegäranden över tid, vilket hjälper till att identifiera mönster och optimera CDN-inställningar.

   - **Loggar snabbt analyser**: För Adobe Commerce Cloud Pro-projekt kan du använda New Relic Logs för att granska och analysera data från Fast CDN- och WAF-loggar för att spåra prestandatrender, säkerhetshändelser och diagnostisera fel eller fördröjningsproblem.

   - **Använd cURL-kommandon**: Kör cURL-kommandon med snabbspecifika rubriker för att kontrollera platsens cachestatus. Nyckelsvarshuvuden omfattar `X-Cache` (HIT/MISS), `Fastly-Module-Enabled`, `Fastly-Magento-VCL-Uploaded` och `Cache-Control` för att verifiera cachelagring och modulstatus. Adobe innehåller exempel på cURL-kommandon för både testnings- och produktionsmiljöer.

   - **Kontrollera rubrikinformation**: Kontrollera rubriker som `Cache-Control`, `Pragma` och `X-Magento-Tags` för att bekräfta lämpliga cachelagringsfunktioner och tagghantering för cachelagrat innehåll. Korrekta rubrikvärden anger om cachelagringskonfigurationer används effektivt i CDN.

   - **Snabbt felsökning och testning**: Använd Snabbas felsökningsfunktion för att identifiera och felsöka problem med HIT- och MISS-frekvenser för cache, cachelagringslogik eller felaktiga rubriksvar, som kan peka på konfigurationsproblem eller felpassning med förväntade cachelagringsregler.

Dessa övervakningssteg hjälper till att upprätthålla optimala CDN-prestanda och åtgärda problem som påverkar webbplatsens hastighet och tillförlitlighet.

>[!TIP]
>
>Se [Översikt över snabba tjänster](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/cdn/fastly) i _molnguiden_.

#### Regelbunden säkerhetsövervakning

Adobe rekommenderar ett mångfacetterat tillvägagångssätt som innefattar kontinuerlig skanning, loggning och proaktiva säkerhetsrutiner för att upprätthålla regelbunden säkerhetsövervakning i Adobe Commerce Cloud. Här följer några viktiga åtgärder för att säkerställa kontinuerlig säkerhet:

- **Säkerhetssökning**: Använd Adobe säkerhetssökningsverktyg för att övervaka kända säkerhetsluckor och skadlig kod på Commerce webbplatser. Det här verktyget ger varningar om potentiella säkerhetsrisker och efterlevnadsproblem.

- **Regelbundet korrigerings- och uppdateringsunderhåll**: Använd Adobe säkerhetsuppdateringar och uppdateringar när de blir tillgängliga. Uppgradera till den senaste Adobe Commerce-versionen och få de senaste versionerna av skydd mot hot.

- **Gransknings- och loggövervakning**: Använd verktyg som New Relic Logs (tillgängligt för Pro-projekt) för att centralisera och analysera säkerhetsloggar från både testnings- och produktionsmiljöer och förbättra synligheten för potentiella säkerhetsproblem och överträdelser.

- **Konto- och åtkomsthantering**: Granska regelbundet användar- och administratörskonton för att ta bort oauktoriserade eller inaktuella konton. Stärk åtkomstkontrollen med multifaktorautentisering (MFA) för administratörsanvändare.

- **Brandvägg för webbprogram (WAF)**: Använd den inbyggda Fastly WAF för att upptäcka och minska hot från skadliga trafikmönster, till exempel otillåtna dataextraheringsförsök.

- **Anpassad kod och tilläggssäkerhet**: Skydda anpassad kod eller tillägg från tredje part genom att utföra regelbundna kodgranskningar och begränsa tillägg till dem som kontrolleras av Adobe.

>[!TIP]
>
>Se [Säkerhet](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/security/security) i _handboken för administratörssystem_.

#### Felloggning och övervakning

För att övervaka felloggning i Adobe Commerce Cloud tillhandahåller Adobe flera verktyg och rutiner för effektiv felsökning och prestandahantering:

- **Loggaggning med New Relic**: New Relic samlar in och centraliserar loggar från Adobe Commerce-program, inklusive loggar relaterade till infrastruktur, CDN och WAF. Med den här konfigurationen kan du effektivt spåra fel, skapa kontrollpaneler och frågeloggar för att få djupare insikter om programmets prestanda och problem. Med åtkomst till New Relic Logs kan du söka och filtrera loggar med hjälp av olika attribut för att snabbt diagnostisera problem.

- **Felloggtyper**: Nyckelfelloggarna i Adobe Commerce Cloud innehåller `cloud.log`, som innehåller distributionsfeedback, och `cloud.error.log`, som loggar distributionsvarningar och fel. Andra specifika loggar för felsökning är `debug.log`, `system.log` och `exception.log`, där var och en har tydliga roller för fel- och händelsespårning på Commerce-plattformen.

- **Anpassad loggning med Monolog**: Adobe Commerce har stöd för anpassad loggning via Monolog, vilket gör att utvecklare kan dirigera loggmeddelanden till olika mål, som filer, databaser och till och med aviseringar. Den här flexibiliteten är användbar för att skapa avancerade loggningsstrategier som tillgodoser olika övervakningsbehov i utvecklings- och produktionsmiljöer.

- **Övervakning av undantag med webbplatsövergripande analysverktyg**: Med det platsövergripande analysverktyget kan du övervaka och hantera undantagsloggar och identifiera återkommande problem i både distributions- och programhändelser. Det här verktyget lyfter fram problem som ofta uppstår och gör det enklare att prioritera och åtgärda viktiga problem som påverkar prestandan.

>[!TIP]
>
>Mer information om loggnings- och felspårningsrutiner i Adobe Commerce Cloud finns i [New Relic logghantering](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management) och [undantagsövervakning](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions).

### Säkerhet och uppdateringar

#### Säkerhetsuppdateringar

Här följer några viktiga metoder för att övervaka säkerhetsuppdateringar och uppdateringar:

- **Prenumerera på Adobe Commerce säkerhetsvarningar**: Håll dig informerad om säkerhetsproblem genom att [registrera dig för meddelanden från Adobe](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/security/security).

- **Kontrollera versionsinformation**: [Granska regelbundet versionsinformation för säkerhetsuppdateringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/release/notes/security-patches/overview) som är taggade med&quot;-pN&quot; för versioner (t.ex. 2.3.5-p1) och innehåller viktiga korrigeringar och förbättringar.

- **Använd säkerhetsuppdateringar omedelbart**: Använd säkerhetsuppdateringar så snart de är tillgängliga. Detta inkluderar uppdatering till de senaste versionerna eller användning av specifika korrigeringsfiler.

- **Använd molnpatchar**: För Adobe Commerce Cloud kan säkerhetsuppdateringar paketeras i Cloud Tools Suite. Uppgradera programsviten eller Commerce-versionen för att få dessa korrigeringar.

- **Automatisk korrigeringshantering**: Överväg att använda verktyg som centraliserad korrigeringsfil för att [hantera och tillämpa korrigeringsfiler i flera butiker automatiskt](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale).

>[!TIP]
>
>Mer information och steg-för-steg-anvisningar om hur du tillämpar korrigeringar och upprätthåller säkerheten finns i [Versionsinformation för säkerhetspatchar](../../../release/release-notes/security/overview.md) och [Använda säkerhetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches). Du bör även granska [Site-Wide Analysis Tool](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/site-wide-analysis-tool/access)-rapporter.

#### PCI-kompatibilitet

Följ de här huvudrutinerna för att se till att PCI-kompatibilitet upprätthålls i Adobe Commerce Cloud:

- **Skydda information om kortinnehavare**: Lagra aldrig data om kortinnehavare i Adobe Commerce. Om lagring krävs kan du skydda den med krypterade och tokeniserade metoder.

- **Använd säkra överföringsprotokoll**: Överför alltid betalningsdata via säkra protokoll som TLS, med kryptering och korrekt nyckelhantering.

- **Utnyttja brandväggen för webbprogram (WAF)**: Den snabbstyrda WAF-tjänsten uppfyller PCI DSS 6.6-kraven och skyddar mot vanliga säkerhetsluckor genom att blockera skadlig trafik innan den når din plats. Se mer information [här](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage) och [här](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service).

- **Begränsa åtkomst**: Se till att endast auktoriserad personal har tillgång till känsliga betalningsdata och [använd åtkomstkontroll för att minska risken för exponering](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage).

- **Regelbunden säkerhetssökning**: Utför vanliga PCI ASV-skanningar och [övervaka din miljö](https://experienceleague.adobe.com/sv/docs/commerce-operations/security-and-compliance/shared-responsibility) för att åtgärda potentiella sårbarheter.

>[!TIP]
>
>Mer detaljerade riktlinjer om hur du upprätthåller PCI-kompatibilitet med Adobe Commerce finns i [bästa praxis för betalningshantering och lagring](../planning/payment-processing-storage.md).

### Support för användare och kunder

#### Inställningar

- **Supportkanaler**: Implementera kundsupportkanaler som:

   - **Live-chatt**: Erbjud live-chattsupport för omedelbar hjälp. Bland de vanligaste lösningarna finns Zendesk, Intercom och Tidio.

   - **E-postsupport**: Använd ett supportsystem som t.ex. Freshdesk eller Zoho Desk för att hantera kundförfrågningar effektivt.

   - **Telefonsupport**: Om du har en stor kundbas bör du överväga att erbjuda telefonsupport under kontorstid.

#### Utbildning av administratörer

- **Intern utbildning**: Utbilda personalen i hur man använder Adobe Commerce Admin, bearbetar beställningar, hanterar produkter och hanterar kundservicefrågor.

- **Dokumentation**: Underhåll en intern kunskapsbas eller användarhandbok för vanliga frågor (FAQ), felsökning och vanliga uppgifter.

#### Optimering av kundupplevelser

- **Undersökningar och feedback**: Använd enkäter för att samla in feedback och optimera kundupplevelsen. Adobe Commerce stöder integreringar med verktyg som SurveyMonkey eller Google Forms.

- **Hantering av granskningar**: Hantera kundrecensioner och omdömen om dina produkter. Uppmuntra nöjda kunder att lämna granskningar och samtidigt besvara negativa granskningar på lämpligt sätt.

- **Personalization**: Implementera personaliseringsfunktioner som personaliserade produktrekommendationer eller riktade kampanjer.

### Underhåll och optimering av butik

#### Sökmotoroptimering (SEO)

- **Optimering av innehåll**: Uppdatera produktbeskrivningar, blogginlägg och kategorisidor regelbundet så att innehållet är aktuellt för sökmotorer.

- **SEO-granskningar**: Utför regelbundna SEO-granskningar med verktyg som Google Search Console eller Screaming Frog för att identifiera SEO-problem (t.ex. brutna länkar, saknade metadata, duplicerat innehåll).

- **URL-struktur**: Behåll en ren, logisk URL-struktur och se till att det inte finns några brutna länkar eller omdirigeringar.

#### Optimering av konverteringsgraden (CRO)

- **A/B-testning**: Kör A/B-tester på olika sidelement, till exempel produktsidor eller utcheckningsprocess, för att förbättra konverteringsgraden.

- **Avbruten kundvagn**: Implementera e-postkampanjer för kundvagn eller popup-fönster för avslutningsavsikt för att återställa förlorad försäljning.

- **Optimering av utcheckning**: Förenkla utcheckningsprocessen genom att minska antalet steg och erbjuda gästutcheckning för att förbättra konverteringarna.

#### Marknadsintegrering

- **E-postkampanjer**: Skapa automatiska e-postmarknadsföringsflöden för välkomstmeddelanden, övergivna kundvagnsmeddelanden och uppföljningar efter köp. Plattformar som Adobe Marketo, Mailchimp eller Klaviyo kan integreras väl med Adobe Commerce.

- **Integrering av sociala medier och annonser**: Integrera med plattformar som Facebook, Instagram och Google Ads för att köra riktade kampanjer och spåra resultatet.

#### Mobiloptimering

- **Mobila svarstider**: Testa regelbundet webbplatsens mobilrespons och användbarhet. Med tanke på att mobilhandeln växer är en strategi som sätter mobilen i första rummet avgörande för fortsatt framgång.

- **Mobila prestanda**: Använd Google mobilvänliga test- och prestandaverktyg för att optimera upplevelsen i mobilbutiken.

### Skalning och utveckling av nya funktioner

- **Automatisk skalning för trafikhantering**:

   - Adobe Commerce Cloud stöder automatisk skalning för att dynamiskt justera serverresurser (till exempel webbnoder) baserat på trafikkrav i realtid, vilket säkerställer att din butik kan hantera stora besöksvolymer utan manuell inblandning. Se [autoskalning](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/architecture/autoscaling) i _molnguiden_.

   - Webb- och tjänstenivåer kan skalas oberoende av varandra och lägga till fler webnoder för ökad trafik och skalning av databaser eller servicanoder för backend-prestanda under perioder med hög belastning. Se [skalad arkitektur](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) i _molnguiden_.

- **Prestandaövervakning**:

   - Använd **New Relic** för att övervaka prestandamått i realtid (t.ex. CPU användning, trafiknivåer) och göra nödvändiga justeringar.

   - Testa prestanda i testmiljöer före skalning för att undvika produktionsproblem.

- **Utveckling av nya funktioner**:

   - Integrera avancerade funktioner som **AI-driven personalisering**, **prenumerationshantering** och anpassade lösningar.

   - Testa och förfina funktionerna i testmiljöer före driftsättning för att minimera driftstoppen.

- **Pågående webbplatsunderhåll**:

   - Granska systemloggar och prestandamått regelbundet för att identifiera områden som kan förbättras.

   - Säkerställ att infrastrukturen förblir skalbar och anpassningsbar till nya affärskrav och tillväxt.

>[!TIP]
>
>Detaljerad vägledning finns i [bästa praxis för underhåll](overview.md), [personalisering](https://business.adobe.com/se/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization) och [funktionsutveckling](https://business.adobe.com/se/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization).

### Rapportering och analys

- **Adobe Commerce Intelligence:** Commerce Intelligence, en kärnfunktion i Adobe Commerce, ger insikter om god praxis i flera datakällor, så att handlare kan fatta vetenskapliga, datadrivna beslut och vidta tydliga och välgrundade åtgärder. Se [_Commerce Intelligence användarhandbok_](https://experienceleague.adobe.com/sv/docs/commerce-business-intelligence/mbi/getting-started).

- **Adobe Analytics:** Adobe Analytics erbjuder en kraftfull lösning för att spåra, analysera och optimera onlinebutikens prestanda. Adobe Analytics hjälper e-handelsföretag att få djupare insikter i kundbeteende, produktresultat, konverteringsgrader och andra viktiga mätvärden, vilket möjliggör datadrivet beslutsfattande.

- **Google Analytics:** Använd Google Analytics för att spåra kundbeteende, trafikkällor och konverteringsgrader.

- **Fler Commerce Intelligence-verktyg:** Adobe Commerce innehåller avancerad rapportering. Den här funktionen ger dig tillgång till en uppsättning dynamiska rapporter som baseras på dina produkt-, order- och kunddata, med en anpassad kontrollpanel som är anpassad efter ditt företags behov. Mer information finns i [avancerad rapportering](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting) i _användarhandboken för administratörer_.

### Slutsats

Support och underhåll efter lanseringen är pågående åtgärder som kräver regelbunden tillsyn för att din Adobe Commerce Store ska fortsätta fungera bra, förbli säker och anpassas efter ditt företags behov. För att lyckas på lång sikt är det viktigt att ha en strukturerad strategi för webbplatsövervakning, kundsupport, optimering och uppdateringar.
