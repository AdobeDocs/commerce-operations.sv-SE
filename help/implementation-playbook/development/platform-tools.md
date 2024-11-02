---
title: plattformsverktyg
description: Välj rekommenderade plattformsverktyg för implementeringen av Adobe Commerce.
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
feature: Configuration
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# plattformsverktyg

Det råder ingen brist på aspekter som måste genomsyras väl och noggrant testas för att en e-handelsplats ska fungera utan störningar. Ni måste inte bara identifiera rätt lösningar för att hantera alla delar av webbplatsen - från datalagring och programmering till cachning och säkerhet - utan även rätt process för att säkerställa att ni får en plattform som både fungerar smidigt och kan byggas och optimeras effektivt.

I det här avsnittet beskrivs inte bara verktyg, lösningar, processer och metoder som har testats och optimerats i ett antal Adobe Commerce-implementeringar, utan även våra rekommendationer för vilka lösningar bäst passar specifika affärsbehov och mål.

Följande tabell innehåller lösningar som vi rekommenderar och kan användas i Adobe Commerce för att öka prestanda på plattformen:

| Syfte | Verktyg |
|------------------------------------------|-------------------------|
| Databas | MySQL, MariaDB, Percona |
| Programmering | PHP, JS, HTML, LESS CSS |
| Integrerad utvecklingsmiljö | Eclipse, PHPStorm |
| Webbserver | Nginx, Apache |
| Cachelagringstjänster | Redis, lack |
| Söktjänster | Elasticsearch |
| Meddelandekötjänster | [!DNL RabbitMQ] |
| Verktyget för säkerhetsgenomsökning | SonarQube, ZAP |

## Databas

Det finns tre olika verktyg som vi använder beroende på varumärkets behov. MySQL är en bra baslinjelösning som Adobe Commerce-databasen om du inte förväntar dig att din butik ska hantera extrema belastningar.

MariaDB är mer användarfokuserad och fungerar bättre för användare som bryr sig mer om funktioner än rena prestanda. MariaDB har stöd för ett stort antal databasmotorer, diskkryptering, komplexa horisontella anslutningsmöjligheter och skalningsfunktioner, vilket kan vara intressant för stora Adobe Commerce-butiker.

Percona är en gaffel i MySQL som centrerar sig kring prestanda och hantering av toppbelastning. Välj MariaDB om du behöver mer livskvalitet och DevOps-funktioner. Gå till Percona om du vill få höga prestanda i storskaliga datauppsättningar.

## Programmering

Adobe Commerce är ett PHP-baserat program och de senaste versionerna är alltid kompatibla med den senaste stabila PHP-versionen (Adobe Commerce version 2.4 rekommenderar till exempel att du använder PHP 7.4). För att få högre säkerhet och prestanda finns det flera faktorer att ta hänsyn till när PHP konfigureras för att få maximal hastighet och effektivitet vid behandling av begäranden. Adobe Commerce webbutik byggs med HTML, JavaScript och LESS CSS-preprocessorn.

## Webbservrar

Adobe Commerce har fullt stöd för webbservrarna Nginx och Apache. Adobe Commerce innehåller exempelfiler med rekommenderad konfiguration för båda:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

Nginx-exemplet innehåller inställningar för bättre prestanda och är utformat så att liten omkonfiguration krävs.

## Cachelagringstjänster

Adobe Commerce har flera alternativ för att lagra cacheminne och sessionsdata, bland annat Redis, Memcache, filsystem och databas. Redis är det bästa alternativet för en konfiguration med flera webbnoder.

Vi rekommenderar att du använder Varnish som helsidesserver för din butik. Adobe Commerce distribuerar en exempelkonfigurationsfil för lack som innehåller alla rekommenderade inställningar för prestanda.

## Söktjänster

För Adobe Commerce version 2.4 och senare måste alla installationer vara konfigurerade att använda Elasticsearch eller OpenSearch som katalogsökningslösning. Elasticsearch erbjuder snabba och avancerade sökningar på produkter i katalogen. Elasticsearch är valfritt för versioner före 2.4, men rekommenderas.

## Meddelandekötjänster

Meddelandeköer är en asynkron kommunikationsmekanism där avsändaren och mottagaren av ett meddelande inte kontaktar varandra. [!DNL RabbitMQ] är en meddelandeansvarig med öppen källkod som erbjuder ett tillförlitligt, skalbart och portabelt meddelandesystem med hög tillgänglighet.

## Säkerhetsverktyg

Med [Adobe Commerce Security Scan Tool](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) kan du regelbundet övervaka dina butikswebbplatser och få uppdateringar för kända säkerhetsrisker, skadlig kod och inaktuell programvara. Vanligtvis börjar du använda det här verktyget när du börjar testa användargodkännande (UAT). Förutom verktyget Adobe Commerce Security Scan, som är kostnadsfritt och tillgängligt för alla implementeringar och versioner av Adobe Commerce, finns det andra alternativ som kan användas under CI/CD-processen och före varje release.

SonarQube är en plattform för kvalitetshantering med öppen källkod som är utformad för att analysera och mäta kodens tekniska kvalitet. SonarQube ger inte bara en fullständig rapport över kodfel, syntaxfel och sårbarheter, utan också förslag och exempel på hur du kan åtgärda koden. SonarQube är perfekt att använda i en CI/CD-miljö som ett verktyg som kan analysera koden innan den distribueras.

Zed Attack Proxy (ZAP) är ett kostnadsfritt säkerhetstestverktyg som används av tusentals testare runt om i världen. ZAP har utvecklats av OWASP och är ett av de verktyg som rekommenderas för manuell säkerhetstestning.
