---
title: Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.4
description: Läs mer om säkerhetsfelkorrigeringar, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetsuppdateringarna för Adobe Commerce version 2.4.4.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 7705e750a466ab134ae2616a40a32880ee0c45de
workflow-type: tm+mt
source-wordcount: '1429'
ht-degree: 0%

---


# Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.4

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.4-p9

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p9 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.4.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Plattformsuppgraderingar

* **Stöd för MariaDB 10.5**. Den här korrigeringsversionen är kompatibel med MariaDB version 10.5. Adobe Commerce är fortfarande kompatibelt med MariaDB version 10.4, men Adobe rekommenderar att du endast använder Adobe Commerce 2.4.4-p9 och alla kommande 2.4.4-säkerhetsuppdateringar med MariaDB version 10.5 eftersom MariaDB 10.4-underhållet upphör den 18 juni 2024. <!--AC-11530-->

## 2.4.4-p8

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p8 innehåller säkerhetsfelkorrigeringar för driftsättningen av Adobe Commerce 2.4.4. Uppdateringarna åtgärdar sårbarheter som har identifierats i tidigare versioner.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.4-p7

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p7 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Viktiga säkerhetsfunktioner

Den här versionen innehåller två viktiga säkerhetsförbättringar:

* **Ändringar av beteendet för icke genererade cachenycklar**:

   * Icke genererade cachenycklar för block innehåller nu prefix som skiljer sig från prefix för nycklar som genereras automatiskt. (Icke-genererade cachenycklar är nycklar som ställs in via malldirektivets syntax eller `setCacheKey` eller `setData` metoder.)
   * Icke genererade cachenycklar för block får nu endast innehålla bokstäver, siffror, bindestreck (-) och understreck (_). <!-- AC-9831 -->

* **Begränsningar för antalet autogenererade kupongkoder**. Commerce begränsar nu antalet kupongkoder som genereras automatiskt. Standardmaxvärdet är 250 000. Handlare kan använda nya **[!UICONTROL Code Quantity Limit]** konfigurationsalternativ (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) för att styra den nya gränsen. <!-- AC-8753 -->

## 2.4.4-p6

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p6 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

### Säkerhetsmarkering

I den här versionen introduceras en ny konfigurationsinställning för helsidescache som minskar riskerna med `{BASE-URL}/page_cache/block/esi HTTP` slutpunkt. Den här slutpunkten stöder obegränsade, dynamiskt inlästa innehållsfragment från Commerce layouthandtag och blockstrukturer. Den nya **[!UICONTROL Handles Param]** konfigurationsinställning anger värdet för den här slutpunktens `handles` -parameter, som avgör det högsta tillåtna antalet handtag per API. Egenskapens standardvärde är 100. Handlare kan ändra det här värdet från administratören (**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Känt fel

**Problem**: Adobe Commerce visar en **felaktig kontrollsumma** fel vid hämtning från Composer från `repo.magento.com`, och nedladdningen av paketet avbryts. Detta problem kan uppstå vid hämtning av versionspaket som gjorts tillgängliga under förhandsversionen och orsakas av en ompaketering av `magento/module-page-cache` paket.

**Tillfällig lösning**: Handlare som ser det här felet under nedladdningen kan göra följande:

1) Ta bort `/vendor` katalog i projektet, om det finns någon.
2) Kör `bin/magento composer update magento/module-page-cache` -kommando. Det här kommandot uppdaterar bara `page cache` paket.

Om problemet med kontrollsumman kvarstår tar du bort `composer.lock` innan du kör om `bin/magento composer update` för att uppdatera varje paket.

## 2.4.4-p5

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p5 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Använd en patch för att åtgärda säkerhetsluckan CVE-2022-31160 i jQuery-UI-biblioteket

`jQuery-UI` biblioteksversion 1.13.1 har ett känt säkerhetsproblem (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [jQuery UI security vulnerability CVE-2022-31160 fix for 2.4.4, 2.4.5, and 2.4.6 releases](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Kunskapsbasartikeln.

## 2.4.4-p4

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p4 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar och plattformsuppgraderingar för att förbättra efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Använd en patch för att åtgärda säkerhetsluckan CVE-2022-31160 i jQuery-UI-biblioteket

`jQuery-UI` biblioteksversion 1.13.1 har ett känt säkerhetsproblem (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [jQuery UI security vulnerability CVE-2022-31160 fix for 2.4.4, 2.4.5, and 2.4.6 releases](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Kunskapsbasartikeln.

### Säkerhetsmarkering

Standardbeteendet för [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL query and ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST-slutpunkten har ändrats. API:t returnerar nu alltid som standard `true`. Handlare kan aktivera det ursprungliga beteendet, vilket är att returnera `true` om e-postmeddelandet inte finns i databasen och `false` om den finns. <!-- AC-6695 -->

### Plattformsuppgraderingar

Plattformsuppgraderingar för den här versionen förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

* **Stöd för lack cache 7.3**. Den här versionen är kompatibel med den senaste versionen av Varnish Cache 7.3. Kompatibiliteten är fortfarande kompatibel med versionerna 6.0.x och 7u.2.x, men Adobe rekommenderar att du endast använder Adobe Commerce 2.4.4-p4 med Varnish Cache version 7.3 eller version 6.0 LTS.

* **Stöd för RabbitMQ 3.11**. Den här versionen är kompatibel med den senaste versionen av RabbitMQ 3.11. Kompatibiliteten finns kvar med RabbitMQ 3.9 som stöds till och med augusti 2023, men Adobe rekommenderar att du endast använder Adobe Commerce 2.4.4-p4 med RabbitMQ 3.11.

* **JavaScript-bibliotek**. De gamla JavaScript-biblioteken har uppgraderats till den senaste mindre versionen eller korrigeringsversionen, inklusive `moment.js` bibliotek (v2.29.4), `jQuery UI` bibliotek (v1.13.2), och `jQuery` validerings-plugin-bibliotek (v1.19.5).

## 2.4.4-p3

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p3 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.4-p2

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p2 innehåller korrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. En korrigering innebär att en ny konfigurationsinställning skapas. The **Kräv e-postbekräftelse om e-post har ändrats** Med konfigurationsinställningar kan administratörer kräva e-postbekräftelse när en administratör ändrar sin e-postadress. <!-- AC-6292-->

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

### Använd AC-3022.patch för att fortsätta erbjuda DHL som fraktfirma

DHL har introducerat schemaversion 6.2 och kommer inom kort att föråldra schemaversion 6.0. Adobe Commerce 2.4.4 och tidigare versioner som stöder DHL-integration stöder endast version 6.0. Handlare som distribuerar dessa versioner bör tillämpa `AC-3022.patch` så snart det går att fortsätta erbjuda DHL som fraktfirma. Se [Använd en patch för att fortsätta erbjuda DHL som fraktfirma](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) Kunskapsbasartikeln innehåller information om hur du hämtar och installerar korrigeringen.

## 2.4.4-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p1 innehåller korrigeringar av säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin](https://helpx.adobe.com/security/products/magento/apsb22-38.html).t

### Använd `AC-3022.patch` fortsätta erbjuda DHL som fraktfirma

DHL har introducerat schemaversion 6.2 och kommer inom kort att föråldra schemaversion 6.0. Adobe Commerce 2.4.4 och tidigare versioner som stöder DHL-integration stöder endast version 6.0. Handlare som distribuerar dessa versioner bör tillämpa `AC-3022.patch` så snart det går att fortsätta erbjuda DHL som fraktfirma. Se [Använd en patch för att fortsätta erbjuda DHL som fraktfirma](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Kunskapsbasartikeln innehåller information om hur du hämtar och installerar korrigeringen.

### Viktiga säkerhetsfunktioner

Säkerhetsförbättringar för den här versionen förbättrar efterlevnaden av de senaste bästa säkerhetsrutinerna, inklusive:

* ACL-resurser har lagts till i inventeringen.
* Säkerheten för lagermallar har förbättrats.

### Kända fel

**Problem**: Webb-API och integrationstester visar det här felet vid körning i 2.4.4-p1-paketet: `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **Tillfällig lösning**: Installera den tidigare versionen av Monolog genom att köra `require monolog/monolog:2.6.0` -kommando. <!-- AC-3651-->

**Problem**: Merchants kan se information om nedgradering av paketversioner under en uppgradering från Adobe Commerce 2.4.4 till Adobe Commerce 2.4.4-p1. Dessa meddelanden kan ignoreras. Skillnaden i paketversioner beror på avvikelser vid paketgenerering. Ingen produktfunktion har påverkats. Se [Paket som nedgraderats efter uppgradering från 2.4.4 till 2.4.4-p1](https://support.magento.com/hc/en-us/articles/8214752983949) Kunskapsbasartikeln innehåller information om berörda scenarier och tillfälliga lösningar.
