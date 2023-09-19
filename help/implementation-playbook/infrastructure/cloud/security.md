---
title: Säkerhet för molninfrastruktur
description: Läs om hur Adobe skyddar Adobe Commerce i molninfrastrukturen.
exl-id: cd5d1106-c8db-4b70-b1c7-12378d7d77a7
feature: Cloud, Security
source-git-commit: 8d8cd0d33c1a3a95186948e670df6d9865b9a871
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 0%

---


# Säkerhet

Adobe Commerce [Proffsarkitektur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) är utformat för att ge en mycket säker miljö. Varje kund driftsätts i sin egen isolerade servermiljö, skild från andra kunder. Säkerhetsdetaljerna för produktionsmiljön beskrivs nedan.

## Webbläsare

Största delen av trafiken i och från molnmiljön kommer från konsumenternas webbläsare. Konsumenttrafiken kan säkras med HTTPS för alla sidor på webbplatsen (med antingen en delad SSL-certifiering eller kundens eget SSL-certifikat mot en extra avgift). Utchecknings- och kontosidor hanteras alltid med HTTPS. Det bästa sättet är att hantera alla sidor under HTTPS.

## Content Delivery Network

Tillhandahåller snabbt ett CDN-skydd (Content Delivery Network) och DoS-skydd (Distributed Denial of Service). Snabbt CDN hjälper till att isolera direkt åtkomst till de ursprungliga servrarna. Den offentliga DNS:en pekar bara på snabbnätverket. Den snabba DDoS-lösningen skyddar mot mycket störande Layer 3- och Layer 4-attacker och mer komplexa Layer 7-attacker. Layer 7-attacker kan blockeras med anpassade regler som baseras på hela HTTP/HTTPS-begäranden och som baseras på klient- och frågekriterier som headers, cookies, begärandesökväg och klient-IP, eller indikatorer som geolocation.

Se [Snabb översikt över tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html) i _Molnguide_.

## Brandvägg för webbaserade program

WAF (Snably Web Application Firewall) används för att ge ytterligare skydd. Fastly molnbaserade WAF använder tredjepartsregler från kommersiella och öppna källor som OWASP Core-regler. Dessutom används Adobe Commerce-specifika regler. Kunderna skyddas från viktiga attacker på applikationsnivå, inklusive injektionsangrepp och skadliga indata, serveröverskridande skriptning, dataexfiltrering, HTTP-protokollöverträdelser och andra tio hot mot OWASP.

WAF-reglerna uppdateras av Adobe Commerce om nya säkerhetsluckor upptäcks som gör att Managed Services kan&quot;åtgärda&quot; säkerhetsproblem före programkorrigeringar. Fast WAF tillhandahåller inte hastighetsbegränsande eller robotdetekteringstjänster. Om så önskas kan kunderna licensiera en tredjepartstjänst för robotdetektering som är kompatibel med Fastly.

Se [Brandvägg för webbaserade program (WAF)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service.html) i _Molnguide_.

## Virtuellt privat moln

Produktionsmiljön för Adobe Commerce Pro-planen är konfigurerad som ett virtuellt privat moln (VPC) så att produktionsservrarna är isolerade och har begränsad möjlighet att ansluta till och från molnmiljön. Endast säkra anslutningar till molnservrar tillåts. Säkra protokoll som SFTP eller rsync kan användas för filöverföringar.

Kunder kan använda SSH-tunnlar för att skydda kommunikationen med programmet. Du kan få tillgång till AWS PrivateLink mot en extra avgift. Alla anslutningar till dessa servrar styrs med AWS säkerhetsgrupper, en virtuell brandvägg som begränsar anslutningarna till miljön. Kundernas tekniska resurser kan komma åt dessa servrar med SSH.

## Kryptering

Amazon Elastic Block Store (EBS) används för lagring. Alla EBS-volymer krypteras med AES-256-algoritmen, vilket innebär att data krypteras i vila. Systemet krypterar också data som överförs mellan CDN och ursprungsservern samt mellan ursprungsservrarna. Kundlösenord lagras som hashar. Känsliga autentiseringsuppgifter, inklusive autentiseringsuppgifter för betalningsgateway, krypteras med SHA-256-algoritmen.

Adobe Commerce-programmet stöder inte kryptering på kolumn- eller radnivå eller kryptering när data inte finns tillgängliga eller inte är på väg mellan servrar. Kunden kan hantera krypteringsnycklar inifrån programmet. Tangenter som används av systemet lagras i AWS Key Management System och måste hanteras av Managed Services för att kunna tillhandahålla delar av tjänsten.

## Slutpunktsidentifiering och -svar

[!DNL CrowdStrike Falcon], installeras en lättviktsagent, nästa generationens EDR-agent (Endpoint Detection and Response) på alla slutpunkter (inklusive servrar) inom Adobe. EDR-agenter skyddar data och system från Adobe med kontinuerlig övervakning och insamling i realtid, vilket möjliggör snabb identifiering och åtgärder av hot.

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

Den fullständiga kodbasen skannas med dessa verktyg varannan vecka. Kunderna meddelas om säkerhetsuppdateringar via direkt e-post, meddelanden i programmet och i [Security Center](https://helpx.adobe.com/security.html).

Kunderna måste se till att dessa korrigeringsfiler tillämpas på deras anpassade program inom 30 dagar efter lanseringen, enligt PCI-riktlinjerna. Adobe har också en [Verktyg för säkerhetsgenomsökning](https://docs.magento.com/user-guide/magento/security-scan.html) som gör det möjligt för handlare att regelbundet övervaka sina webbplatser och få uppdateringar om kända säkerhetsrisker, skadlig kod och obehörig åtkomst. Verktyget för säkerhetssökning är en kostnadsfri tjänst och kan köras på alla versioner av Adobe Commerce.

Adobe Commerce har en [buggprogram](https://hackerone.com/magento) utöver intern testning. Kunden får dessutom den fullständiga källkoden för programmet för egen granskning om så önskas.

## Skrivskyddat filsystem

All körbar kod distribueras till en skrivskyddad filsystembild, vilket dramatiskt minskar de ytor som kan attackeras. Distributionsprocessen skapar en Squash-FS-avbildning för att minska möjligheterna att injicera PHP- eller JavaScript-kod i systemet eller ändra Adobe Commerce-programfiler.

## Fjärrdistribution

Det enda sättet att få körbar kod i Managed Services produktionsmiljö är att köra den genom en provisioneringsprocess. Etablering innebär att överföra källkod från källdatabasen till en fjärrdatabas som initierar en distributionsprocess. Åtkomsten till det distributionsmålet är kontrollerad, så du har fullständig kontroll över vem som har åtkomst till distributionsmålet. Alla distributioner av programkod till icke-produktionsmiljön styrs av kunden.

## Loggning

Alla AWS-aktiviteter loggas i AWS CloudTrail. Operativsystem, programserver och databasloggar lagras på produktionsservrarna och lagras i säkerhetskopior. Alla ändringar av källkoden registreras i en Git-databas. Distributionshistorik finns i Adobe Commerce [Project Web Interface](https://devdocs.magento.com/cloud/project/projects.html#login). All supportåtkomst loggas och supportsessioner registreras.

Se [Visa och hantera loggar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) i _Molnguide_.

## Känsliga data

Känsliga data kan omfatta antingen personuppgifter från konsumenter eller konfidentiella uppgifter från Managed Services-kunder. Skyddet av känsliga data från kunder och konsumenter är en viktig skyldighet för Adobe Commerce Managed Services. Både Managed Services- och Adobe-kunder har juridiska skyldigheter avseende personligt identifierbar information. Förutom arkitekturens säkerhetsfunktioner finns det andra kontroller som begränsar distributionen och åtkomsten till känsliga data.

Kunderna äger sina data och har kontroll över var dessa data finns. Kunden anger var deras produktions- och utvecklingsinstanser finns. De anger också vilken plats som används för Adobe Commerce rapporteringsmiljö med Commerce och om det Adobe Commerce Reporting-programmet har tillgång till personligt identifierbar information eller inte. Produktionsinstanser kan finnas i de flesta AWS-regioner, medan utvecklings- och Adobe Commerce Reporting-miljöer för närvarande finns i antingen USA eller EU.

Känsliga data kan passera genom snabbnätverket för CDN-servrar, men lagras inte i snabbnätverket. Alla partners som ingår i Managed Services-erbjudandet har avtalsenliga skyldigheter att säkerställa skydd av känsliga uppgifter. Managed Services flyttar inte känsliga kund- eller konsumentdata från de platser som kunden anger.

Som en del av att tillhandahålla de tjänster som ingår i Managed Services-erbjudandet behöver Managed Services personal tillgång till produktionssystem som innehåller känsliga data. Dessa medarbetare har utbildats för att skydda känsliga kunddata och konsumentdata. Tillgång till dessa system är begränsad till medarbetare som behöver åtkomst. Dessa anställda har bara tillgång till den tid som behövs för att kunna leverera dessa tjänster.

## Allmän dataskyddsförordning

Den allmänna dataskyddsförordningen (GDPR) är en rättslig ram som fastställer riktlinjer för insamling och behandling av personuppgifter för enskilda personer inom EU. Dessa bestämmelser gäller oavsett var webbplatsen är baserad, och EU-besökare har tillgång till den.

Besökarna måste underrättas om vilka data en webbplats samlar in och uttryckligen samtycker till informationsinsamling. Webbplatserna måste meddela besökarna om de personuppgifter som finns på webbplatsen bryts.

Den handlare eller det företag som driver webbplatsen måste ha ett särskilt uppgiftsskyddsombud som ansvarar för webbplatsens datasäkerhet. Data Privacy Officer (eller webbplatshanteringsteamet) ska vara tillgänglig för kontakt om en besökare begär att deras data ska raderas.

GDPR kräver att all personligt identifierbar information (t.ex. namn, ras och födelsedatum) som samlas in antingen anonymiseras eller pseudonymiseras.

>[!NOTE]
>
>Den här sidan innehåller en allmän översikt över vad du bör tänka på för GDPR. Se _[Handbok för säkerhet och efterlevnad](../../../security-and-compliance/privacy/gdpr.md)_ om du vill veta mer om hur Adobe Commerce lagrar personuppgifter. För att avgöra hur ditt företag ska uppfylla juridiska skyldigheter, rådfråga ditt juridiska ombud eller se [officiell text](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Säkerhetskopior

Säkerhetskopieringar utförs varje timme under de senaste 24 timmarna. Efter 24-timmarsperioden sparas säkerhetskopior enligt ett schema med tjänsten AWS EBS Snapshot. Se [Bevarandeprincip](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#retention-policy) i _Molnguide_.

Tjänsten skapar en oberoende säkerhetskopiering av redundant lagring. Eftersom EBS-volymerna är krypterade krypteras även säkerhetskopiorna. Managed Services utför även säkerhetskopiering på begäran av kunden.

Managed Services metod för säkerhetskopiering och återställning använder en arkitektur med hög tillgänglighet kombinerat med säkerhetskopiering i hela systemet. Varje projekt replikeras - data, kod och resurser - mellan tre olika tillgänglighetszoner för AWS; varje zon har ett separat datacenter.

Se [Ögonblicksbilder och hantering av säkerhetskopiering](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html) i _Molnguide_.
