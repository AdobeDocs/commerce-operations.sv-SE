---
title: Adobe Commerce 2.4.4 Security Patch Release Notes
description: Läs mer om säkerhetsfelkorrigeringar, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetsuppdateringarna för Adobe Commerce version 2.4.4.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 9bf1c539220d70a8e7fe449e4d91199f23cc23b2
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---


# Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.4

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.4-p13

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p13 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.4.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-26](https://helpx.adobe.com/se/security/products/magento/apsb25-26.html).

{{b2b-patches}}

## 2.4.4-p12

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p12 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.4.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-08](https://helpx.adobe.com/se/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.4-p11

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p11 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.4.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-73](https://helpx.adobe.com/se/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

## 2.4.4-p10

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p10 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.4.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-61](https://helpx.adobe.com/se/security/products/magento/apsb24-61.html).

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Programfixar som ingår i den här versionen

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.4-p9

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p9 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.4.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-40](https://helpx.adobe.com/se/security/products/magento/apsb24-40.html).

### Programfix för CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Plattformsuppgraderingar

* **MariaDB 10.5 support**. This patch release introduces compatibility with MariaDB version 10.5. Adobe Commerce is still compatible with MariaDB version 10.4, but Adobe recommends using Adobe Commerce 2.4.4-p9 and all upcoming 2.4.4 security-only patch releases only with MariaDB version 10.5 because MariaDB 10.4 maintenance ends on June 18, 2024. <!--AC-11530-->

### Högdagrar

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.4-p8

The Adobe Commerce 2.4.4-p8 security release provides security bug fixes for your Adobe Commerce 2.4.4 deployment. These updates fix vulnerabilities that have been identified in previous releases.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-18](https://helpx.adobe.com/se/security/products/magento/apsb24-18.html).

## 2.4.4-p7

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p7 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-03](https://helpx.adobe.com/se/security/products/magento/apsb24-03.html).

### Högdagrar

Den här versionen innehåller två viktiga säkerhetsförbättringar:

* **Ändringar av beteendet för icke genererade cachenycklar**:

   * Icke genererade cachenycklar för block innehåller nu prefix som skiljer sig från prefix för nycklar som genereras automatiskt. (Icke-genererade cachenycklar är nycklar som ställs in via malldirektiv eller metoderna `setCacheKey` eller `setData`.)
   * Icke genererade cachenycklar för block får nu bara innehålla bokstäver, siffror, bindestreck (-) och understreck (_). <!-- AC-9831 -->

* **Begränsningar för antalet autogenererade kupongkoder**. Commerce begränsar nu antalet kupongkoder som genereras automatiskt. Standardmaxvärdet är 250 000. Handlare kan använda det nya konfigurationsalternativet **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) för att styra den nya gränsen. <!-- AC-8753 -->

## 2.4.4-p6

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p6 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

For the latest information about the security bug fixes, see [Adobe Security Bulletin APSB23-50](https://helpx.adobe.com/se/security/products/magento/apsb23-50.html).

Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

### Högdagrar

I den här versionen introduceras en ny konfigurationsinställning för helsidescache, som hjälper till att minska riskerna med slutpunkten `{BASE-URL}/page_cache/block/esi HTTP`. Den här slutpunkten stöder obegränsade, dynamiskt inlästa innehållsfragment från Commerce layouthandtag och blockstrukturer. Den nya konfigurationsinställningen **[!UICONTROL Handles Param]** ställer in värdet för den här slutpunktens `handles` -parameter, som avgör det högsta tillåtna antalet hanterare per API. Egenskapens standardvärde är 100. Handlare kan ändra det här värdet från Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Kända fel

**Issue**: Adobe Commerce displays a **wrong checksum** error during download by Composer from `repo.magento.com`, and package download is interrupted. This issue can occur during download of release packages that were made available during prerelease and is caused by a repackaging of the `magento/module-page-cache` package.

**Workaround**: Merchants who see this error during download can take these steps:

1) Delete the `/vendor` directory inside the project, if one exists.
2) Run the `bin/magento composer update magento/module-page-cache` command. This command updates only the `page cache` package.

If the checksum problem persists, remove the `composer.lock` file before re-running the `bin/magento composer update` command to update every package.

## 2.4.4-p5

The Adobe Commerce 2.4.4-p5 security release provides security bug fixes for vulnerabilities that have been identified in previous releases.

For the latest information about the security bug fixes, see [Adobe Security Bulletin APSB23-42](https://helpx.adobe.com/se/security/products/magento/apsb23-42.html).

### Programfix för CVE-2022-31160

`jQuery-UI` biblioteksversion 1.13.1 har ett känt säkerhetsproblem (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [jQuery UI-säkerhetsproblemet CVE-2022-31160 för version 2.4.4, 2.4.5 och 2.4.6 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=sv-SE) i kunskapsbasartikeln.

## 2.4.4-p4

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p4 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar och plattformsuppgraderingar för att förbättra efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB23-35](https://helpx.adobe.com/se/security/products/magento/apsb23-35.html).

### Programfix för CVE-2022-31160

`jQuery-UI` biblioteksversion 1.13.1 har ett känt säkerhetsproblem (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [jQuery UI-säkerhetsproblemet CVE-2022-31160 för version 2.4.4, 2.4.5 och 2.4.6 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=sv-SE) i kunskapsbasartikeln.

### Högdagrar

Standardbeteendet för GraphQL-frågan [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) och REST-slutpunkten ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) har ändrats. API:t returnerar nu alltid `true` som standard. Handläggarna kan aktivera det ursprungliga beteendet, som är att returnera `true` om e-postmeddelandet inte finns i databasen och `false` om det finns. <!-- AC-6695 -->

### Plattformsuppgraderingar

Plattformsuppgraderingar för den här versionen förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

* **Stöd för lack cache 7.3**. Den här versionen är kompatibel med den senaste versionen av Varnish Cache 7.3. Kompatibiliteten behålls med versionerna 6.0.x och 7u.2.x, men Adobe rekommenderar att du endast använder Adobe Commerce 2.4.4-p4 med Varnish Cache version 7.3 eller version 6.0 LTS.

* **Stöd för KaninMQ 3.11**. Den här versionen är kompatibel med den senaste versionen av RabbitMQ 3.11. Kompatibiliteten kvarstår med RabbitMQ 3.9 som stöds till och med augusti 2023, men Adobe rekommenderar att du bara använder Adobe Commerce 2.4.4-p4 med RabbitMQ 3.11.

* **JavaScript-bibliotek**. Inaktuella JavaScript-bibliotek har uppgraderats till de senaste mindre versionerna eller korrigeringsversionerna, inklusive `moment.js` bibliotek (v2.29.4), `jQuery UI` bibliotek (v1.13.2) och `jQuery` plugin-bibliotek för validering (v1.19.5).

## 2.4.4-p3

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p3 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB23-17](https://helpx.adobe.com/se/security/products/magento/apsb23-17.html).

## 2.4.4-p2

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p2 innehåller korrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. En korrigering innebär att en ny konfigurationsinställning skapas. **Kräv e-postbekräftelse om e-postadressen har ändrats** så att administratörer kan kräva e-postbekräftelse när en administratörsanvändare ändrar sin e-postadress. <!-- AC-6292-->

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB22-48](https://helpx.adobe.com/se/security/products/magento/apsb22-48.html).

### Använd AC-3022.patch för att fortsätta erbjuda DHL som fraktfirma

DHL har introducerat schemaversion 6.2 och kommer inom kort att föråldra schemaversion 6.0. Adobe Commerce 2.4.4 och tidigare versioner som stöder DHL-integration stöder endast version 6.0. Merchants som distribuerar dessa releaser ska tillämpa `AC-3022.patch` så snart som möjligt för att fortsätta erbjuda DHL som fraktfirma. Information om hur du hämtar och installerar korrigeringsfilen finns i [Använd en korrigeringsfil för att fortsätta erbjuda DHL som fraktfirma](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481).

## 2.4.4-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.4-p1 innehåller korrigeringar av säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin](https://helpx.adobe.com/se/security/products/magento/apsb22-38.html).t

### Använd `AC-3022.patch` om du vill fortsätta erbjuda DHL som fraktfirma

DHL har introducerat schemaversion 6.2 och kommer inom kort att föråldra schemaversion 6.0. Adobe Commerce 2.4.4 och tidigare versioner som stöder DHL-integration stöder endast version 6.0. Merchants som distribuerar dessa releaser ska tillämpa `AC-3022.patch` så snart som möjligt för att fortsätta erbjuda DHL som fraktfirma. Information om hur du hämtar och installerar korrigeringsfilen finns i [Använd en korrigeringsfil för att fortsätta erbjuda DHL som fraktfirma](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier).

### Högdagrar

Säkerhetsförbättringar för den här versionen förbättrar efterlevnaden av de senaste bästa säkerhetsrutinerna, inklusive:

* ACL-resurser har lagts till i inventeringen.
* Säkerheten för lagermallar har förbättrats.

### Kända fel

**Problem**: Det här felet visas i webb-API:t och integrationstester när de körs i 2.4.4-p1-paketet: `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **Tillfällig lösning**: Installera den tidigare versionen av Monolog genom att köra kommandot `require monolog/monolog:2.6.0`. <!-- AC-3651-->

**Utgåva**: Merchants kan se information om nedgradering av paketversioner under en uppgradering från Adobe Commerce 2.4.4 till Adobe Commerce 2.4.4-p1. Dessa meddelanden kan ignoreras. Skillnaden i paketversioner beror på avvikelser vid paketgenerering. Ingen produktfunktion har påverkats. See the [Packages downgraded after upgrading from 2.4.4 to 2.4.4-p1](https://support.magento.com/hc/en-us/articles/8214752983949) Knowledge Base article for a discussion of affected scenarios and workarounds.
