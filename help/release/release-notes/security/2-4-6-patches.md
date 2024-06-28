---
title: Adobe Commerce 2.4.6 Security Patch Release Notes
description: Läs mer om säkerhetsfelkorrigeringar, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetsuppdateringarna för Adobe Commerce version 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: e5f659cc3bee2d116222c15549fb3d6094644531
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 0%

---


# Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.6

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.6-p6

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p6 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.6.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Säkerhetsmarkering

För kompatibilitet med Commerce version 2.4.6-p6 måste handlare som har Adobe Commerce B2B-tillägget uppgradera till [B2B version 1.4.2-p1](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes#b2b-v142p1.html).


### Ytterligare säkerhetsförbättringar

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.6-p5

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p5 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.6.

Den senaste informationen om dessa korrigeringar finns i [Adobe säkerhetsbulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.6-p4

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p4 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Viktiga säkerhetsfunktioner

Den här versionen innehåller två viktiga säkerhetsförbättringar:

* **Ändringar av beteendet för icke genererade cachenycklar**:

   * Icke genererade cachenycklar för block innehåller nu prefix som skiljer sig från prefix för nycklar som genereras automatiskt. (Icke-genererade cachenycklar är nycklar som ställs in via malldirektivets syntax eller `setCacheKey` eller `setData` metoder.)
   * Icke genererade cachenycklar för block får nu endast innehålla bokstäver, siffror, bindestreck (-) och understreck (_).  <!-- AC-9831 -->

* **Begränsningar för antalet autogenererade kupongkoder**. Commerce begränsar nu antalet kupongkoder som genereras automatiskt. Standardmaxvärdet är 250 000. Handlare kan använda nya **[!UICONTROL Code Quantity Limit]** konfigurationsalternativ (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) för att styra den nya gränsen. <!-- AC-8753 -->

## Adobe Commerce 2.4.6-p3

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p3 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetskorrigeringarna finns i [Adobe säkerhetsbulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Viktiga säkerhetsfunktioner

I den här versionen introduceras en ny konfigurationsinställning för helsidescache som minskar riskerna med `{BASE-URL}/page_cache/block/esi HTTP` slutpunkt. Den här slutpunkten stöder obegränsade, dynamiskt inlästa innehållsfragment från Commerce layouthandtag och blockstrukturer. Den nya **[!UICONTROL Handles Param]** konfigurationsinställning anger värdet för den här slutpunktens `handles` -parameter, som avgör det högsta tillåtna antalet handtag per API. Egenskapens standardvärde är 100. Handlare kan ändra det här värdet från administratören (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### Programfixar som ingår i den här versionen

Adobe Commerce 2.4.6-p3 innehåller en upplösning för prestandaförsämringen som korrigeras med patchen ACSD-51892. Handlarna påverkas inte av problemet som åtgärdas av den här patchen, som beskrivs i [ACSD-51892: Prestandaproblem där konfigurationsfiler läses in flera gånger](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) Kunskapsbasartikeln.

### Känt fel

**Problem**: Adobe Commerce visar en `wrong checksum` fel vid hämtning från Composer från `repo.magento.com`, och nedladdningen av paketet avbryts. Detta kan inträffa vid hämtning av releasepaket som gjorts tillgängliga under prerelease-perioden och orsakas av en ompaketering av `magento/module-page-cache` paket.

**Tillfällig lösning**: Handlare som ser det här felet under nedladdningen kan göra följande:

1) Ta bort `/vendor` katalog i projektet, om det finns någon.
2) Kör `bin/magento composer update magento/module-page-cache` -kommando. Det här kommandot uppdaterar bara `page cache` paket.

Om problemet med kontrollsumman kvarstår tar du bort `composer.lock` innan du kör om `bin/magento composer update` för att uppdatera varje paket.

## 2.4.6-p2

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p2 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Använd en patch för att åtgärda säkerhetsluckan CVE-2022-31160 i jQuery-UI-biblioteket

`jQuery-UI` biblioteksversion 1.13.1 har ett känt säkerhetsproblem (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [jQuery UI security vulnerability CVE-2022-31160 fix for 2.4.4, 2.4.5, and 2.4.6 releases](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Kunskapsbasartikeln.

### Säkerhetsmarkering

Värdet för `fastcgi_pass` i `nginx.sample` filen har returnerats till det tidigare (före 2.4.6-p1) värdet för `fastcgi_backend`. Det här värdet ändrades av misstag till `php-fpm:9000` i Adobe Commerce 2.4.6-p1.

### Programfixar som ingår i den här versionen

Adobe Commerce 2.4.6-p2 innehåller en upplösning för prestandaförsämringen som åtgärdas med patchen ACSD-51892. Handlarna påverkas inte av problemet som åtgärdas av den här patchen, som beskrivs i [ACSD-51892: Prestandaproblem där konfigurationsfiler läses in flera gånger](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) Kunskapsbasartikeln.

## Adobe Commerce 2.4.6-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p1 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar och plattformsuppgraderingar för att förbättra efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Använd en patch för att åtgärda säkerhetsluckan CVE-2022-31160 i jQuery-UI-biblioteket

`jQuery-UI` biblioteksversion 1.13.1 har ett känt säkerhetsproblem (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [Säkerhetslucka i användargränssnittet - åtgärda 2.4.4, 2.4.5 och 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Kunskapsbasartikeln.

#### Säkerhetsmarkering

Standardbeteendet för [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL query and ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST-slutpunkten har ändrats. API:t returnerar nu alltid som standard `true`. Handlare kan aktivera det ursprungliga beteendet, vilket är att returnera `true` om e-postmeddelandet inte finns i databasen och `false` om den finns. <!-- AC-6695 -->

### Plattformsuppgraderingar

Plattformsuppgraderingar för den här versionen förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

* **Stöd för lack cache 7.3**. Den här versionen är kompatibel med den senaste versionen av Varnish Cache 7.3. Kompatibiliteten är fortfarande kompatibel med versionerna 6.0.x och 7.2.x, men Adobe rekommenderas att endast använda Adobe Commerce 2.4.6-p1 med version 7.3 eller version 6.0 av Varnish Cache.

* **Stöd för RabbitMQ 3.11**. Den här versionen är kompatibel med den senaste versionen av RabbitMQ 3.11. Kompatibiliteten är fortfarande kompatibel med RabbitMQ 3.9 som stöds till och med augusti 2023, men Adobe rekommenderar att du endast använder Adobe Commerce 2.4.6-p1 med RabbitMQ 3.11.

* **JavaScript-bibliotek**. De gamla JavaScript-biblioteken har uppgraderats till den senaste mindre versionen eller korrigeringsversionen, inklusive `moment.js` bibliotek (v2.29.4), `jQuery UI` bibliotek (v1.13.2), och `jQuery` validerings-plugin-bibliotek (v1.19.5).

### Kända fel

* The `nginx.sample` filen uppdaterades av misstag med en ändring som ändrar värdet för `fastcgi_pass` från `fastcgi_backend` till `php-fpm:9000`. Den här ändringen kan ångras eller ignoreras. <!-- AC-8992 -->

* Beroenden som saknas för B2B-säkerhetspaketet orsakar följande installationsfel när B2B-tillägget installeras eller uppgraderas till 1.4.0.

  ```terminal
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Problemet kan lösas genom att man lägger till manuella beroenden för B2B-säkerhetspaketet med ett [stabilitetstagg](https://getcomposer.org/doc/04-schema.md#package-links). Mer information finns i [Versionsinformation för B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue).
