---
title: Säkerhet för molninfrastruktur
description: Läs om hur vi skyddar Adobe Commerce i molninfrastrukturen.
exl-id: cd5d1106-c8db-4b70-b1c7-12378d7d77a7
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---

# Säkerhet

Planarkitekturen i Adobe Commerce Pro är utformad för att ge en mycket säker miljö. Varje kund driftsätts i sin egen isolerade servermiljö, skild från andra kunder. Säkerhetsdetaljerna för produktionsmiljön beskrivs nedan.

## Webbläsare

Största delen av trafiken i och från molnmiljön kommer från konsumenternas webbläsare. Konsumenttrafiken kan säkras med HTTPS för alla sidor på webbplatsen (med antingen en delad SSL-certifiering eller kundens eget SSL-certifikat mot en extra avgift). Utchecknings- och kontosidor hanteras alltid med HTTPS. Det bästa sättet är att hantera alla sidor under HTTPS.

## CDN (Content Delivery Network)

Tillhandahåller snabbt ett CDN-skydd och DoS-skydd (Distributed Denal of Service). Snabbt CDN hjälper till att isolera direkt åtkomst till de ursprungliga servrarna. Den offentliga DNS:en pekar bara på snabbnätverket. Fast DDoS-lösningen skyddar mot mycket störande Layer 3- och Layer 4-attacker samt mer komplexa Layer 7-attacker. Layer 7-attacker kan blockeras med anpassade regler som baseras på hela HTTP/HTTPS-begäranden och som baseras på klient- och frågekriterier som headers, cookies, begärandesökväg och klient-IP, eller indikatorer som geolocation.

## Brandvägg för webbprogram (WAF)

WAF (Snably Web Application Firewall) används för att ge ytterligare skydd. I Fastys molnbaserade WAF används tredjepartsregler från kommersiella och öppna källor som OWASP Core-regler. Dessutom används Adobe Commerce-specifika regler. Kunderna skyddas från viktiga attacker på applikationsnivå, inklusive injektionsangrepp och skadliga indata, korsskriptning mellan webbplatser, dataexfiltrering, HTTP-protokollöverträdelser och andra OWASP Top 10-hot.

WAF-reglerna uppdateras av Adobe Commerce om nya säkerhetsluckor upptäcks som gör det möjligt för Managed Services att&quot;åtgärda&quot; säkerhetsproblem i stort sett innan programkorrigeringar görs. Fast WAF tillhandahåller inte hastighetsbegränsande eller robotdetekteringstjänster. Om så önskas kan kunderna licensiera en tredjepartstjänst för robotdetektering som är kompatibel med Fastly.

## Virtuellt privat moln (VPC)

Produktionsmiljön för Adobe Commerce Pro-planen är konfigurerad som ett virtuellt privat moln (VPC) så att produktionsservrarna är isolerade och har begränsad möjlighet att ansluta till och från molnmiljön. Endast säkra anslutningar till molnservrar tillåts. Säkra protokoll som SFTP eller rsync kan användas för filöverföringar.

Kunder kan använda SSH-tunnlar för att skydda kommunikationen med programmet. Du kan få tillgång till AWS PrivateLink mot en extra avgift. Alla anslutningar till dessa servrar styrs med AWS säkerhetsgrupper, en virtuell brandvägg som begränsar anslutningarna till miljön. Kundernas tekniska resurser kan komma åt dessa servrar med SSH.

## Kryptering

Amazon Elastic Block Store (EBS) används för lagring. Alla EBS-volymer krypteras med AES-265-algoritmen. Detta innebär att data krypteras i vila. Systemet krypterar också data som överförs mellan CDN och ursprungsservern samt mellan ursprungsservrarna. Kundlösenord lagras som hashar. Känsliga autentiseringsuppgifter, inklusive de för betalnings-gatewayen, krypteras med SHA-256-algoritmen.

Adobe Commerce-programmet stöder inte kryptering på kolumn- eller radnivå eller kryptering när data inte finns tillgängliga eller inte är på väg mellan servrar. Kunden kan hantera krypteringsnycklar inifrån programmet. Tangenter som används av systemet lagras i AWS Key Management System och måste hanteras av Managed Services för att kunna tillhandahålla delar av tjänsten.

## Testning av penetration

Managed Services genomför regelbundna penetrationstester av Adobe Commerce molnsystem med programmet som är klart att användas. Kunderna ansvarar för alla penetrationstester av sina anpassade applikationer.

## Betalningsgateway

Adobe Commerce kräver integrering av betalgateway där kreditkortsdata skickas direkt från kundens webbläsare till betalningstjänsten. Kortdata är aldrig tillgängliga i någon av Managed Services-miljöerna i Adobe Commerce Pro-planen. Åtgärder för transaktioner i e-handelsprogrammet slutförs med en referens till transaktionen från gatewayen.

## Adobe Commerce

Adobe testar regelbundet kärnprogramkoden för att se om det finns några säkerhetsluckor. Patchar för defekter och säkerhetsproblem tillhandahålls kunderna. Product Security Team validerar Adobe Commerce-produkter enligt OWASP:s riktlinjer för programsäkerhet. Flera verktyg för säkerhetsbedömning och externa leverantörer används för att testa och verifiera efterlevnad. Säkerhetsverktygen omfattar:

- Veracode Static och Dynamic Scanning
- RIPS-källkodskontroll
- Trustwave och Alert Logic’s vulnerability scanning services
- Burp Suite Pro
- OWASPZAP
- andSqlMap

Den fullständiga kodbasen skannas med dessa verktyg varannan vecka. Kunderna meddelas om säkerhetsuppdateringar via direkt e-post, meddelanden i programmet och i [Security Center](https://magento.com/security).

Kunderna måste se till att dessa korrigeringsfiler tillämpas på deras anpassade program inom 30 dagar efter lanseringen, enligt PCI-riktlinjerna. Adobe har också en [Verktyg för säkerhetsgenomsökning](https://docs.magento.com/user-guide/magento/security-scan.html) som gör det möjligt för handlare att regelbundet övervaka sina webbplatser och få uppdateringar om kända säkerhetsrisker, skadlig kod och obehörig åtkomst. Verktyget för säkerhetssökning är en kostnadsfri tjänst och kan köras på alla versioner av Adobe Commerce.

Adobe Commerce har en [buggprogram](https://hackerone.com/magento) utöver intern testning. Kunden får dessutom den fullständiga källkoden för programmet för egen granskning om så önskas.

## Skrivskyddat filsystem

All körbar kod distribueras till en skrivskyddad filsystembild, vilket dramatiskt minskar de ytor som kan attackeras. Distributionsprocessen skapar en Squash-FS-avbildning. Detta minskar drastiskt möjligheterna att mata in PHP- eller JavaScript-kod i systemet eller att ändra Adobe Commerce programfiler.

## Fjärrdistribution

Det enda sättet att få körbar kod i Managed Services produktionsmiljö är att köra den genom en provisioneringsprocess. Detta innebär att överföra källkod från källdatabasen till en fjärrdatabas som initierar en distributionsprocess. Åtkomsten till det distributionsmålet är kontrollerad, så du har fullständig kontroll över vem som har åtkomst till distributionsmålet. Alla distributioner av programkod till icke-produktionsmiljön styrs av kunden.

## Loggning

Alla AWS-aktiviteter loggas i AWS CloudTrail. Linux-, programserver- och databasloggar lagras på produktionsservrarna och lagras i säkerhetskopior. Alla ändringar av källkoden registreras i en Git-databas. Distributionshistorik finns i Adobe Commerce [Project Web Interface](https://devdocs.magento.com/cloud/project/projects.html#login). All supportåtkomst loggas och supportsessioner registreras.

## Känsliga data

Känsliga data kan omfatta antingen personuppgifter från konsumenter eller konfidentiella uppgifter från Managed Services-kunder. Skyddet av känsliga data från kunder och konsumenter är en viktig skyldighet för Adobe Commerce Managed Services. Både Managed Services och våra kunder har juridiska skyldigheter när det gäller personligt identifierbar information. Förutom arkitekturens säkerhetsfunktioner finns det andra kontroller som begränsar distributionen och åtkomsten till känsliga data.

Kunderna äger sina data och har kontroll över var dessa data kommer att placeras. Kunden anger var deras produktions- och utvecklingsinstanser finns. De anger också vilken plats som ska användas för Magento Business Intelligence-miljön (MBI) i samverkan med Commerce, och om MBI-programmet har tillgång till personligt identifierbar information eller inte. Produktionsinstanser kan finnas i de flesta AWS-regioner, medan utvecklings- och MBI-miljöer för närvarande kan vara både i USA och i EU.

Känsliga data kan passera genom snabbnätverket för CDN-servrar, men lagras inte i snabbnätverket. Alla partners som ingår i Adobe Commerce Managed Services har avtalsenliga skyldigheter att skydda känsliga uppgifter. Managed Services flyttar inte känsliga kund- eller konsumentdata från de platser som kunden anger.

Som en del av tjänsterna i Adobe Commerce Managed Services kräver Managed Services personal tillgång till produktionssystem som innehåller känsliga data. Dessa medarbetare har utbildats för att skydda känsliga kunddata och konsumentdata. Tillgång till dessa system är begränsad till medarbetare som behöver åtkomst. Dessa anställda har bara tillgång till den tid som behövs för att kunna leverera dessa tjänster.

## Allmänna dataskyddsförordningen (GDPR)

GDPR är en rättslig ram som fastställer riktlinjer för insamling och behandling av personuppgifter för enskilda personer inom EU. Dessa bestämmelser gäller oavsett var webbplatsen är baserad, och EU-besökare har tillgång till den.

I grund och botten måste besökarna informeras om de data som webbplatsen samlar in från dem och uttryckligen godkänna informationsinsamlingen. Webbplatserna måste meddela besökarna om de personuppgifter som finns på webbplatsen bryts.

Den handlare eller det företag som driver webbplatsen måste också ha ett särskilt uppgiftsskyddsombud som ansvarar för webbplatsens datasäkerhet, och denna person (eller webbplatsens ledningsgrupp) ska vara tillgänglig för kontakt om en besökare begär att deras data raderas.

GDPR kräver också att all personligt identifierbar information (t.ex. namn, ras och födelsedatum) som samlas in antingen ska anonymiseras eller pseudonymiseras.

>[!NOTE]
>
> Den här sidan är helt enkelt avsedd som en allmän översikt över vad som ska övervägas för den allmänna dataskyddsförordningen. För mer information, kontakta ditt juridiska ombud eller se[officiell text](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Säkerhetskopior

Säkerhetskopieringar utförs varje timme under de senaste 24 timmarna. Efter 24-timmarsperioden sparas säkerhetskopiorna enligt följande schema med tjänsten AWS EBS Snapshot:

| Tidsperiod | Lagringsprincip för säkerhetskopia |
|----------------|-------------------------|
| Dagar 1 till 3 | Varje säkerhetskopia |
| Dagar 4 till 6 | En säkerhetskopiering per dag |
| Vecka 2 till 6 | En säkerhetskopia per vecka |
| Vecka 8 till 12 | En säkerhetskopiering varannan vecka |
| Vecka 12 till 22 | En säkerhetskopia per månad |

Detta skapar en oberoende säkerhetskopiering av redundant lagring. Eftersom EBS-volymerna är krypterade krypteras även säkerhetskopiorna. Dessutom utför Managed Services säkerhetskopiering på begäran av kunden.

Adobe Commerce Managed Services metod för säkerhetskopiering och återställning använder en arkitektur med hög tillgänglighet kombinerat med säkerhetskopiering i hela systemet. Varje projekt replikeras - data, kod och resurser - mellan tre olika tillgänglighetszoner för AWS. varje zon med ett separat datacenter.
