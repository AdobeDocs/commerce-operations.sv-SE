---
title: Självvärdande tips för Adobe Commerce
description: Lär dig mer om självbetjäningstips och idéer och de bästa metoderna att tänka på.
landing-page-description: Lär dig några tips och saker att tänka på när du är värd för Adobe Commerce på egen hand.
short-description: Lär dig strategier och tips om hur du själv kan vara värd för Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: ab099b2a8a353c2462424831cf8100e7e281b1be
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---


# Självvärdande tips för Adobe Commerce

Att använda en flexibel och kraftfull e-handelsplattform innebär inte att du behöver offra prestanda. Det har gjorts många förbättringar i kärnapplikationen sedan Adobe Commerce invigdes. I version 2.5.4 utförde Adobe Commerce tekniker ett test för att testa applikationen. Testresultaten visar att Adobe Commerce klarar att hantera en stor katalog på över 240 miljoner SKU:er, API:s handläggningstider är ett enastående medelvärde på 300 ms och antalet sidvisningar och beställningar per timme är fenomenalt vid 2 miljoner sidvisningar och 208 000 beställningar per timme.

Se de senaste prestandatestresultaten genom att gå över till [Experience League - Adobe Commerce - Implementeringsspelbok - prestandatecken](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

Följ dessa standarder när du lägger till anpassningar och ytterligare komplexitet i ditt projekt, så att du kan optimera saker och ting så bra som möjligt.

I följande avsnitt beskrivs ämnen som du bör tänka på och råd om hur du kan optimera implementeringen av din värdtjänst.

## Varnish

Avvikelse är HTTP-omvänd proxy med cache. Hur komplicerat det än kan tyckas är resultatet snabba svar för att säkerställa att förfrågningarna returneras snabbare än om det var nödvändigt att hämta objektet från källan. Om du kör en Adobe Commerce-webbplats utan någon version av Varnish blir sidinläsningen långsammare och andra viktiga mätvärden. Det kan vara lite svårt att konfigurera och hantera sig själv, men vi har det här ämnet i Experience League [Konfigurera lack](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} för att få en bättre förståelse för hur den används med Adobe Commerce. Ett alternativ är att använda en molnbaserad lösning. Även om det finns många att tänka på har Fastly valts som lösning för Adobe Commerce i molnet. Det är en version av Fastly, molnbaserad, som använder VCL:er och många fernissa.

Det är svårt att hitta en lösning som bäst passar program, konfiguration, budget och tekniska funktioner. Om du använder ett molnbaserat alternativ försvinner alla hårda delar så långt hantering, konfiguration, servrar och andra infrastrukturkomponenter beaktas. Den har valts ut av Adobe Commerce i molnteamet som sin lösning på grund av dess prestanda, skalbarhet, genomströmning och många andra viktiga mätvärden.

Genom att välja en bra lösning för ditt projekt när det gäller Varnish, skapar du dig själv för bästa prestanda för dina kunder och sparar affärsapplikationen så att den inte arbetar så hårt som den måste.

## CDN

Tillsammans med Varnish som är en värdefull tillgång för ditt Adobe Commerce-projekt är nästa rad ett CDN. Tillsammans med din engelska kan ett CDN tillhandahålla cachelagrade instanser för din CSS, sidresurser som bilder för att minska bandbredden i ditt Adobe Commerce-program. Det kan cache-lagra GraphQL-svar och ytterligare utnyttja fördelarna med en headless Adobe Commerce-webbplats. Vissa CDN-nummer erbjuder bildoptimering, en brandvägg för webbprogram och andra funktioner.

Adobe Commerce i molnet valde att använda Fastly för sitt Varnish-cacheminne men också som sitt CDN. Denna enda lösning innehåller en mängd funktioner som ger en enastående upplevelse för Adobe Commerce på molnkunder. Du kan läsa snabbtjänstöversikten i Experience League [Snabb översikt över tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

Ett CDN ger optimerat och säkert leveransinnehåll för Adobe Commerce-projektet. Om detta inte är en nödvändig komponent i ditt projekt bör det beaktas när webbplatsen mognar och antalet besökare ökar. Genom att tillhandahålla ett CDN kan du fördröja tillägg av ytterligare maskinvara till infrastrukturen eller skalning av den befintliga infrastrukturen på grund av den belastning som tas bort från varje begäran.

## Inaktivera moduler

Inaktivering av en oanvänd modul bör övervägas, men inte tas lätt. Den här tekniken minskar vissa kostnader och bearbetningstid för vissa förfrågningar, men det finns biverkningar som bör beaktas. Det finns ofta tillfällen när en utvecklare antar att en modul är tillgänglig när de skapar funktioner. Detta är ofta säkert, såvida de inte väljer att använda vissa klasser som finns i en modul som har inaktiverats.

Det är ganska vanligt att inaktivera en modul som det ursprungliga nyhetsbrevet. Detta gäller särskilt när butiksägaren har ett tredjepartsföretag som hanterar deras nyhetsbrev. Det här kan vara ett problem när en tredjepartsmodul är installerad och av någon anledning bestämde de sig för att använda en klass från nyhetsbrevet. Detta oavsiktliga beroende kommer troligtvis att fångas upp under en inledande installation och testning, men du måste sedan bestämma om du vill behålla den här tredjepartsmodulen, aktivera nyhetsbrevet och sedan regressionstesta webbplatsen för att hitta något ojämnt beteende som tillkommit. Eller så hittar du en ersättning för den tredjepartsmodulen. Bägge besluten är riskfyllda, tidskrävande och möjligen buggar.

Innan du inaktiverar oanvända moduler bör du kontrollera att du inte har några tester, till exempel enheten, [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} inläsningstest eller API-begäranden som kan påverkas.

## Kräv att Adobe Commerce- och PHP-kodningsstandarder följs för varje pull-begäran

Adobe Commerce har en uppsättning [Kodstandarder](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. Dessa hjälper till att säkerställa att liknande mönster, format och förväntad design följs oavsett typ av programutveckling. När du bidrar till Adobe Commerce-kodbasen är detta ett krav. Om du väljer att följa den här metoden för anpassad utveckling skapar du emellertid en solid hörnsten för alla utvecklare, både nuvarande och framtida. När alla pull-begäranden måste skicka en kodstandard, blir det lättare att se och förvänta sig samma enhetliga utvecklingsmönster.

Som en del av Adobe Commerce kodningsstandarder används även PHP:s grundläggande kodningsstandarder. Det bör tydligt definieras i utvecklarhandböckerna vilka standarder du måste följa och eventuella avvikelser som är godtagbara. En reservdel bör dock utgå från den allmänna handboken på [PHP-FIG](https://www.php-fig.org){target="_blank"}.

En fast hållning efter PSR-1 och PSR-12. Genom att se till att de utvecklare som bidrar till projektet följer dessa säkerställer du att det inte finns några välstrukturerade filer och mönster. Detta bidrar också till att framtida utvecklare snabbt kan läsa och förstå koden de granskar. Ju närmare ni följer dessa mönster och kodstandarder, desto enklare att läsa och snabbare implementera i framtiden.

## Kör lasttester efter varje distribution

Att utföra ett belastningstest efter varje distribution kan verka överdrivet. Om den här metoden följs kan möjligheten att använda nya funktioner som ger försämrade prestanda spåras och minskas.

Förutom att upptäcka prestandaförsämringar från ny kod kan du med hjälp av en historisk referens till nyckeltal från din webbplats få insikt i när ett nytt verktyg eller en ny infrastruktur är aktiverad. Innan du till exempel betalar värdföretaget för att anpassa miljön och hoppas att du får den prestandaökning du förväntar dig, kan du konfigurera en staging-miljö med de nya konfigurationerna och köra ett lasttest för att se vad det faktiska resultatet blir.

Dessa tester kan automatiseras och ingå i CI/CD-flödet. På grund av detta kan du också ha regler som tar resultaten och eventuellt blockerar sammanslagningen av funktioner om för mycket avvikelse från standarden inträffar. Antalet användningsfall för dessa data är obegränsat, men om du inte startar den här processen kommer du kanske aldrig att inse dess potential.

Adobe Commerce har skrivit en bra text om detta ämne i Experience League [Tips för prestandatestning](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
