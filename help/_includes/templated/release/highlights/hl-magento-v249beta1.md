---
source-git-commit: 65a9bd667d434f1deae69798696f66998e6024a0
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 0%

---
# Magento Open Source highlights (v2.4.9-beta1)

## Högdagrar i v2.4.9-beta1

Följande markeringar gäller för Magento Open Source 2.4.9-beta1.

### API:er

#### Lägg till en möjlighet att behålla arv av produktgalleriet i REST API när en produkt uppdateras i butiksvyn

Uppdatering av produkt via REST API i ett butiksomfång medför inte längre att produktbilder och videor ärver ändringar från det globala omfånget om media_gallery_entries utelämnas från nyttolasten eller anges till NULL för att förhindra ändringar i produktgalleriet i det omfånget. Dessutom är det nu möjligt att återställa omfångsarv för produktbilder och video via REST API genom att ange motsvarande fält som NULL

_ACP2E-4358 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Ramverk

#### Undersök den senaste större versionen av web-token/jwt-framework

Som en del av den kontinuerliga säkerhetsgranskningen utvärderade vi den senaste större releasen av det gemensamma teknikramverket för att säkerställa framtida kompatibilitet och upprätthålla starka säkerhetsstandarder. Den här versionen har ingen effekt på befintliga funktioner.

_AC-13209 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/2bac8114) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/33b81f28)_

#### Ersätt carlos-mg89/oauth med inbyggda PHP-funktioner

Ersatte Carlos-mg89/oauth-biblioteket från tredje part med inbyggda PHP OAuth-funktioner för att förbättra säkerheten, minska externa beroenden och förbättra plattformens stabilitet.

_AC-14075 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/7b8064f7)_

#### Undersök den senaste versionen av chart.js

Uppgraderade diagrambiblioteket Chart.js JavaScript till den senaste versionen, 4.4.8, för att förbättra diagramåtergivningsprestanda, förbättra visuella funktioner och åtgärda säkerhetsluckor i adminkontrollpanelen och rapportmodulerna.

_AC-14304 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/768b4442)_

#### Undersök senaste version jquery/uppy och uppy

Uppgraderade Uppy-biblioteket för filöverföring till version 4.13.4 för att förbättra filöverföringsmöjligheterna, förbättra användarupplevelsen och åtgärda säkerhetsluckor vid filhantering i Adobe Commerce administratörsgränssnitt och klientkomponenter.

_AC-14307 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/eb491c05)_

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

#### Uppdatera allure-framework/allure-phpunit version till 3 och ta bort ursprungligt beroende i 2.4.9-alpha1

I Adobe Commerce 2.4.9 har beroendet av allure-framework/allure-phpunit uppgraderats till huvudversion 3, som har stöd för PHP 8.4, PHP 8.5 och moderniserar vår Allure-baserade testrapporteringsstack. Det systemspecifika beroendet som tidigare krävdes för äldre versioner av Allure PHPUnit har tagits bort där det är tillämpligt, vilket förenklar installation och underhåll.

_AC-14548 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/87b8b34e)_

#### Uppgradera chart.js-beroendet till den senaste versionen

Diagram.js-beroendet uppgraderas till den senaste versionen, 4.5.0

_AC-15133 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/657f983e)_

#### Lägg till officiellt stöd för Symfony 7.4 LTS och PHP 8.5 i Adobe Commerce 2.4.9

Som en del av Adobe Commerce 2.4.9-plattformsuppdateringen har alla Symfony-beroenden som används av magento/composer-paketet uppdaterats till de senaste Symfony LTS 7.4-versionerna. Detta anpassar Commerce Composer-verktyg efter den aktuella Symfony LTS-raden och tar bort tidigare beroendebegränsningar som gäller äldre Symfony-versioner. Dessutom har alla anpassade klasser som utökar Symfony-huvudklasser uppdaterat typdeklarationer och metodsignaturer i enlighet med de senaste Symfonkraven innan de uppgraderar till Adobe Commerce 2.4.9. Detta förhindrar kompatibilitetsproblem och säkerställer en smidig övergång till de uppdaterade ramverkskomponenterna.

_AC-15170 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/c127d10b)_

### Övriga

#### Captcha / reCaptha fungerar inte för API / GraphQl

När CAPTCHA (eller reCAPTCHA) är aktiverat för formuläret Skapa konto i Adobe Commerce 2.4.9, används nu samma CAPTCHA-validering för att skapa kundkonton via API:erna REST och GraphQL.

_AC-16245 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/fd7f30ee)_

### Säkerhet

#### Förbättra prestanda för asynkrona/gruppvisa begäranden

Åtgärda prestandaförsämringen i asynkrona webbslutpunkter som introducerats efter säkerhetspatchen APSB25-08, vilket resulterar i fler körningstider.

_AC-14078 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/9a7352b7)_

#### Endast en aktiverad 2FA-provider måste konfigureras per användare

Administratörsanvändare behöver nu bara konfigurera en av handlarens aktiverade 2FA-leverantörer (till exempel Google Authenticator eller U2F) för att få åtkomst till administrationspanelen. Ytterligare aktiverade providers kan konfigureras senare efter behov. När flera 2FA-providers var aktiverade (t.ex. Google Authenticator och U2F) var alla administratörsanvändare tvungna att konfigurera alla aktiverade leverantörer innan de kunde logga in. Detta skapade en funktion för användare som inte hade tillgång till alla faktorer (till exempel en maskinvarunyckel för U2F).

_AC-8253 - [GitHub-kodbidrag](https://github.com/magento/security-package/commit/71e7936b)_

### Mellanlagring och förhandsvisning

#### [Funktionsförfrågan] Förhandsvisning av innehållstagning i mobilvyn

Med funktionen för förhandsgranskning av mellanlagring på adminpanelen kan webbläsarsimulerade förhandsvisningar av mobila enheter återges korrekt, vilket ger en visuell representation av hur mellanlagringsuppdateringen kommer att visas på en mobil enhet.

_ACP2E-3397 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/520f9e30)_
