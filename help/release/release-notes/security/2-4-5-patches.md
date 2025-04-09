---
title: Versionsinformation för säkerhetskorrigeringar för Adobe Commerce 2.4.5
description: Lär dig mer om buggfixar för säkerhet, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetskorrigeringarna för Adobe Commerce version 2.4.5.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 9bf1c539220d70a8e7fe449e4d91199f23cc23b2
workflow-type: tm+mt
source-wordcount: '1235'
ht-degree: 0%

---


# Versionsinformation för säkerhetskorrigeringar för Adobe Commerce 2.4.5

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.5-p12

Säkerhetsversionen Adobe Commerce 2.4.5-p12 innehåller buggfixar för säkerhetsproblem som identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html).

{{b2b-patches}}

## 2.4.5-p11

Säkerhetsversionen Adobe Commerce 2.4.5-p11 innehåller säkerhetsbuggar för sårbarheter som identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.5-p10

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p10 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Programfixar som ingår i den här versionen

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.5-p9

Säkerhetsversionen Adobe Commerce 2.4.5-p9 innehåller buggfixar för säkerhetsproblem som identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsbuggar [finns i Adobes säkerhetsbulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Programfixar som ingår i den här versionen

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.5-p8

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p8 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Installera snabbkorrigering för CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Uppgraderingar av plattformen

* **Stöd för** MariaDB 10.5. Den här korrigeringsversionen introducerar kompatibilitet med MariaDB version 10.5. Adobe Commerce är fortfarande kompatibelt med MariaDB version 10.4, men Adobe rekommenderar att du använder Adobe Commerce 2.4.5-p8 och alla kommande säkerhetskorrigeringar för 2.4.5 endast med MariaDB version 10.5 eftersom underhållet av MariaDB 10.4 upphör den 18 juni 2024. <!--AC-11530-->

### Höjdpunkter

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.5-p7

Säkerhetsversionen Adobe Commerce 2.4.5-p7 innehåller säkerhetsbuggar för sårbarheter som har identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.5-p6

Säkerhetsversionen Adobe Commerce 2.4.5-p6 innehåller säkerhetsbuggar för sårbarheter som har identifierats i tidigare versioner av 2.4.5. Den här versionen innehåller även säkerhetsförbättringar för att förbättra efterlevnaden av de senaste bästa säkerhetsmetoderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Högdagrar

Den här versionen innehåller två viktiga säkerhetsförbättringar:

* **Ändringar av beteendet för icke genererade cachenycklar**:

   * Icke genererade cachenycklar för block innehåller nu prefix som skiljer sig från prefix för nycklar som genereras automatiskt. (Icke-genererade cachenycklar är nycklar som ställs in via malldirektiv eller metoderna `setCacheKey` eller `setData`.)
   * Icke-genererade cachenycklar för block får nu endast innehålla bokstäver, siffror, bindestreck (-) och understreck (_).  <!-- AC-9831 -->

* **Begränsningar av antalet automatiskt genererade kupongkoder**. Commerce begränsar nu antalet kupongkoder som genereras automatiskt. Standardvärdet är 250 000. Handlare kan använda det nya **[!UICONTROL Code Quantity Limit]** konfigurationsalternativet (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) för att kontrollera den nya gränsen. <!-- AC-8753 -->

## 2.4.5-p5

Säkerhetsversionen Adobe Commerce 2.4.5-p5 innehåller säkerhetsbuggar för sårbarheter som har identifierats i tidigare versioner av 2.4.5. Den här versionen innehåller även säkerhetsförbättringar för att förbättra efterlevnaden av de senaste bästa säkerhetsmetoderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Högdagrar

I den här versionen introduceras en ny konfigurationsinställning för helsidescache, som hjälper till att minska riskerna med slutpunkten `{BASE-URL}/page_cache/block/esi HTTP`. Den här slutpunkten stöder obegränsade, dynamiskt inlästa innehållsfragment från Commerce layouthandtag och blockstrukturer. Den nya konfigurationsinställningen **[!UICONTROL Handles Param]** ställer in värdet för den här slutpunktens `handles` -parameter, som avgör det högsta tillåtna antalet hanterare per API. Egenskapens standardvärde är 100. Handlare kan ändra det här värdet från Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Kända fel

**Problem**: Adobe Commerce visar ett **fel kontrollsummefel** vid hämtning från Composer från `repo.magento.com` och pakethämtningen avbryts. Det här problemet kan uppstå vid hämtning av versionspaket som gjorts tillgängliga under förhandsversionen och orsakas av en ompaketering av paketet `magento/module-page-cache`.

**Tillfällig lösning**: Handlare som ser det här felet under hämtningen kan göra följande:

1) Ta bort katalogen `/vendor` i projektet, om det finns någon.
2) Kör kommandot `bin/magento composer update magento/module-page-cache`. Det här kommandot uppdaterar bara paketet `page cache`.

Om problemet med kontrollsumman kvarstår tar du bort `composer.lock` filen innan du `bin/magento composer update` kör kommandot igen för att uppdatera varje paket.

## 2.4.5-p4

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p4 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Programfix för CVE-2022-31160

`jQuery-UI` biblioteksversion 1.13.1 har ett känt säkerhetsproblem (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [jQuery UI-säkerhetsproblemet CVE-2022-31160 för version 2.4.4, 2.4.5 och 2.4.6 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6) i kunskapsbasartikeln.

## 2.4.5-p3

Säkerhetsversionen Adobe Commerce 2.4.5-p3 innehåller säkerhetskorrigeringar för sårbarheter som har identifierats i tidigare versioner av 2.4.5. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsmetoderna.

Den senaste informationen om korrigeringar av säkerhetsbuggar finns i [Adobes säkerhetsbulletin](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Installera snabbkorrigering för CVE-2022-31160

`jQuery-UI` biblioteksversion 1.13.1 har en känd säkerhetsrisk (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [säkerhetsluckan för användargränssnittsfrågor CVE-2022-31160 för version 2.4.4, 2.4.5 och 2.4.6 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6) i kunskapsbasartikeln.

### Högdagrar

Standardbeteendet för GraphQL-frågan [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) och REST-slutpunkten ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) har ändrats. API:t returnerar nu alltid `true` som standard. Handläggarna kan aktivera det ursprungliga beteendet, som är att returnera `true` om e-postmeddelandet inte finns i databasen och `false` om det finns. <!-- AC-6695 -->

### Plattformsuppgraderingar

Plattformsuppgraderingar för den här versionen förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

* **Stöd för lack cache 7.3**. Den här versionen är kompatibel med den senaste versionen av Varnish Cache 7.3. Kompatibiliteten är fortfarande kompatibel med versionerna 6.0.x och 7.2.x, men vi rekommenderar att du bara använder Adobe Commerce 2.4.5-p3 med Varnish Cache version 7.3 eller version 6.0 LTS.

* **Stöd för KaninMQ 3.11**. Den här versionen är kompatibel med den senaste versionen av RabbitMQ 3.11. Kompatibiliteten är fortfarande med RabbitMQ 3.9, som stöds fram till augusti 2023, men vi rekommenderar att du endast använder Adobe Commerce 2.4.5-p3 med RabbitMQ 3.11.

* **JavaScript-bibliotek**. Inaktuella JavaScript-bibliotek har uppgraderats till de senaste mindre versionerna eller korrigeringsversionerna, inklusive `moment.js` bibliotek (v2.29.4), `jQuery UI` bibliotek (v1.13.2) och `jQuery` plugin-bibliotek för validering (v1.19.5).

## 2.4.5-p2

Säkerhetsversionen Adobe Commerce 2.4.5-p2 innehåller tre säkerhetskorrigeringar för sårbarheter som har identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.5-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p1 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

En av säkerhetsbuggfixarna inkluderade skapandet av en ny konfigurationsinställning. Med **konfigurationsinställningen Kräv e-postbekräftelse om e-post har ändrats** kan administratörer kräva e-postbekräftelse när en administratörsanvändare ändrar sin e-postadress. <!-- AC-6292-->
