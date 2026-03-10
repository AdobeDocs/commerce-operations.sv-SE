---
title: Adobe Commerce 2.4.5 Security Patch Release Notes
description: Läs mer om säkerhetsfelkorrigeringar, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetsuppdateringarna för Adobe Commerce version 2.4.5.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: aca7de52b79acd844950e792430937795bd23eba
workflow-type: tm+mt
source-wordcount: '1729'
ht-degree: 0%

---


# Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.5

{{$include /help/_includes/release-notes/security-patch-intro.md}}

>[!IMPORTANT]
>
>MySQL 8.0 kommer att ha stöd för End of Support (EOS) från 30 april 2026.
>
>Efter detta datum kommer Adobe Commerce 2.4.5 inte att vara kompatibelt eller
>stöd för alla MySQL-versioner som släpps efter MySQL 8.0. Adobe kommer inte att
>validera eller ge stöd för nyare större MySQL-versioner på denna Adobe
>Commerce release line.
>
>Alla Adobe Commerce lokala kunder som kör version 2.4.5 är
>rekommenderas att migrera sina databasservrar till en kompatibel MariaDB-version.

## 2.4.5-p16

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p16 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB26-05](https://helpx.adobe.com/security/products/magento/apsb26-05.html).

{{b2b-patches}}

### Högdagrar

Den här versionen innehåller följande högdagrar:

#### Kompatibilitet med Apache ActiveMQ Artemis

På grund av den risk för slutet på stödet som är kopplad till RabbitMQ 4 har Adobe Commerce initierat en strategisk migrering till Apache ActiveMQ Artemis för att säkerställa långsiktig stabilitet och stöd för sin meddelandeköinfrastruktur.

* Adobe Commerce 2.4.5 har nu stöd för den senaste versionen av Apache ActiveMQ Artemis.
* Kompatibiliteten med RabbitMQ 4.1 bibehålls för kunder som föredrar att stanna kvar i den befintliga MQ-tjänsten.
* ActiveMQ stöds nu fullt ut i Adobe Commerce Cloud, inklusive distributioner av AWS ActiveMQ för molnbaserade program.

#### 2.4.5-p16-kompatibilitet med MariaDB 10.11

Adobe Commerce 2.4.5-p16 har verifierats för kompatibilitet med MariaDB 10.11, men stöder fortfarande MariaDB 10.6. Merchants som för närvarande kör 2.4.5-px kan tryggt uppgradera till 2.4.5-p16 och gå över från MariaDB 10.6 till MariaDB 10.11.

## 2.4.5-p15

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p15 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

>[!NOTE]
>
>Extended Support Security Patches for 2.4.5 are available for Adobe Commerce customers only. Dessa korrigeringar är inte tillgängliga för Magento Open Source kodbas. Se [Utökad support](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy#extended-support).

### Kända fel

#### Utcheckningssidan kan inte läsa in static.min.js och mixins.min.js

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.5-p14

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p14 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.5-p13

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p13 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Högdagrar

Den här versionen innehåller följande högdagrar:

* **API-prestandaförbättring** - Åtgärdar prestandaförsämring i asynkrona webb-API-slutpunkter som introducerades efter den föregående säkerhetspatchen.<!-- AC-14078 -->

* **Åtkomstkorrigering för CMS Blockerar** - Åtgärdar ett fel där administratörsanvändare med begränsade behörigheter (till exempel tillgång för enbart försäljning) inte kunde visa listsidan för [!UICONTROL CMS Blocks].

  Tidigare påträffade dessa användare ett fel på grund av saknade konfigurationsparametrar efter installation av tidigare säkerhetsuppdateringar.<!-- AC-14087 -->

* **Kompatibilitet för cookie-begränsning** - Korrigerar en bakåtkompatibel ändring som involverar konstanten `MAX_NUM_COOKIES` i ramverket. Den här uppdateringen återställer förväntat beteende och säkerställer kompatibilitet för tillägg och anpassningar som interagerar med cookie-gränser.<!-- AC-14475 -->

* **Asynkrona åtgärder** - Begränsade asynkrona åtgärder för att åsidosätta tidigare kundorder.<!-- AC-13917 -->

## 2.4.5-p12

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p12 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.5-p11

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p11 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.5.

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

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p9 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Programfixar som ingår i den här versionen

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.5-p8

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p8 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Programfix för CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Plattformsuppgraderingar

* **Stöd för MariaDB 10.5**. Den här korrigeringsversionen är kompatibel med MariaDB version 10.5. Adobe Commerce är fortfarande kompatibelt med MariaDB version 10.4, men Adobe rekommenderar att du använder Adobe Commerce 2.4.5-p8 och alla kommande 2.4.5-säkerhetsuppdateringar endast med MariaDB version 10.5 eftersom MariaDB 10.4-underhållet upphör den 18 juni 2024. <!--AC-11530-->

### Högdagrar

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.5-p7

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p7 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.5-p6

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p6 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.5. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Högdagrar

Den här versionen innehåller två viktiga säkerhetsförbättringar:

* **Ändringar av beteendet för icke genererade cachenycklar**:

   * Icke genererade cachenycklar för block innehåller nu prefix som skiljer sig från prefix för nycklar som genereras automatiskt. (Icke-genererade cachenycklar är nycklar som ställs in via malldirektiv eller metoderna `setCacheKey` eller `setData`.)
   * Icke genererade cachenycklar för block får nu bara innehålla bokstäver, siffror, bindestreck (-) och understreck (_). <!-- AC-9831 -->

* **Begränsningar för antalet autogenererade kupongkoder**. Commerce begränsar nu antalet kupongkoder som genereras automatiskt. Standardmaxvärdet är 250 000. Handlare kan använda det nya konfigurationsalternativet **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) för att styra den nya gränsen. <!-- AC-8753 -->

## 2.4.5-p5

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p5 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.5. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Högdagrar

I den här versionen introduceras en ny konfigurationsinställning för helsidescache, som hjälper till att minska riskerna med slutpunkten `{BASE-URL}/page_cache/block/esi HTTP`. Den här slutpunkten stöder obegränsade, dynamiskt inlästa innehållsfragment från Commerce layouthandtag och blockstrukturer. Den nya konfigurationsinställningen **[!UICONTROL Handles Param]** ställer in värdet för den här slutpunktens `handles` -parameter, som avgör det högsta tillåtna antalet hanterare per API. Egenskapens standardvärde är 100. Handlare kan ändra det här värdet från Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Kända fel

**Problem**: Adobe Commerce visar ett **fel kontrollsummefel** vid hämtning från Composer från `repo.magento.com` och pakethämtningen avbryts. Det här problemet kan uppstå vid hämtning av versionspaket som gjorts tillgängliga under förhandsversionen och orsakas av en ompaketering av paketet `magento/module-page-cache`.

**Tillfällig lösning**: Handlare som ser det här felet under hämtningen kan göra följande:

1) Ta bort katalogen `/vendor` i projektet, om det finns någon.
2) Kör kommandot `bin/magento composer update magento/module-page-cache`. Det här kommandot uppdaterar bara paketet `page cache`.

Om kontrollsummeproblemet kvarstår tar du bort filen `composer.lock` innan du kör kommandot `bin/magento composer update` igen för att uppdatera varje paket.

## 2.4.5-p4

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p4 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Programfix för CVE-2022-31160

`jQuery-UI` biblioteksversion 1.13.1 har ett känt säkerhetsproblem (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [jQuery UI-säkerhetsproblemet CVE-2022-31160 för version 2.4.4, 2.4.5 och 2.4.6 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6) i kunskapsbasartikeln.

## 2.4.5-p3

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p3 innehåller säkerhetsfixar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.5. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Programfix för CVE-2022-31160

`jQuery-UI` biblioteksversion 1.13.1 har ett känt säkerhetsproblem (CVE-2022-31160) som påverkar flera versioner av Adobe Commerce och Magento Open Source. Detta bibliotek är beroende av Adobe Commerce och Magento Open Source 2.4.4, 2.4.5 och 2.4.6. Handlare som kör berörda distributioner bör tillämpa den korrigering som anges i [säkerhetsluckan för användargränssnittsfrågor CVE-2022-31160 för version 2.4.4, 2.4.5 och 2.4.6 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6) i kunskapsbasartikeln.

### Högdagrar

Standardbeteendet för GraphQL-frågan [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) och REST-slutpunkten ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) har ändrats. API:t returnerar nu alltid `true` som standard. Handläggarna kan aktivera det ursprungliga beteendet, som är att returnera `true` om e-postmeddelandet inte finns i databasen och `false` om det finns. <!-- AC-6695 -->

### Plattformsuppgraderingar

Plattformsuppgraderingar för den här versionen förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

* **Stöd för lack cache 7.3**. Den här versionen är kompatibel med den senaste versionen av Varnish Cache 7.3. Kompatibiliteten är fortfarande kompatibel med versionerna 6.0.x och 7.2.x, men vi rekommenderar att du bara använder Adobe Commerce 2.4.5-p3 med Varnish Cache version 7.3 eller version 6.0 LTS.

* **Stöd för KaninMQ 3.11**. Den här versionen är kompatibel med den senaste versionen av RabbitMQ 3.11. Kompatibiliteten är fortfarande med RabbitMQ 3.9, som stöds fram till augusti 2023, men vi rekommenderar att du endast använder Adobe Commerce 2.4.5-p3 med RabbitMQ 3.11.

* **JavaScript-bibliotek**. Inaktuella JavaScript-bibliotek har uppgraderats till de senaste mindre versionerna eller korrigeringsversionerna, inklusive `moment.js` bibliotek (v2.29.4), `jQuery UI` bibliotek (v1.13.2) och `jQuery` plugin-bibliotek för validering (v1.19.5).

## 2.4.5-p2

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p2 innehåller tre säkerhetskorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.5-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.5-p1 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.5.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

En av säkerhetsfelkorrigeringarna var att skapa en ny konfigurationsinställning. [!UICONTROL **Kräv e-postbekräftelse om e-postadressen har ändrats**] så att administratörer kan kräva e-postbekräftelse när en Admin-användare ändrar sin e-postadress. <!-- AC-6292-->

<!-- Last updated from includes: 2026-02-20 15:30:03 -->
