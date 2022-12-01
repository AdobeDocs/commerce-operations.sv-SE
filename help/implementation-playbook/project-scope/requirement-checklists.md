---
title: Checklistor för krav
description: Använd den här listan med utförliga frågor för att förbereda er för en implementering av Adobe Commerce.
exl-id: 9ac485c5-d491-4022-9366-5e3a382513b6
source-git-commit: d18be812626723e203d2308be8c3f9783a19b43b
workflow-type: tm+mt
source-wordcount: '1536'
ht-degree: 0%

---

# Checklistor för krav

Följande frågor kan fungera som en utgångspunkt för att se vilken information som bör dokumenteras för att bekräfta organisationens beredskap. De kan också hjälpa till vid utvecklingen av en anbudsförfrågan.

## Företag

- Vilka affärsmål har den nya e-handelsplattformen?

- Vilka är skälen till att du ändrar din nuvarande e-handelsplattform?

- Vilka mål har webbplatsens infrastruktur?

- Vilken är din tidsram för att leverera den nya e-handelsplattformen?

- Hur många av dina IT-projektledare ska tilldelas det här projektet?

- Hur många av dina affärsanalytiker kommer att tilldelas det här projektet?

- Hur många av dina tekniska analytiker kommer att tilldelas det här projektet?

- Hur många av dina HTML-utvecklare kommer att tilldelas det här projektet?

- Vilken dokumentation finns för de aktuella affärsprocesserna?

- Vilken dokumentation finns för den aktuella systemintegreringen?

- Vilken dokumentation finns för aktuella processflöden?

- Vilken dokumentation finns för aktuella dataflöden?

- Vem ska tillhandahålla utbildningen?

- Vilken utbildning kommer att genomföras innan du går live?

- Vilken utbildning kommer att genomföras efter att man gått ut?

- Vilken Adobe Commerce-support krävs efter lanseringen?

- Är projektet beroende av andra systemutvecklingsprojekt?

- Hur ser du att din försäljning ökar under de kommande 12-24 månaderna?

- Vilka är era viktigaste konkurrenter? Ange länkar till deras webbplatser. Hur vill du skilja din onlineupplevelse från dina konkurrenter?

- Var ser ni den framtida tillväxten i er verksamhet?

- Vilken roll spelar digital handel i er affärsstrategi? Vilka är era främsta mål med att skapa denna e-handelsplattform?

- Har ni varumärken/företag som ni använder som referens för hur ni utvecklar ert flerkanalsföretag?

- Vilka team eller individer driver e-handelsstrategin? Beskriv de relevanta positionerna.

## Aktuell plattform

- Hur fungerar den aktuella plattformen? Intern, värdtjänstleverantör, privata molnservrar eller värdbaserade molnservrar?

- Vilka miljöer har den aktuella plattformen? utveckling, kvalitetssäkring, förproduktion, produktion?

- Hur många webb- och databasservrar finns i utvecklingsmiljön?

- Hur många webb- och databasservrar finns i QA-miljön?

- Hur många webb- och databasservrar finns i staging-miljön (förproduktion)?

- Hur många webb- och databasservrar finns i produktionsmiljön?

- Är det en flerserverarkitektur med belastningsutjämning?

- Är det en systemarkitektur med hög tillgänglighet?

- Vilka problem har du med dina aktuella webbplatser?

- Aktuell katalogstorlek (antal SKU:er)?

- Genomsnittligt antal besökare per dag?

- Genomsnittligt antal samtidiga sessioner per timme?

- Genomsnittlig sidvisning per dag?

- Genomsnittlig order per timme och dag?

## Förväntade plattformskrav

- Vilken Adobe Commerce-version ska du använda?

- Hur kommer den framtida plattformen att hanteras? Intern, värdtjänstleverantör, privata molnservrar eller värdbaserade molnservrar?

- Vilka miljöer kommer den framtida plattformen att ha: utveckling, kvalitetssäkring, förproduktion, produktion?

- Hur många webb- och databasservrar kommer att finnas i utvecklingsmiljön?

- Kommer det att vara en systemarkitektur med hög tillgänglighet?

- Hur många Adobe Commerce-administratörer har du?

- Förväntad katalogstorlek (antal SKU:er)?

- Förväntade genomsnittliga besökare per dag?

- Förväntade samtidiga sessioner per timme?

- Förväntade genomsnittliga sidvisningar per dag?

- Vilka data ska importeras från den gamla platsen till den nya? (Exempel: produkt, kund, orderhistorik)

## Webbplatser

- Hur många inhemska webbplatser kommer att implementeras?

- Vilka språk kommer att implementeras?

- Hur många internationella webbplatser kommer att implementeras?

- Vilka regioner kommer webbplatserna att stödja?

- Vilka språk kommer att implementeras?

- Vilka valutor kommer att implementeras?

- Har ni servicenivåavtal för varje land?

- Vilka är era leveransleverantörer för varje land?

- Vilka är era skatteredovisningsleverantörer för varje land?

- Kommer du att behöva ett anpassat internationellt webbplatstema?

- Är detta i första hand en B2C- eller B2B-webbplats? Finns det några B2B2B- eller B2B2C-element?

- Finns det en befintlig design som är anpassad eller kommer plattformen att utformas från grunden?

- Finns det något krav på headless commerce (separata lager för frontend och backend)?

- Vilka är brytpunkterna (surfplatta/mobil) för den responsiva designen?

- Finns det något krav på en mobilapp? Bör PWA utnyttjas för mobila frontend?

- Eventuella webbläsare som ska testas (förutom standardwebbläsarna IE9+, Firefox, Chrome, Safari)?

- Vilka är språk för varje frontend? Är det översatta innehållet tillgängligt eller krävs det support?

- Finns det flera webbplatser? Om så är fallet, kan kunderna använda sina inloggningsuppgifter för alla webbplatser?

- Är produktdata delade på alla webbplatser?

- Har designen ändrats från plats till plats?

- Finns det prenumerationsalternativ och hur hanteras prenumeranter?

- Finns det specifika krav för SEO? Hur hanteras sökmotormarknadsföring?

## Integreringar

- Vilket CMS-system kommer att integreras med Adobe Commerce? (Exempel: WordPress, Drupal, Concrete5)

Finns det befintliga API:er som kan användas?

- Har hantering av systemfel utformats och utvecklats för denna integrering med system från tredje part?

- Vilket ERP-system ska integreras med Adobe Commerce? (Exempel: SAP, MS Dynamics NAV)

- Vilket transportsystem kommer att integreras med Adobe Commerce?

- Vilket skattesystem kommer att integreras med Adobe Commerce? (Exempel: Taxware)

- Från vilket system importeras produktdata till Adobe Commerce?

- Hur ofta importerade produktdata läses in?

- I vilket system exporterar Adobe Commerce produktdata?

- Hur ofta exporterade produktdata läses in?

- Från vilket system beställs data till Adobe Commerce?

- Hur ofta importerade orderdata läses in?

- I vilket system exporterar Adobe Commerce orderdata?

- Hur ofta exporterade orderdata läses in?

- Vilken analysplattform används? (Exempel: Adobe Analytics, Google Analytics)

- Kommer det att finnas en enda inloggning och delning via sociala nätverk? I så fall, vilka sociala nätverk?

- Finns det några belönings- eller lojalitetsprogram? Finns det någon integrering med POS-system för belöningar?

- Hur hanteras produktreturer? Förväntas kunden logga en returbegäran online?

- Krävs ett chattverktyg online? Behövs en chattbot?

- Vilken betalningsgateway vill du att din webbplats ska ha?

- Vilket orderhanteringssystem kommer att integreras med Adobe Commerce? (Exempel: Microsoft Dynamics, SAP, Retail Pro)

- Vilket produktinformationshanteringssystem kommer att integreras med Adobe Commerce? (Exempel: Akeneo, InRiver, Bluestone)

- Vilket kundhanteringssystem kommer att integreras med Adobe Commerce? (Exempel: Hubspot, Salesforce, Klaviyo)

## Adobe Commerce-specifika funktioner

- Behöver du någon typ av A/B-testning?

- Hur många administratörer kan arbeta samtidigt i systemet?

- Kan ni låta en kund plocka upp artiklar som köpts på webbplatsen i en butik?

- Har ni kampanjsidor?

- Kommer ni att ha marknadsföringsbanners?

- Vill du att videor ska spelas upp på en CMS-sida?

- Hur ofta kommer innehållet att ändras eller uppdateras?

- Vilken typ av innehåll kommer att läsas in?

- Kommer innehållsuppdateringar att schemaläggas?

- Behöver ni en webbplats för innehållstagning?

- Bör kunderna tillåtas att skapa ett webbplatskonto?

- Kommer ni att använda unika rabattkuponger för kampanjer?

- Kommer du att få ett kampanjpris?

- Kommer ni att ha flexibla kuponger (möjlighet att skapa per webbplats, kundgrupp, tid, kategorier eller produkter)?

- Erbjuds rabatter för enskilda artiklar?

- Vilken typ av presentfunktionalitet krävs?

- Kommer det att krävas funktioner för belöningsprogram?

- Kommer nyhetsbrev att behövas?

- Vill du tillåta en kund att visa tidigare order och välja artiklar som ska bytas ut?

- Kan ni låta en kund initiera att en order annulleras från webbplatsen?

- Kommer ni att tillåta en kund att initiera utbytet av objekt från webbplatsen?

- Kräver du adressvalidering i realtid?

- Kommer ni att tillåta kunden att initiera returer av objekt från webbplatsen?

- Kommer Adobe Commerce att skicka tillbaka RMA?

- Spara återbetalningsinformation i Adobe Commerce?

- Kräver ni onlineorderspårning för en registrerad kund?

- Kräver ni onlineorderspårning för en gästkund?

- Vill du genomföra onlineauktorisering och hämtning under orderplacering?

- Auktorisering med bedrägerifilter under orderplacering med fördröjd fångst

- Antal dagar för att få full betalning (inte auktorisering)?

- Vill du hämta och köra när auktoriseringen upphör?

- Authorize.net

- Braintree

- PayPal Express

- Butikskredit

- Presentkort av plast

- Belöningspunkter

- &quot;Bill Me Later&quot; - mer allmänt känt som &quot;Buy Now, Pay Later&quot; eftersom det är fakturerat omedelbart men ännu inte betalat

- Kommer det att finnas olika produktpriser på olika webbplatser?

- Kommer det att behövas funktioner för att jämföra olika produkter?

- Vilka typer av produkter kommer du att sälja?

- Hur ofta kommer nya produkter att läggas till?

- Hur ofta uppdateras produkterna?

- Hur ofta kommer nya kategorier eller underkategorier att skapas?

- Kommer funktionen&quot;Klassificeringar och granskningar&quot; att krävas?

- Kommer ni att tillåta kunderna att rekommendera en produkt?

- Försäljning: Beställningar, moms, fakturerad, frakt, återbetalningar, kuponger, PayPal-kvittningsrapporter

- Kundvagn: Produkter i varukorgar, övergivna konstverk

- Produkter: Bestandesförsäljare, beställda produkter, mest visade, låg lagerhållning, nedladdningar

- Kunder: Nya konton, kunder efter ordersumma, kunder efter antal order, kundsegment, kundrecensioner

- Recensioner

- Taggar: Kunder, produkter, populära

- Sökvillkor

- Inbjudningar: Allmänt, kunder, orderkonverteringsgrad

- Behöver ni Adobe Commerce för att generera rapporter baserade på kuponganvändningsdata?

- Behöver ni Adobe Commerce för att generera rapporter baserade på säljdata?

- Behöver ni skräddarsydda Adobe Commerce-rapporter?

- Vad är er nuvarande SEO-strategi?

- Vad blir er nya SEO-strategi?

- Vilka är dina krav för SEO-migrering?

- Vill du lagra fasta priser i Adobe Commerce?

- Vill du tillåta partiell leverans?

- Ska leveransspårningsinformation lagras i Adobe Commerce?

- Kommer ni att kräva regler för skatteberäkning för era inhemska regioner?

- Kommer ni att kräva regler för skatteberäkning för era internationella regioner?
