---
title: Adobe Commerce 2.4.6 Security Patch Release Notes
description: Läs mer om säkerhetsfelkorrigeringar, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetsuppdateringarna för Adobe Commerce version 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: ba5b422f40803e6c5e797e939dd2fc9e3e7c195a
workflow-type: tm+mt
source-wordcount: '1540'
ht-degree: 0%

---


# Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.6

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.6-p13

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p13 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.6.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-94](https://helpx.adobe.com/se/security/products/magento/apsb25-94.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

## 2.4.6-p12

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p12 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.6.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-71](https://helpx.adobe.com/se/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.6-p11

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p11 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.6.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-50](https://helpx.adobe.com/se/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Högdagrar

Den här versionen innehåller följande högdagrar:

* **Stöd för MariaDB** - Stöd för MariaDB 10.11 har lagts till.

* **API-prestandaförbättring** - Åtgärdar prestandaförsämring i asynkrona webb-API-slutpunkter som introducerades efter den föregående säkerhetspatchen.<!-- AC-14078 -->

* **Åtkomstkorrigering för CMS Blockerar** - Åtgärdar ett fel där administratörsanvändare med begränsade behörigheter (till exempel tillgång för enbart försäljning) inte kunde visa listsidan för [!UICONTROL CMS Blocks].

  Tidigare påträffade dessa användare ett fel på grund av saknade konfigurationsparametrar efter installation av tidigare säkerhetsuppdateringar.<!-- AC-14087 -->

* **Kompatibilitet för cookie-begränsning** - Korrigerar en bakåtkompatibel ändring som involverar konstanten `MAX_NUM_COOKIES` i ramverket. Den här uppdateringen återställer förväntat beteende och säkerställer kompatibilitet för tillägg och anpassningar som interagerar med cookie-gränser.<!-- AC-14475 -->

* **Asynkrona åtgärder** - Begränsade asynkrona åtgärder för att åsidosätta tidigare kundorder.<!-- AC-13917 -->

## 2.4.6-p10

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p10 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.6.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-26](https://helpx.adobe.com/se/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.6-p9

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p9 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.6.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-08](https://helpx.adobe.com/se/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.6-p8

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p8 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.6.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-73](https://helpx.adobe.com/se/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Programfixar som ingår i den här versionen

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.6-p7

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p7 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.6.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-61](https://helpx.adobe.com/se/security/products/magento/apsb24-61.html).

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Programfixar som ingår i den här versionen

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.6-p6

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p6 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.6.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-40](https://helpx.adobe.com/se/security/products/magento/apsb24-40.html).

För kompatibilitet med Commerce version 2.4.6-p6 måste handlare som har tillägget Adobe Commerce B2B uppgradera till [B2B version 1.4.2-p1](https://experienceleague.adobe.com/sv/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Programfix för CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

För kompatibilitet med Commerce version 2.4.6-p6 måste handlare som har tillägget Adobe Commerce B2B uppgradera till [B2B version 1.4.2-p1](https://experienceleague.adobe.com/sv/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Högdagrar

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.6-p5

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p5 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.6.

Den senaste informationen om dessa korrigeringar finns i [Adobe säkerhetsbulletin APSB24-18](https://helpx.adobe.com/se/security/products/magento/apsb24-18.html).

## 2.4.6-p4

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p4 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-03](https://helpx.adobe.com/se/security/products/magento/apsb24-03.html).

### Högdagrar

Den här versionen innehåller två viktiga säkerhetsförbättringar:

* **Ändringar av beteendet för icke genererade cachenycklar**:

   * Icke genererade cachenycklar för block innehåller nu prefix som skiljer sig från prefix för nycklar som genereras automatiskt. (Icke-genererade cachenycklar är nycklar som ställs in via malldirektiv eller metoderna `setCacheKey` eller `setData`.)
   * Icke genererade cachenycklar för block får nu bara innehålla bokstäver, siffror, bindestreck (-) och understreck (_). <!-- AC-9831 -->

* **Begränsningar för antalet autogenererade kupongkoder**. Commerce begränsar nu antalet kupongkoder som genereras automatiskt. Standardmaxvärdet är 250 000. Handlare kan använda det nya konfigurationsalternativet **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) för att styra den nya gränsen. <!-- AC-8753 -->

## 2.4.6-p3

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p3 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfixar finns i [Adobe säkerhetsbulletin APSB23-50](https://helpx.adobe.com/se/security/products/magento/apsb23-50.html).

### Högdagrar

I den här versionen introduceras en ny konfigurationsinställning för helsidescache, som hjälper till att minska riskerna med slutpunkten `{BASE-URL}/page_cache/block/esi HTTP`. Den här slutpunkten stöder obegränsade, dynamiskt inlästa innehållsfragment från Commerce layouthandtag och blockstrukturer. Den nya konfigurationsinställningen **[!UICONTROL Handles Param]** ställer in värdet för den här slutpunktens `handles` -parameter, som avgör det högsta tillåtna antalet hanterare per API. Egenskapens standardvärde är 100. Handlare kan ändra det här värdet från Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### Programfixar som ingår i den här versionen

Adobe Commerce 2.4.6-p3 innehåller en upplösning för prestandaförsämringen som korrigeras med patchen ACSD-51892. Handlare påverkas inte av det problem som den här korrigeringen åtgärdar, som beskrivs i [ACSD-51892: Prestandaproblem där konfigurationsfiler läses in flera gånger](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=sv-SE) kunskapsbasartikeln.

### Kända fel

**Problem**: Adobe Commerce visar ett `wrong checksum`-fel under hämtning från Composer från `repo.magento.com` och pakethämtningen avbryts. Det här problemet kan uppstå vid hämtning av frisläppningspaket som är tillgängliga under betaversionsperioden och orsakas av en ompaketering av `magento/module-page-cache`-paketet.

**Tillfällig lösning**: Handlare som ser det här felet under hämtningen kan göra följande:

1) Ta bort katalogen `/vendor` i projektet, om det finns någon.
2) Kör kommandot `bin/magento composer update magento/module-page-cache`. Det här kommandot uppdaterar bara paketet `page cache`.

Om kontrollsummeproblemet kvarstår tar du bort filen `composer.lock` innan du kör kommandot `bin/magento composer update` igen för att uppdatera varje paket.

## 2.4.6-p2

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p2 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB23-42](https://helpx.adobe.com/se/security/products/magento/apsb23-42.html).

### Programfix för CVE-2022-31160

`jQuery-UI` biblioteksversion 1.13.1 har ett känt säkerhetsproblem (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [jQuery UI-säkerhetsproblemet CVE-2022-31160 för version 2.4.4, 2.4.5 och 2.4.6 &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=sv-SE) i kunskapsbasartikeln.

### Högdagrar

Värdet `fastcgi_pass` i filen `nginx.sample` har returnerats till det tidigare (före 2.4.6-p1) värdet `fastcgi_backend`. Det här värdet ändrades av misstag till `php-fpm:9000` i Adobe Commerce 2.4.6-p1.

### Programfixar som ingår i den här versionen

Adobe Commerce 2.4.6-p2 innehåller en upplösning för prestandaförsämringen som åtgärdas med patchen ACSD-51892. Handlare påverkas inte av det problem som den här korrigeringen åtgärdar, som beskrivs i [ACSD-51892: Prestandaproblem där konfigurationsfiler läses in flera gånger](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=sv-SE) kunskapsbasartikeln.

## 2.4.6-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.6-p1 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar och plattformsuppgraderingar för att förbättra efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB23-35](https://helpx.adobe.com/se/security/products/magento/apsb23-35.html).

### Programfix för CVE-2022-31160

`jQuery-UI` biblioteksversion 1.13.1 har ett känt säkerhetsproblem (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [säkerhetsluckan för användargränssnittsfrågor CVE-2022-31160 för version 2.4.4, 2.4.5 och 2.4.6 &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=sv-SE) i kunskapsbasartikeln.

#### Högdager

Standardbeteendet för GraphQL-frågan [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) och REST-slutpunkten ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) har ändrats. API:t returnerar nu alltid `true` som standard. Handläggarna kan aktivera det ursprungliga beteendet, som är att returnera `true` om e-postmeddelandet inte finns i databasen och `false` om det finns. <!-- AC-6695 -->

### Plattformsuppgraderingar

Plattformsuppgraderingar för den här versionen förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

* **Stöd för lack cache 7.3**. Den här versionen är kompatibel med den senaste versionen av Varnish Cache 7.3. Kompatibiliteten är fortfarande kompatibel med versionerna 6.0.x och 7.2.x, men Adobe rekommenderar att du endast använder Adobe Commerce 2.4.6-p1 med version 7.3 eller 6.0 LTS för Varnish Cache.

* **Stöd för KaninMQ 3.11**. Den här versionen är kompatibel med den senaste versionen av RabbitMQ 3.11. Kompatibiliteten är fortfarande med RabbitMQ 3.9, som stöds till och med augusti 2023, men Adobe rekommenderar att du endast använder Adobe Commerce 2.4.6-p1 med RabbitMQ 3.11.

* **JavaScript-bibliotek**. Inaktuella JavaScript-bibliotek har uppgraderats till de senaste mindre versionerna eller korrigeringsversionerna, inklusive `moment.js` bibliotek (v2.29.4), `jQuery UI` bibliotek (v1.13.2) och `jQuery` plugin-bibliotek för validering (v1.19.5).

### Kända fel

* Filen `nginx.sample` uppdaterades av misstag med en ändring som ändrar värdet för `fastcgi_pass` från `fastcgi_backend` till `php-fpm:9000`. Den här ändringen kan ångras eller ignoreras. <!-- AC-8992 -->

* Beroenden som saknas för B2B-säkerhetspaketet orsakar följande installationsfel när B2B-tillägget installeras eller uppgraderas till 1.4.0.

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Det här problemet kan lösas genom att lägga till manuella beroenden för B2B-säkerhetspaketet med en [stabilitetstagg](https://getcomposer.org/doc/04-schema.md#package-links). Mer information finns i [Versionsinformationen för B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html?lang=sv-SE#known-issue).

<!-- Last updated from includes: 2025-10-06 13:12:34 -->
