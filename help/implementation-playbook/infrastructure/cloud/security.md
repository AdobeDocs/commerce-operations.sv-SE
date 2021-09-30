---
title: Cloud Infrartruktur - säkerhet
description: 'Learn about how we keep Adobe Commerce on cloud infrastructure secure. '
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---


# Security

Planarkitekturen i Adobe Commerce Pro är utformad för att ge en mycket säker miljö. Varje kund driftsätts i sin egen isolerade servermiljö, skild från andra kunder. The security details of the production environment are described below.

## Web browsers

Största delen av trafiken i och från molnmiljön kommer från konsumenternas webbläsare. Consumer traffic can be secured using HTTPS for all pages on the website (using either a shared SSL certification or the customer’s own SSL certificate for an additional fee). Checkout and account pages are always served using HTTPS. The best practice is to serve all pages under HTTPS.

## CDN (Content Delivery Network)

Tillhandahåller snabbt ett CDN-skydd och DoS-skydd (Distributed Denal of Service). Snabbt CDN hjälper till att isolera direkt åtkomst till de ursprungliga servrarna. Den offentliga DNS:en pekar bara på snabbnätverket. Fast DDoS-lösningen skyddar mot mycket störande Layer 3- och Layer 4-attacker samt mer komplexa Layer 7-attacker. Layer 7-attacker kan blockeras med anpassade regler som baseras på hela HTTP/HTTPS-begäranden och som baseras på klient- och frågekriterier som headers, cookies, begärandesökväg och klient-IP, eller indikatorer som geolocation.

## Brandvägg för webbprogram (WAF)

The Fastly Web Application Firewall (WAF) is used to provide additional protection. I Fastys molnbaserade WAF används tredjepartsregler från kommersiella och öppna källor som OWASP Core-regler. Dessutom används handelsspecifika regler för Adobe. Customers are protected from key application-layer attacks, including injection attacks and malicious inputs, cross site scripting, data exfiltration, HTTP protocol violations, and other OWASP Top 10 threats.

WAF-reglerna uppdateras av Adobe Commerce om nya säkerhetsluckor upptäcks som gör det möjligt för Managed Services att&quot;åtgärda&quot; säkerhetsproblem i praktiken innan programfixar installeras. The Fastly WAF does not provide rate-limiting or bot-detection services. If desired, customers can license a third-party bot-detection service compatible with Fastly.

## Virtuellt privat moln (VPC)

Produktionsmiljön för Adobe Commerce Pro-planen är konfigurerad som ett virtuellt privat moln (VPC) så att produktionsservrarna är isolerade och har begränsad möjlighet att ansluta till och från molnmiljön. Only secure connections to the cloud servers are allowed. Secure protocols like SFTP or rsync can be used for file transfers.

Kunder kan använda SSH-tunnlar för att skydda kommunikationen med programmet. Du kan få åtkomst till AWS PrivateLink mot en extra avgift. Alla anslutningar till dessa servrar styrs med hjälp av AWS-säkerhetsgrupper, en virtuell brandvägg som begränsar anslutningarna till miljön. Kundernas tekniska resurser kan komma åt dessa servrar med SSH.

## Encryption

Amazon Elastic Block Store (EBS) is used for storage. Alla EBS-volymer krypteras med AES-265-algoritmen. This means that the data will be encrypted at rest. The system also encrypts data in transit between the CDN and the origin, and between the origin servers. Customer passwords are stored as hashes. Sensitive credentials, including those for the payment gateway, are encrypted using the SHA-256 algorithm.

Programmet Adobe Commerce stöder inte kryptering eller kryptering på kolumn- eller radnivå när data inte är vilande eller inte överförs mellan servrar. Kunden kan hantera krypteringsnycklar inifrån programmet. Keys used by the system are stored in AWS Key Management System and must be managed by Managed Services in order to provide parts of the service.

## Penetration testing

Managed Services genomför regelbundna penetrationstester i molnsystemet för Adobe Commerce med programmet som är klart att användas. Kunderna ansvarar för alla penetrationstester av sina anpassade applikationer.

## Betalningsgateway

Adobe Commerce kräver integrering av betalningsgatewayar där kreditkortsdata skickas direkt från konsumentens webbläsare till betalningsgatewayen. Kortdata är aldrig tillgängliga i Managed Services-miljöer baserade på Adobe Commerce Pro. Åtgärder för transaktioner i e-handelsprogrammet slutförs med en referens till transaktionen från gatewayen.

## Adobe Commerce-applikation

Adobe regularly tests the core application code for security vulnerabilities. Patchar för defekter och säkerhetsproblem tillhandahålls kunderna. The Product Security Team validates Adobe Commerce products following OWASP application security guidelines. Several security vulnerability assessment tools and external vendors are used to test and verify compliance. Säkerhetsverktygen omfattar:

- Veracode Static och Dynamic Scanning
- RIPS source code scanning
- Trustwave och Alert Logic’s vulnerability scanning services
- Burp Suite Pro
- OWASPZAP
- andSqlMap

The full code base is scanned with these tools on a bi-weekly basis. Customers are notified of security patches through direct emails, notifications in the application, and in the [Security Center](https://magento.com/security).

Customers must ensure that these patches are applied to their customized application within 30 days of release, according to the PCI guidelines. Adobe har också ett [säkerhetsgenomsökningsverktyg](https://docs.magento.com/user-guide/magento/security-scan.html) som gör det möjligt för handlare att regelbundet övervaka sina webbplatser och få uppdateringar om kända säkerhetsrisker, skadlig kod och obehörig åtkomst. The Security Scan Tool is a free service and can be run on any version of Adobe Commerce.

För att uppmuntra säkerhetsforskare att identifiera och rapportera säkerhetsluckor har Adobe Commerce ett [felbegränsningsprogram](https://hackerone.com/magento) utöver intern testning. Kunden får dessutom den fullständiga källkoden för programmet för egen granskning om så önskas.

## Read-only file system

All the executable code is deployed into a read-only file system image, which dramatically reduces the surfaces that are available for attack. Distributionsprocessen skapar en Squash-FS-avbildning. This approach dramatically reduces opportunities to inject PHP or JavaScript code into the system or modify the Adobe Commerce application files.

## Remote deployment

Det enda sättet att få körbar kod i Managed Services produktionsmiljö är att köra den genom en provisioneringsprocess. Detta innebär att överföra källkod från källdatabasen till en fjärrdatabas som initierar en distributionsprocess. Access to that deployment target is controlled, so you have complete control over who can access the deployment target. All deployments of application code to the non-production environment are controlled by the customer.

## Loggning

All AWS activities are logged in AWS CloudTrail. Linux, application server, and database logs are stored on the production servers and stored in backups. Alla ändringar av källkoden registreras i en Git-databas. Distributionshistorik är tillgänglig i Adobe Commerce [Project Web Interface](https://devdocs.magento.com/cloud/project/projects.html#login). All support access is logged and support sessions are recorded.

## Känsliga data

Känsliga data kan omfatta antingen personuppgifter från konsumenter eller konfidentiella uppgifter från Managed Services-kunder. Skydd av känsliga kunds- och konsumentdata är en viktig skyldighet för Adobe Commerce Managed Services. Både Managed Services och våra kunder har juridiska skyldigheter när det gäller personligt identifierbar information. Förutom arkitekturens säkerhetsfunktioner finns det andra kontroller som begränsar distributionen och åtkomsten till känsliga data.

Kunderna äger sina data och har kontroll över var dessa data kommer att placeras. The customer specifies the location where their production and development instances reside. De anger också vilken plats som ska användas för Magento Business Intelligence-miljön (MBI) i samverkan med Commerce, och om MBI-programmet har tillgång till personligt identifierbar information eller inte. Produktionsinstanser kan finnas i de flesta AWS-regioner, medan utvecklings- och MBI-miljöer för närvarande kan vara både i USA och i EU.

Sensitive data may pass through the Fastly CDN server network but is not stored in the Fastly network. All partners included in the Adobe Commerce Managed Services offering have contractual obligations to ensure the protection of sensitive data. Managed Services flyttar inte känsliga kund- eller konsumentdata från de platser som kunden anger.

Som en del av tillhandahållandet av de tjänster som ingår i Adobe Commerce Managed Services-erbjudandet kräver Managed Services personal tillgång till produktionssystem som innehåller känsliga uppgifter. Dessa medarbetare har utbildats för att skydda känsliga kunddata och konsumentdata. Access to these systems is limited to employees that require access. Dessa anställda har bara tillgång till den tid som behövs för att kunna leverera dessa tjänster.

## Allmänna dataskyddsförordningen (GDPR)

GDPR är en rättslig ram som fastställer riktlinjer för insamling och behandling av personuppgifter för enskilda personer inom EU. Dessa bestämmelser gäller oavsett var webbplatsen är baserad, och EU-besökare har tillgång till den.

I grund och botten måste besökarna informeras om de data som webbplatsen samlar in från dem och uttryckligen godkänna informationsinsamlingen. Webbplatserna måste meddela besökarna om de personuppgifter som finns på webbplatsen bryts.

Den handlare eller det företag som driver webbplatsen måste också ha ett särskilt uppgiftsskyddsombud som ansvarar för webbplatsens datasäkerhet, och denna person (eller webbplatsens ledningsgrupp) ska vara tillgänglig för kontakt om en besökare begär att deras data raderas.

GDPR kräver också att all personligt identifierbar information (t.ex. namn, ras och födelsedatum) som samlas in antingen ska anonymiseras eller pseudonymiseras.

>[!NOTE]
>
> This page is simply meant as a general overview for what to consider for GDPR. For more information, please consult with your legal counsel or refer to the[official text](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Backups

Säkerhetskopieringar utförs varje timme under de senaste 24 timmarna. Efter 24-timmarsperioden sparas säkerhetskopiorna enligt följande schema med tjänsten AWS EBS Snapshot:

| Tidsperiod | Lagringsprincip för säkerhetskopia |
|----------------|-------------------------|
| Dagar 1 till 3 | Each backup |
| Dagar 4 till 6 | En säkerhetskopiering per dag |
| Vecka 2 till 6 | En säkerhetskopia per vecka |
| Vecka 8 till 12 | One biweekly backup |
| Weeks 12 to 22 | One backup per month |

Detta skapar en oberoende säkerhetskopiering av redundant lagring. Eftersom EBS-volymerna är krypterade krypteras även säkerhetskopiorna. Additionally, Managed Services performs on-demand backups on a customer-requested basis.

Your Adobe Commerce Managed Services backup and recovery approach uses a high-availability architecture combined with full-system backups. Varje projekt replikeras - alla data, all kod och alla resurser - i tre separata AWS-tillgänglighetszoner; varje zon med ett separat datacenter.
