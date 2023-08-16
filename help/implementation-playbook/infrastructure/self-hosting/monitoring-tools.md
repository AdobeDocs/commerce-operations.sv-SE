---
title: Självvärdande verktyg för Adobe Commerce-övervakning
description: Lär dig mer om självvärdande övervakningsverktyg, idéer och idéer och bästa metoder att tänka på.
landing-page-description: Lär dig några koncept och saker som du bör tänka på när du har Adobe Commerce som värd.
short-description: Lär dig strategier och övervakningsverktyg för att själv vara värd för Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 728e9439-63d0-4481-b014-7ba2ce97b9d0
feature: Install, Logs, Observability
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 0%

---

# Självhosting Adobe Commerce Monitoring - telemetri och verktyg

Med övervakningsverktygen kan man upptäcka förändringar utan att behöva betala någon för att se allting hela tiden. Med de flesta verktyg kan du lägga till varningar och meddelanden om ett tröskelvärde uppnås, t.ex. när det blir ont om utrymme på hårddisken. Vissa verktyg ger utdata som ska spåras och beräknas, till exempel resultat av inläsningstest. Oavsett vilket verktyg du använder har alla verktyg ett syfte och när de används på ett konsekvent sätt kan de hjälpa dig att hantera programmet. Det finns kostnadsfria alternativ för alla verktyg, men kom ihåg att betala för en tjänst ofta ger snabbare och tillförlitligare support och kan vara värd investeringen. New Relic är ett exempel på ett verktyg som erbjuder ett kostnadsfritt skikt och en betalversion som frigör mycket mer kraft och möjligheter. Det finns andra, till exempel DataDog eller Dynatrace. Hitta ett bra alternativ för dig och använd det konsekvent.

## Infrastrukturövervakning

I detta sammanhang används termen infrastruktur i ganska liten utsträckning. I det här avsnittet innebär detta alla servrar, processer eller enheter som används för att få webbplatsen att fungera. Exempel:

* Hårddisk
* CPU-användning
* RAM-användning
* Redis
* Genomsnittlig belastning per server
* nätverkstrafik

Tröskelvärden för att skapa effektiva aviseringar. Tilldela inte något för viktiga saker, t.ex. hårddiskkapacitet. Ställ in några för att meddela olika grupper när det blir värre. Här följer till exempel en uppsättning regler när en hårddisk börjar bli full.

* 70 % Slack-meddelande till DevOps-kanalen
* 80 % Notify the Slack room DevOps channel and an email distribution list of DevOps teammates
* 90 % Notify Slack DevOps channel and production support Slack channel, email DevOps distribution group and the engineering manager
* 95 % Notify Slack DevOps and production support Slack channel, email distribution list of all engineering and Director of engineering
* 98 % Notify any P1 Slack channel and DevOps and production support Slack channel, email distribution list of Engineers and Director of Engineering and VP of technology

Det finns många sätt att meddela ett team, så se till att du väljer ett som är tillförlitligt och inte översvämmas av för många larm. Det är viktigt att reservera varningar när det är viktigt, annars riskerar du att bli överväldigad och börjar ignorera varningar.

Det finns ofta bra mallar att följa för de flesta verktyg som New Relic, DataDog och Dynatrace. Ta dig tid att hitta bra idéer som passar ditt program bäst. Med Adobe Commerce i molninfrastruktur finns det varningar och utlösare när projektet etableras. Detta gör det möjligt för produktionsteamet på Adobe att använda sina verktyg för drifttid och övervakning av hög tillgänglighet.

Instrumentpaneler ger snabb åtkomst till de vanliga eller viktiga aspekterna av din webbplats. Kontrollpanelsobjekten kan bestå av sidvyer, processoranvändning per värd, lista över alla servrar, sidladdningstider, transaktionstider och till och med syntetiska övervakningstester de senaste dagarna. Dessa instrumentpaneler bör byggas så att det går snabbt att trivas om något är fel, eller olika instrumentpaneler som har konfigurerats för olika användarupplevelser. Förhoppningsvis kan du utforma flera kontrollpaneler och se hur applikationsövervakningen ser ut i realtid. Den är mycket tillfredsställande, särskilt om du tillfrågas av projektägaren eller en projektledare om hur webbplatsen fungerar, och du hittar svaret på frågan i sekunder, inte timmar.

## Loggsamling och rotation

Loggfiler finns på programservrar som bearbetar begäranden eller MySQL-loggar när det tar för lång tid att köra. Det svåraste med loggar är att de är åtskilda från varandra och att hitta alla, och att analysera informationen från varje logg kan vara besvärligt. För många år sedan löstes problemet med en teknik som kallas _loggaggregering_. Detta tar loggfiler från alla dina loggplatser som överför dem till en central plats. När dokumenten har flyttats kan en del program läsa dem och ge olika sätt att söka, filtrera och granska informationen. Det här kan vara en svår process att få rätt. Det finns många alternativ, men om du har tur kan övervakningsverktygen läsa och sammanställa dina loggfiler, till exempel New Relic. Genom att hitta ett bra verktyg kan du spara dig själv en omätbar tid i framtiden. Om du inte bara har en enda server som gör allt för att din webbplats ska kunna köras och fungera är det viktigt att du har en loggaggregering. Detta är särskilt användbart när du försöker ta reda på om du är utsatt för en DDoS-attack eller upplever en legitim trafikspik, eller när du undersöker varför en viss begäran misslyckas.

En annan viktig del för loggarna är att se till att rotationen sker. Det här historiskt gäller `run-away logs` som av misstag kan fylla i hårddisken och få webbplatsen att krascha. En version av loggrotation kan inträffa när en loggfil når en viss storlek, till exempel 1 GB. Det finns verktyg på servernivå som `logrotate` som automatiskt kan ta bort dem. Den kan t.ex. ta bort mycket stora loggfiler när de blir större än 1 GB eller ta bort loggfiler som är äldre än 90 dagar. Du definierar en loggpolicy, så det är viktigt att förstå dina resursbegränsningar.

## Skannade program

Många webbhotell som är dedikerade till Adobe Commerce har ett bibliotek med kända explosioner och skadlig kod. De bör erbjuda en skanning antingen automatiskt eller på begäran. Där de är effektiva är de reaktionära och fungerar bara när ny skadlig kod upptäcks. Det kan vara en bra idé att ha ett proaktivt verktyg som kan undersöka koden och databasen för känd skadlig kod. Det finns ett antal alternativ, till exempel [MageReport](https://www.magereport.com){target="_blank"}, [Sansec](https://sansec.io){target="_blank"}, or [Magento Malware Scanner](https://github.com/gwillem/magento-malware-scanner){target="_blank"}. De kan antingen göra en fjärrsökning utifrån eller installeras och uppdatera/skanna/övervaka proaktivt efter att de har konfigurerats på servrarna. Dessa kan vara ett bra alternativ eftersom deras bibliotek uppdateras kontinuerligt eftersom de installeras och övervakar tusentals webbplatser om du väljer en lösning som Sansec. När en ny skadlig kod upptäcks kommer varje projekt de övervakar att informationen är bra och nu kommer att uppmärksammas om den upptäcks.

Det finns några kostnadsfria versioner att tänka på, men för skadlig kod bör du verkligen överväga en betallösning. Detta kan vara en skillnad mellan din infektion under några minuter och några månader. Att ha ett utnyttjandemärke på er sajt orsakar enorma problem, det här är ett område som man bör överväga att betala för en tjänst.

## Adobe Site-Wide Analysis Tool

Site-Wide Analysis Tool är ett proaktivt självbetjäningsverktyg och en central lagringsplats som innehåller detaljerade systeminsikter och rekommendationer för att säkerställa säkerheten och användbarheten för din Adobe Commerce-installation. Den ger prestandaövervakning, rapporter och råd i realtid dygnet runt alla dagar för att identifiera potentiella problem och bättre synlighet för webbplatsens hälsa, säkerhet och programkonfigurationer. Det minskar upplösningstiden och förbättrar webbplatsens stabilitet och prestanda.

På sidan Recommendations i verktyget för webbplatsanalys visas rekommendationer baserade på bästa praxis för att åtgärda problem som upptäcks på din webbplats. Rekommendationerna sorteras efter prioriterad PO till P4, där PO är kritiskt och P4 är lågt. Resultatet är beskrivning, rekommendation, webbplatsens påverkan, rotorsak, scenarier/förhandsförhållanden, förväntat resultat och verktyg som används.

Lär dig mer om de bästa sätten att förbättra webbplatsens prestanda. Spåra och implementera de rekommendationer som anges per prioritet.

Mer information om hur du installerar detta i ditt projekt finns på [Installationshandbok för Site-Wide Analysis Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/installation.html){target="_blank"}.

## SSL-övervakning

Ett av de mer glömda objekten i ett projekt är SSL-certifikatet. De behöver bara uppmärksammas en gång om året, så det är mycket enkelt att glömma dem. Om ditt säkerhetscertifikat upphör att gälla kan det leda till att webbläsare varnar eller vägrar visa sidorna på din webbplats. Kunder kan börja skicka e-post eller ringa support om de får ett sådant problem och du kanske inte kan arbeta förrän det har lösts. Varje minut räknas, så det är av största vikt att känna igen förfallotiden och se till att allt förnyas för att hålla webbplatsen igång. Det finns många sätt att utföra SSL-övervakning. Överväg att använda syntetiska övervakningsverktyg för er webbplats med kostnadsfria verktyg eller lågkostnadsverktyg som Storbritannien, Keybröst eller Sucuri och till och med prenumerera på en tjänst som erbjuder SSL-certifikatets förfallovarningar. Dessa enkla verktyg kan säkerställa att era platscertifikat är giltiga och minskar risken för driftstopp för era kunder.

## Automatiserad testning

Att utföra automatiska tester som funktionstester eller enhetstester hjälper ofta till att upptäcka problem med nyligen införd kod. Dessa tester kanske inte fångar upp allt eftersom Adobe Commerce och enhetstester vanligtvis har mindre än 50 % täckning. Det betyder inte att du bör undvika att skriva och testa dem. De här verktygen finns här för att lägga till ytterligare ett säkerhets- och säkerhetsskikt som inte påverkar resultatet negativt och eventuella anpassade tester som utvecklingsgruppen skapar. Genom att köra dessa tester på varje driftsättning fångas eventuella stora problem upp tidigt och undviker att tillåta saker att göra sig av med produktionen.

Belastningstester kan vara svåra att få det rätt. Mycket av komplexiteten kommer från hur frontend används och implementeras. Om din webbplats har en headless edge kan du läsa in testnings-API:erna för GraphQL och REST. Det är upp till dig och DevOps-teamet att avgöra hur belastningstesten ska gå till. Se till att varje laddningstest, som utförs så snart som möjligt, ger en inblick i projektets status. Den innehåller också riktmärken för framtida provningar för att se om det finns några drastiska förändringar i belastningsprovningsresultaten. Om så är fallet, och de är negativa, är detta ett bra tillfälle att granska de senaste kodändringarna och leta efter prestandapåverkande avsnitt som kan förbättras.

Adobe Commerce har goda riktlinjer för att förstå hur du kör enhetstester, se [Testning av PHP-enheter](https://developer.adobe.com/commerce/testing/guide/unit/){target="_blank"} i _Programtestguide_ på Adobe Developer dokumentationswebbplats.

Mer information om funktionstestning finns på [Introduktion till Functional Testing Framework](https://developer.adobe.com/commerce/testing/functional-testing-framework/){target="_blank"}.


{{$include /help/_includes/hosting-related-links.md}}
