---
title: Adobe Commerce 2.4.5 Security Patch Release Notes
description: Läs mer om säkerhetsfelkorrigeringar, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetsuppdateringarna för Adobe Commerce version 2.4.5.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: e1c5b5e5c1a8800aa5aa2657060f61c16743cbda
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 0%

---


# Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.5

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.5-p7

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p7 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.5-p6

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p6 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Viktiga säkerhetsfunktioner

Den här versionen innehåller två viktiga säkerhetsförbättringar:

* **Ändringar av beteendet för icke genererade cachenycklar**:

   * Icke genererade cachenycklar för block innehåller nu prefix som skiljer sig från prefix för nycklar som genereras automatiskt. (Icke-genererade cachenycklar är nycklar som ställs in via malldirektivets syntax eller `setCacheKey` eller `setData` metoder.)
   * Icke genererade cachenycklar för block får nu endast innehålla bokstäver, siffror, bindestreck (-) och understreck (_).  <!-- AC-9831 -->

* **Begränsningar för antalet autogenererade kupongkoder**. Commerce begränsar nu antalet kupongkoder som genereras automatiskt. Standardmaxvärdet är 250 000. Handlare kan använda nya **[!UICONTROL Code Quantity Limit]** konfigurationsalternativ (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) för att styra den nya gränsen. <!-- AC-8753 -->



## Adobe Commerce 2.4.5-p5

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p5 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Säkerhetsmarkering

I den här versionen introduceras en ny konfigurationsinställning för helsidescache som minskar riskerna med `{BASE-URL}/page_cache/block/esi HTTP` slutpunkt. Den här slutpunkten stöder obegränsade, dynamiskt inlästa innehållsfragment från Commerce layouthandtag och blockstrukturer. Den nya **[!UICONTROL Handles Param]** konfigurationsinställning anger värdet för den här slutpunktens `handles` -parameter, som avgör det högsta tillåtna antalet handtag per API. Egenskapens standardvärde är 100. Handlare kan ändra det här värdet från administratören (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Känt fel

**Problem**: Adobe Commerce visar en **felaktig kontrollsumma** fel vid hämtning från Composer från `repo.magento.com`, och nedladdningen av paketet avbryts. Detta problem kan uppstå vid hämtning av versionspaket som gjorts tillgängliga under förhandsversionen och orsakas av en ompaketering av `magento/module-page-cache` paket.

**Tillfällig lösning**: Handlare som ser det här felet under nedladdningen kan göra följande:

1) Ta bort `/vendor` katalog i projektet, om det finns någon.
2) Kör `bin/magento composer update magento/module-page-cache` -kommando. Det här kommandot uppdaterar bara `page cache` paket.

Om problemet med kontrollsumman kvarstår tar du bort `composer.lock` innan du kör om `bin/magento composer update` för att uppdatera varje paket.

## Adobe Commerce 2.4.5-p4

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p4 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Använd en patch för att åtgärda säkerhetsluckan CVE-2022-31160 i jQuery-UI-biblioteket

`jQuery-UI` biblioteksversion 1.13.1 har ett känt säkerhetsproblem (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [jQuery UI security vulnerability CVE-2022-31160 fix for 2.4.4, 2.4.5, and 2.4.6 releases](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Kunskapsbasartikeln.

## Adobe Commerce 2.4.5-p3

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p3 innehåller säkerhetsfixar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Använd en patch för att åtgärda säkerhetsluckan CVE-2022-31160 i jQuery-UI-biblioteket

`jQuery-UI` biblioteksversion 1.13.1 har ett känt säkerhetsproblem (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [Säkerhetslucka i användargränssnittet - åtgärda 2.4.4, 2.4.5 och 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Kunskapsbasartikeln.

### Säkerhetsmarkering

Standardbeteendet för [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL query and ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST-slutpunkten har ändrats. API:t returnerar nu alltid som standard `true`. Handlare kan aktivera det ursprungliga beteendet, vilket är att returnera `true` om e-postmeddelandet inte finns i databasen och `false` om den finns. <!-- AC-6695 -->

### Plattformsuppgraderingar

Plattformsuppgraderingar för den här versionen förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

* **Stöd för lack cache 7.3**. Den här versionen är kompatibel med den senaste versionen av Varnish Cache 7.3. Kompatibiliteten är fortfarande kompatibel med versionerna 6.0.x och 7.2.x, men vi rekommenderar att du bara använder Adobe Commerce 2.4.5-p3 med Varnish Cache version 7.3 eller version 6.0 LTS.

* **Stöd för RabbitMQ 3.11**. Den här versionen är kompatibel med den senaste versionen av RabbitMQ 3.11. Kompatibiliteten är fortfarande med RabbitMQ 3.9, som stöds fram till augusti 2023, men vi rekommenderar att du endast använder Adobe Commerce 2.4.5-p3 med RabbitMQ 3.11.

* **JavaScript-bibliotek**. De gamla JavaScript-biblioteken har uppgraderats till den senaste mindre versionen eller korrigeringsversionen, inklusive `moment.js` bibliotek (v2.29.4), `jQuery UI` bibliotek (v1.13.2), och `jQuery` validerings-plugin-bibliotek (v1.19.5).

## Versionsinformation om Adobe Commerce 2.4.5-p2

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p2 innehåller tre säkerhetskorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## Adobe Commerce 2.4.5-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p1 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i den tidigare utgåvan (Adobe Commerce 2.4.5 och Magento Open Source 2.4.5).

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

En av säkerhetsfelkorrigeringarna var att skapa en ny konfigurationsinställning. The **Kräv e-postbekräftelse om e-post har ändrats** Med konfigurationsinställningen kan administratörer kräva e-postbekräftelse när en Admin-användare ändrar sin e-postadress. <!-- AC-6292-->


