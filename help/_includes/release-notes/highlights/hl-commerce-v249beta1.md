---
source-git-commit: adda02b9d05b66ab066f110e877584bc1c77515d
workflow-type: tm+mt
source-wordcount: '2408'
ht-degree: 0%

---
# Adobe Commerce highlights (v2.4.9-beta1)

## Högdagrar i v2.4.9-beta1

Följande markeringar gäller för Adobe Commerce 2.4.9-beta1.

### API:er

#### REST API-produktgalleriarvskontroll på butiksvynivå

Uppdatering av en produkt via REST API i ett butiksomfång medför inte längre att produktbilder och videoklipp ärver ändringar från det globala omfånget när `media_gallery_entries` utelämnas från nyttolasten eller anges till `NULL`. Nu är det också möjligt att återställa omfångsarv för produktbilder och videofilmer via REST API genom att ställa in motsvarande fält på `NULL`.

_ACP2E-4358 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Administratörsgränssnitt

#### Menyn Åtgärder för rastret för katalogprisregler

Rutnätet för katalogprisregler i Commerce Admin innehåller nu en Åtgärder-meny, som gör att handlare kan aktivera, inaktivera eller ta bort flera katalogprisregler samtidigt. Detta medför att hantering av katalogprisregler överensstämmer med befintliga massåtgärder för kundprisregler, vilket avsevärt minskar tiden som krävs för att hantera stora regeluppsättningar.

_AC-13916_

#### Förhandsgranskning i mobilvyn för innehållstagning

Med funktionen för förhandsgranskning av mellanlagring i Admin kan nu webbläsarsimulerade förhandsvisningar av mobila enheter återges korrekt, vilket ger en visuell representation av hur en mellanlagringsuppdatering kommer att visas på en mobil enhet.

_ACP2E-3397 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_

### Braintree

#### Express-utcheckning

- **Kampanjerbjudanden i Google Pay Express Paysheet**

  Google Pay Express Pay Sheet har nu stöd för erbjudandekoder. Köpare kan ansöka om, visa och ta bort kundvagnsreklam direkt i Google Pay Sheet, vilket säkerställer att man får samma rabatter och incitament som vid vanlig utcheckning.

  _BUNDLE-3476_

- **Kampanjerbjudanden i Apple Pay Express Paysheet**

  Apple Pay Express Pay Sheet har nu stöd för erbjudandekoder. Köpare kan lägga på en kupong direkt i Apple Pay Sheet, så att man kan dra nytta av samma rabatter och kampanjer som i kassan.

  _BUNDLE-3477_

- **Apple Betala på Chrome och Firefox**

  Apple Pay kan nu användas i Chrome och Firefox, inte bara i Safari. När Apple Pay Express är aktiverat är Apple Pay-knappar tillgängliga för alla butiksplatser som stöds, och kunderna betalar genom att skanna en kod med sin iPhone.

  _BUNDLE-3478_

- **Återanrop för serverleverans för PayPal Express**

  Återanropet för PayPal Express-leverans har flyttats från klientsidan till serversidan. Detta ger dynamiska leveransmetoder, kostnadsberäkningar i realtid och korrekt kundvagnsinformation direkt i PayPal modal, förbättrad tillförlitlighet och utgör grunden för framtida funktioner som stöd för kontaktmodul, app-switch-flöden och Venmo Express.

  _BUNDLE-3479_

- **PayPal-kontaktmodul för Express-utcheckning av handlare i USA**

  En ny PayPal Contact Module introduceras för handlare i USA. När det här alternativet är aktiverat kan köpare som använder PayPal Express visa och uppdatera den e-postadress och det telefonnummer som delas med handlaren direkt i PayPal-modal under expressflöden (PDP, mini-cart, cart, checkout express). Den valda kontaktinformationen lagras sedan på Commerce-beställningen.

  _BUNDLE-3480_

#### Betalningsmetoder

- **Stöd för typ av ELO-kort för Braintree-betalningar**

  Stöd för typen av ELO-kort har lagts till i Braintree Payments. Administratörer kan nu aktivera ELO i kreditkortskonfigurationen och kunderna kan beställa via ELO-kort i kassan, vilket ger smidiga transaktioner via Braintree.

  _BUNDLE-3464_

- **BLIK lokal betalningsmetod för polska kunder**

  BLIK har lagts till som en ny lokal betalningsmetod för polska kunder. På så sätt kan man få säkra, bankbaserade BLIK-betalningar inom det befintliga Braintree LPM-flödet (Local Payment Methods), vilket underlättar utcheckningen och underlättar konverteringen för kunder i Polen.

  _BUNDLE-3481_

- **Betala på faktura - ny BNPL-betalningsmetod för Tyskland**

  Lagt till en ny lokal betalningsmetod, Betala på faktura för tyska köpare. Pay On Invoice är ett Buy Now, Pay Later (BNPL)-alternativ som drivs av PayPal och Ratepay (&quot;Rechnungskauf mit Ratepay&quot;) som gör att kunderna kan ta emot varor först och betala fakturan inom 30 dagar, utan att behöva ett PayPal-konto. Eftersom det inte är en direktbetalning drivs orderfärdigställandet av en webkrok på serversidan från PayPal.

  _BUNDLE-3475_

#### Kortsäkring

- **Utvärderar Google Betala via kontoområdet**

  Nu kan kunderna vault sina Google Pay-kort via kontoområdet när Google Pay Vault är aktiverat i Braintree. Vaultade kort visas under lagrade betalningsmetoder, kan användas för framtida inköp vid utcheckning och kan tas bort av kunden. Detta ger bättre stöd än Cards och PayPal till Google Pay.

  _BUNDLE-3459_

- **Kontouppdateraren i realtid (RTAU) för Braintree-kort i vaulted**

  Funktionen Real-Time Account Updater (RTAU) som lagts till i Braintree säkerställer att kortuppgifterna för Visa, Mastercard och Discover uppdateras automatiskt när korten går ut eller ersätts. Detta minimerar misslyckade betalningar, håller Commerce Vault aktuellt och hoppar över typer som inte stöds (förbetald, Apple Pay, Google Pay) utan fel.

  _BUNDLE-3462_

#### Administratörsverktyg

- **Länka Commerce-beställning till Braintree-portalen**

  Nu har en Braintree Portal-länk lagts till i orderinformationen i Commerce Admin. När du klickar på länken öppnas den relaterade transaktionen i Braintree Portal (på en ny flik) med hjälp av handels-ID och transaktions-ID från Commerce-ordern. Detta möjliggör direkt korsreferens utan att logga in i båda systemen separat.

  _BUNDLE-3461_

#### Säkerhet och kompatibilitet

- **Uppdatering av innehållets säkerhetsprincip för kardinell integration för 3D-säkerhet**

  CSP (Content Security Policy) har uppdaterats för att stödja de senaste integrationskraven för kardinal (3D Secure). Detta garanterar att alla kardinalbaserade skript, iframes och relaterade resurser som används under 3D-säkra flöden tillåts av webbläsarens CSP, vilket förhindrar blockerade förfrågningar och trasiga utmaningar eller verifieringsupplevelser.

  _BUNDLE-3485_

- **Kompatibilitet med Braintree-betalningstillägg PHP 8.5**

  Braintree betalningstillägg har uppdaterats för att stödja PHP 8.5-miljön, samtidigt som kompatibiliteten med PHP 8.4 bibehålls.

  _BUNDLE-3493_

### Plattform och infrastruktur

#### Stöd för OpenSearch 3.x

Adobe Commerce 2.4.9-beta1 är helt kompatibelt med OpenSearch 3.x. Med den här uppdateringen kan handlare dra nytta av förbättrade prestanda, bättre säkerhet och långsiktig support samtidigt som bakåtkompatibiliteten med OpenSearch 2.x bibehålls.

_AC-11846_

#### Fullt stöd för Valkey 8.x

Adobe Commerce 2.4.9-beta1 har omfattande stöd för Valkey 8.x som Redis-kompatibel cache-server, inklusive fullständig CLI-kommandoparitet med Redis. Konfigurationsalternativen för Admin och Cloud har uppdaterats för sömlös Valkey-konfiguration. Detta stöds av Redis 7.2, som ger säljarna ett tillförlitligt och fullt stöd alternativ till Redis i Commerce-versionerna 2.4.5 till 2.4.9-beta1.

_AC-14103, AC-14604_

#### Stöd för Apache ActiveMQ Artemis ersätter RabbitMQ

Stöd för Apache ActiveMQ Artemis har lagts till som ett strategiskt alternativ till RabbitMQ, som drivs av supportrisker i samband med RabbitMQ 4. ActiveMQ Artemis stöds nu fullt ut på Commerce-versionerna 2.4.6 till 2.4.9-beta1, inklusive Adobe Commerce Cloud med AWS ActiveMQ för molnbaserade distributioner, och har stöd för STOMP-konfiguration för kökonsumenter och utgivare. Befintliga installationer av RabbitMQ 4 är fortfarande kompatibla för handlare som föredrar att fortsätta använda sin meddelandekötjänst.

_AC-14558_

### PHP och Composer

#### Kompatibilitet med PHP 8.5

Från och med Adobe Commerce 2.4.9-beta1 är plattformen helt kompatibel med PHP 8.5, samtidigt som stödet för PHP 8.4 bibehålls och PHP 8.3 tillåts endast för uppgraderingsscenarier. Detta arbete moderniserar kärnkod, beroenden och verktyg så att handlarna säkert kan gå över till nyare PHP-versioner framför stödet för PHP 8.4, vilket upprätthåller PCI-kompatibiliteten och långsiktig plattformshälsa.

_AC-15615_

#### Stöd för PHP 8.2 har tagits bort

Från och med Adobe Commerce 2.4.9-beta1 stöds inte längre PHP 8.2. Plattformen har nu PHP 8.3 och senare som mål, med kärnkod, beroenden och verktyg uppdaterade så att de kan köras på ett korrekt och tillförlitligt sätt i PHP 8.4 och 8.5.

_AC-15758_

#### Kompatibiliteten för Composer 2.9 har verifierats

Adobe Commerce 2.4.9-beta1 är helt kompatibelt med Composer 2.x, inklusive Composer 2.9. Justeringen bevarar bakåtkompatibiliteten och ger en stabil bygg- och driftsättningsupplevelse för handlare och utvecklare med de senaste Composer-versionerna.

_AC-14481_

### Ramverk

#### Uppdatering av säkerhet och kompatibilitet för JWT-ramverk

Som en del av den kontinuerliga säkerhetsgranskningen av plattformen har JWT-ramverkets webb-token-beroende utvärderats och uppdaterats till den senaste större versionen, vilket garanterar framtida kompatibilitet och höga säkerhetsstandarder för tokenbaserad autentisering i Commerce-integrationer. Befintliga funktioner bevaras helt.

_AC-13209 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2bac8114) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/33b81f28)_

#### Adobe Commerce Functional Testing Framework uppdaterat till Symfony LTS-beroenden

Adobe Commerce Functional Testing Framework (MFTF) har uppdaterats för att använda de senaste Symfony LTS-beroendena, inklusive symfony/config, vilket krävs för uppgraderingen av web-token/jwt-framework. Detta löser tidigare beroendekonflikter och säkerställer en stabil stack som stöds för funktionstestning.

_AC-13244_

#### Inbyggda PHP OAuth-funktioner ersätter tredjepartsbibliotek

Tredjepartsbiblioteket `carlos-mg89/oauth` har ersatts med inbyggda PHP OAuth-funktioner, vilket förbättrar säkerheten, minskar externa beroenden och förbättrar plattformsstabiliteten.

_AC-14075 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7b8064f7)_

#### Komponenten Symfoni Cache ersätter Zend_Cache

Från och med Adobe Commerce 2.4.9-beta1 har den inaktuella Zend_Cache-komponenten ersatts av Symfony Cache-komponenten. Uppdateringen förbättrar cacheprestanda och -underhåll och garanterar långsiktig kompatibilitet med PHP 8.x och framtida plattformsuppdateringar. Befintliga cacheminnesbackendar och cachehanteringskommandon stöds fortfarande fullt ut, utan några ändringar som krävs för aktuella integreringar.

_AC-15823_

#### WYSIWYG editor har migrerats från TinyMCE till HugeRTE

På grund av att stödet för TinyMCE 5 och 6 har upphört och att licensieringen inte är kompatibel med TinyMCE 7 har Adobe Commerce WYSIWYG-redigeraren migrerats till den öppna [HugeRTE](https://hugerte.org/) -redigeraren. Tack vare den här migreringen är Adobe Commerce fortfarande kompatibelt med öppen källkodslicensiering, undviker kända TinyMCE 6-problem och levererar en modern redigeringsupplevelse som stöds av både handlare och utvecklare.

_AC-14568_

#### Inbyggd MVC-implementering ersätter Laminas MVC

Adobe Commerce har infört en intern MVC-implementering som ersätter den gamla Laminas MVC för att säkerställa långsiktig kompatibilitet och stabilitet utöver PHP 8.5. Den här förändringen förbättrar prestanda, minskar externa beroenden och ger en mer framtidsklar grund för Commerce.

_AC-15160_

#### Officiellt stöd för Symfony 7.4 LTS

Som en del av Adobe Commerce 2.4.9-beta1-plattformsuppdateringen har alla Symfony-beroenden uppdaterats till de senaste Symfony LTS 7.4-versionerna. Alla anpassade klasser som utökar Symfony-huvudklasser har uppdaterade typdeklarationer och metodsignaturer som är anpassade till de senaste Symfonkraven, vilket förhindrar kompatibilitetsproblem och ger en smidig övergång till de uppdaterade ramverkskomponenterna.

_AC-15170 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c127d10b)_

#### Allokerat PHPUnit-beroende uppgraderat till version 3

`allure-framework/allure-phpunit`-beroendet har uppgraderats till huvudversion 3, som lägger till stöd för PHP 8.4 och PHP 8.5 och moderniserar den Allure-baserade testrapporteringsstacken. Det systemspecifika beroendet som tidigare krävdes för äldre versioner av Allure PHPUnit har tagits bort, vilket förenklar installation och underhåll.

_AC-14548 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/87b8b34e)_

#### New Relic-rapportering har uppdaterats till NerdGraph API

New Relic rapporteringsmodul har uppdaterats för att stödja New Relic NerdGraph (GraphQL) API för ändringsspårning samtidigt som den befintliga integreringen med REST v2-distributionsmarkörer bevaras. Ändringen ger mer omfattande metadata för driftsättning, regionalt stöd för slutpunkter (USA och EU) och konfigureringsmöjligheter via administratörsinställningarna utan att befintliga inställningar bryts.

_AC-15461_

#### JavaScript biblioteksuppdateringar

- **Chart.js har uppdaterats till version 4.5.0**

  Uppgraderade diagrambiblioteket Chart.js JavaScript till version 4.5.0 för att förbättra diagramåtergivningsprestanda, förbättra de visuella funktionerna och åtgärda säkerhetsluckor i adminkontrollpanelen och rapportmodulerna.

  _AC-14304, AC-15133 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/768b4442), [GitHub-kodbidrag](https://github.com/magento/magento2/commit/657f983e)_

- **Upphöjt filöverföringsbibliotek uppdaterat till version 4.13.4**

  Uppgraderade Uppy-biblioteket för filöverföring till version 4.13.4 för att förbättra filöverföringsmöjligheterna, förbättra användarupplevelsen och åtgärda säkerhetsluckor vid filhantering i Adobe Commerce administratörsgränssnitt och klientkomponenter.

  _AC-14307 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/eb491c05)_

- **jQuery Validate-bibliotek uppgraderat till version 1.21.0**

  Uppgraderade jQuery Validate-biblioteket till version 1.21.0 för att förbättra formulärvalideringsfunktionerna, förbättra användarupplevelsen och säkerställa att alla Adobe Commerce-formulär är kompatibla i både admin- och klientgränssnitt.

  _AC-14403 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/98b2848a)_

- **jQuery-gränssnittsbibliotek uppgraderat till version 1.14.1**

  Uppgraderade jQuery-gränssnittsbiblioteket till version 1.14.1 för att förbättra användargränssnittets widgetar, förbättra tillgängligheten och säkerställa modern webbläsarkompatibilitet för alla komponenter i Adobe Commerce admin- och klientgränssnitt.

  _AC-14417 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/77c589a6)_

- **CSS-preprocessorn Less.js har uppgraderats till version 4.2.2**

  Uppgraderade CSS-preprocessorn Less.js till version 4.2.2 för att förbättra CSS-kompileringsprestanda, förbättra syntaxstödet och modernisera temabygeringsprocessen för alla Adobe Commerce-frontend- och -administratörsteman.

  _AC-14418 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/98b2848a)_

- **Tidszonsbiblioteket uppgraderas till version 0.5.43**

  Uppgraderade tidszonsbiblioteket (`moment-timezone-with-data.js`) till version 0.5.43 för att förbättra tidszonshanteringen, uppdatera tidszonsdata med de senaste IANA-ändringarna av tidszonsdatabasen och förbättra datum- och tidsbearbetningsnoggrannheten för alla Adobe Commerce-åtgärder, både internationellt och i flera tidszoner.

  _AC-14419 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/98b2848a)_

- **Verktygsbiblioteket Underscore.js har uppgraderats till version 1.13.7**

  Uppgraderade underscore.js-verktygsbiblioteket till version 1.13.7 för att förbättra JavaScript funktionalitet, förbättra datamanipuleringsprestanda och säkerställa modern webbläsarkompatibilitet över alla delar av Adobe Commerce klientdel och admin-gränssnitt.

  _AC-14420 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/98b2848a)_

### Säkerhet

#### CAPTCHA-validering används nu för REST- och GraphQL-API:er

När CAPTCHA (eller reCAPTCHA) är aktiverat för formuläret Create Account, används nu samma CAPTCHA-validering för att skapa kundkonton via REST- och GraphQL-API:er.

_AC-16245_

#### Förbättrade prestanda för asynkron/bulkbegäran

Den här korrigeringen åtgärdar prestandaförsämring i asynkrona webb-API-slutpunkter som introducerats efter APSB25-08-säkerhetskorrigeringen, vilket återställer förväntade körningstider.

_AC-14078 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9a7352b7)_

#### Förenklad tvåfaktorsautentiseringskonfiguration

Administratörsanvändare behöver nu bara konfigurera en av handlarens aktiverade 2FA-leverantörer (till exempel Google Authenticator eller U2F) för att få åtkomst till administrationspanelen. Ytterligare aktiverade providers kan konfigureras senare efter behov. När flera 2FA-providers var aktiverade tidigare krävdes det att alla Admin-användare konfigurerade alla aktiverade leverantörer innan de kunde logga in, vilket skapade en funktion för användare som inte hade tillgång till alla faktorer.

_AC-8253 - [GitHub-kodbidrag](https://github.com/magento-commerce/security-package/commit/41e5a26bd36528cb6b1bdc27b249696a2c721779)_

### Leverans

#### Migrera USPS-integrering till RESTful USPS API:er

För att uppfylla USPS aviserade tillbakadragande av tidigare API:er för webbverktyg har Adobe Commerce migrerat sin USPS-integrering till de nya RESTful USPS API:erna.

Viktiga förbättringar:

- Stöd för dubbla API:er: Administratörsanvändare kan nu välja mellan det äldre API:t för webbverktyg och det nya RESTful USPS API:t via konfigurationsinställningar.
- Autentiseringsuppgradering: Använder OAuth 2.0 för säker API-åtkomst.
- Förbättrat dataformat: JSON används i stället för XML för tydligare och effektivare kommunikation.
- Nya administratörsfält:
   - URL för gateway REST (baserat på läge: Utveckling eller Live)
   - Klient-ID och hemlighet
   - Kontotyp, kontonummer
   - CRID, MID, Mailer Identification Code
   - AES/ITN för internationella transporter
   - REST-specifika tillåtna leveransmetoder

Denna migrering säkerställer att Adobe Commerce följer USPS-standarderna, förbättrar systemets tillförlitlighet och framtida korrekturleveranser för handlare.

_AC-13257_

#### Migrera DHL-integrering till MyDHL RESTful API:er

Den inbyggda DHL-leveransintegreringen har nu stöd för MyDHL RESTful-API:er, samtidigt som kompatibiliteten med det gamla DHL Express XML-API:t bibehålls. Merchants kan välja vilket DHL-API som ska användas i Admin och dra nytta av moderna REST-funktioner utan att bryta befintliga XML-baserade inställningar.

_AC-13258_
