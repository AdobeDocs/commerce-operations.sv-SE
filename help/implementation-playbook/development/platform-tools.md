---
title: Platform Tools
description: Choose recommended platform tools for your Adobe Commerce implementation.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# Plattformsverktyg

Det råder ingen brist på aspekter som måste genomsyras väl och noggrant testas för att en e-handelsplats ska fungera utan störningar. Ni måste inte bara identifiera rätt lösningar för att hantera alla delar av webbplatsen - från datalagring och programmering till cachning och säkerhet - utan även rätt process för att säkerställa att ni får en plattform som både fungerar smidigt och kan byggas och optimeras effektivt.

This section offers not only a look at the tools, solutions, processes, and methodologies that have been tested and perfected over a number of Adobe Commerce implementations, but also our recommendations for which solutions best fit specific business needs and objectives.

The following table includes solutions that we recommend and can be used within Adobe Commerce to drive performance on the platform:

| Syfte | Verktyg |
|------------------------------------------|-------------------------|
| Database | MySQL, MariaDB, Percona |
| Programmeringsspråk | PHP, JS, HTML, LESS CSS |
| Integrerad utvecklingsmiljö (IDE) | Eclipse, PHPStorm |
| Webbserver | Nginx, Apache |
| Cachelagring | Redis, Varnish |
| Söktjänster | Elasticsearch |
| Meddelandekötjänster | KaninMQ |
| Verktyget för säkerhetsgenomsökning | SonarQube, ZAP |

## Datbase

Det finns tre olika verktyg som vi använder beroende på varumärkets behov. MySQL är en bra baslinjelösning som ligger i Adobe Commerce-databasen om du inte förväntar dig att din butik ska hantera extrema laster.

MariaDB is more community-focused and works better for users who care more about features than pure performance. MariaDB supports a large array of database engines, disk encryption, complex horizontal interconnectivity, and scaling features, which could be interesting for large Adobe Commerce stores.

Percona är en gaffel i MySQL som centrerar sig kring prestanda och hantering av toppbelastning. Välj MariaDB om du behöver mer livskvalitet och DevOps-funktioner. Go for Percona if your goal is to gain high-load performance in large-scale datasets.

## Programmeringsspråk

Adobe Commerce är en PHP-baserad applikation och de senaste releaserna är alltid kompatibla med den senaste stabila PHP-versionen (till exempel rekommenderar Adobe Commerce version 2.4 att man använder PHP 7.4). För att få högre säkerhet och prestanda finns det flera faktorer att ta hänsyn till när PHP konfigureras för att få maximal hastighet och effektivitet vid behandling av begäranden. Adobe Commerce webbutik byggs med HTML, JavaScript och LESS CSS-preprocessorn.

## Webbservrar

Adobe Commerce fully supports the Nginx and Apache web servers. Adobe Commerce innehåller exempelrekommenderade konfigurationsfiler för båda:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

The Nginx sample contains settings for better performance and is designed so that little reconfiguration is required.

## Caching services

Adobe Commerce har många alternativ för att lagra cacheminne och sessionsdata, bland annat Redis, Memcache, filsystem och databas. Redis är det bästa alternativet för en konfiguration med flera webbnoder.

We highly recommend using Varnish as the full-page cache server for your store. Adobe Commerce distribuerar en exempelkonfigurationsfil för lack som innehåller alla rekommenderade inställningar för prestanda.

## Söktjänster

For Adobe Commerce version 2.4 and later, all installations must be configured to use Elasticsearch as the catalog search solution. Elasticsearch provides quick and advanced searches on products in the catalog. Elasticsearch is optional for releases prior to 2.4, but it’s recommended.

## Meddelandekötjänster

Message queues provide an asynchronous communication mechanism in which the sender and the receiver of a message do not contact each other. RabbitMQ är en meddelandeansvarig med öppen källkod som erbjuder ett tillförlitligt, skalbart och portabelt meddelandesystem med hög tillgänglighet.

## Säkerhetsverktyg

The [Adobe Commerce Security Scan Tool](https://docs.magento.com/user-guide/magento/security-scan.html) enables you to regularly monitor your store websites and receive updates for known security risks, malware, and out-of-date software. Vanligtvis börjar du använda det här verktyget när du börjar testa användargodkännande (UAT). Besides the Adobe Commerce Security Scan tool, which is free and available for all implementations and versions of Adobe Commerce, there are other choices that can be used during the CI/CD process and before each release.

SonarQube är en plattform för kvalitetshantering med öppen källkod som är utformad för att analysera och mäta kodens tekniska kvalitet. SonarQube ger inte bara en fullständig rapport över kodfel, syntaxfel och sårbarheter, utan också förslag och exempel på hur du kan åtgärda koden. SonarQube är perfekt att använda i en CI/CD-miljö som ett verktyg som kan analysera koden innan den driftsätts.

Zed Attack Proxy (ZAP) är ett kostnadsfritt säkerhetstestverktyg som används av tusentals testare runt om i världen. ZAP is developed by OWASPand is one of the most preferred tools for manual security testing.
