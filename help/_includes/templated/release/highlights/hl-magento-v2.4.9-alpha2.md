---
source-git-commit: 5b0229d73dc7b8ad53750102e99447bb15baa84d
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---
# Versionsinformation för Magento Open Source (v2.4.9-alpha2)

## Högdagrar i v2.4.9-alpha2

Följande högdagrar gäller för Magento Open Source version 2.4.9-alpha2.

### Ramverk

#### Lägg till stöd för OpenSearch 3

Adobe Commerce 2.4.9 är nu helt kompatibelt med OpenSearch 3.x. Med den här uppdateringen kan handlare dra nytta av förbättrade prestanda, bättre säkerhet och långsiktig support samtidigt som bakåtkompatibiliteten med OpenSearch 2.x bibehålls.

_AC-11846_

#### Uppdatera Nginx-version från 1.26 till 1.28

Nginx-versionen som används i utvecklings- och testmiljöer i alla Adobe Commerce-versioner som stöds för närvarande uppdateras från 1,26 till 1,28, i linje med den senaste stabila Nginx-versionen som finns tillgänglig.
Testning på PR-nivå körs nu mot Nginx 1.28 som bekräftar fullständig kompatibilitet och stöd för alla Adobe Commerce-versioner.

_AC-14104_

#### Undersök den senaste versionen jquery-validate

Uppgraderade jQuery Validate-biblioteket till version 1.21.0 för att förbättra formulärvalideringsfunktionerna, förbättra användarupplevelsen och säkerställa att alla Adobe Commerce-formulär är kompatibla i både admin- och klientgränssnitt.

_AC-14403 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/98b2848a)_

#### Undersök den senaste versionen jquery-ui

Uppgraderade jQuery-gränssnittsbiblioteket till version 1.14.1 för att förbättra användargränssnittets widgetar, förbättra tillgängligheten och säkerställa modern webbläsarkompatibilitet för alla komponenter i Adobe Commerce admin- och klientgränssnitt.

_AC-14417 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/77c589a6)_

#### Undersök den senaste versionen mindre.js

Uppgraderade CSS-preprocessorn Less.js till version 4.2.2 för att förbättra CSS-kompileringsprestanda, förbättra syntaxstödet och modernisera temabygeringsprocessen för alla Adobe Commerce-frontend- och -administratörsteman.

_AC-14418 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/98b2848a)_

#### Undersök den senaste versionen av minute-timezone-with-data.js

Uppgraderade tidszonsbiblioteket för stund till version 0.5.43 för att förbättra tidszonshanteringen, uppdatera tidszonsdata med de senaste IANA-ändringarna av tidszonsdatabasen och förbättra datum- och tidsbearbetningsnoggrannheten för alla Adobe Commerce-åtgärder både internationellt och i flera tidszoner.

_AC-14419 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/98b2848a)_

#### Undersök den senaste versionen under score.js

Uppgraderade underscore.js-verktygsbiblioteket till version 1.13.7 för att förbättra JavaScript funktionalitet, förbättra datamanipuleringsprestanda och säkerställa modern webbläsarkompatibilitet över alla delar av Adobe Commerce klientdel och admin-gränssnitt.

_AC-14420 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/98b2848a)_

#### Migrera från TinyMCE till Hugerte.org

På grund av att stödet för TinyMCE 5 och 6 har upphört och att licensinkompatibiliteten med TinyMCE 7 har upphört migreras den nuvarande implementeringen av Adobe Commerce WYSIWYG-redigeraren från TinyMCE till den öppna HugeRTE-redigeraren (https://hugerte.org/).
Tack vare den här migreringen är Adobe Commerce fortfarande kompatibelt med öppen källkodslicensiering, undviker kända TinyMCE 6-problem och levererar en modern redigeringsupplevelse som stöds av både handlare och utvecklare.

_AC-14568_

#### Lägg till fullständigt stöd för 8.x-tangenten för 2.4.9-alpha2

Adobe Commerce 2.4.9 har fullt stöd för CLI-kommandon för Valkey, vilket motsvarar de befintliga Redis-funktionerna. Admin- och molnkonfigurationen har uppdaterats för att tillåta sömlös Valkey-konfiguration.
Denna uppdatering garanterar att Adobe Commerce förblir framtidssäkert och prestandasäkert genom stöd för Valkey 8.x, vilket ger handlare och utvecklare ett tillförlitligt alternativ till Redis när det närmar sig slutet av livscykeln.

_AC-14604_

### Övriga

#### Uppdatera tjänsten AWS Valkey 8.x för CNS Build and Test

Uppdatera tjänsten AWS Valkey 8.x för CNS Build

_AC-14470_

#### 2.4.9-alpha2 - Förbättringar av grundkvalitet i augusti

_AC-14700_

### Säkerhet

#### Säkerhetsförbättringar för 2.4.9-alfa2

_AC-14610_

### Leverans

#### Migrera USPS-integrering från gamla webbverktyg-API:er till nya RESTful USPS API:er

För att uppfylla USPS-annonser om att äldre API:er för webbverktyg har upphört att gälla den 25 januari 2026 migreras Adobe Commerce USPS-integreringen till de nya RESTful USPS API:erna.

Viktiga förbättringar:

* Stöd för dubbla API:er: Administratörsanvändare kan nu välja mellan det äldre API:t för webbverktyg och det nya RESTful USPS API:t via konfigurationsinställningar.
* Autentiseringsuppgradering: Implementerad OAuth 2.0 för säker API-åtkomst.
* Förbättrat dataformat: Gå över från XML till JSON för tydligare och effektivare kommunikation.
* Nya administratörsfält:
   * URL för gateway REST (baserat på läge: Utveckling eller Live)
   * Klient-ID och hemlighet
   * Kontotyp, kontonummer
   * CRID, MID, Mailer Identification Code
   * AES/ITN för internationella transporter
   * REST-specifika tillåtna leveransmetoder

Denna migrering säkerställer att Adobe Commerce följer USPS-standarderna, förbättrar systemets tillförlitlighet och framtida korrekturleveranser för handlare.

_AC-13257_
