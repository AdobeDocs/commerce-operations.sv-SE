---
title: Adobe Commerce 2.4.7 Security Patch Release Notes
description: Läs mer om säkerhetsfelkorrigeringar, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetsuppdateringarna för Adobe Commerce version 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 2657c83d5467e603a681521886e80592e3b335aa
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---


# Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.7

{{$include /help/_includes/release-notes/security-patch-intro.md}}

>[!IMPORTANT]
>
>MySQL 8.0 kommer att ha stöd för End of Support (EOS) från 30 april 2026.
>
>Efter detta datum kommer Adobe Commerce 2.4.7 inte att vara kompatibelt eller
>stöd för alla MySQL-versioner som släpps efter MySQL 8.0. Adobe kommer inte att
>validera eller ge stöd för nyare större MySQL-versioner på denna Adobe
>Commerce release line.
>
>Alla Adobe Commerce lokala kunder som kör version 2.4.7 är
>rekommenderas att migrera sina databasservrar till en kompatibel MariaDB-version.

## 2.4.7-p9

Säkerhetsutgåvan av Adobe Commerce 2.4.7-p9 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.7.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB26-05](https://helpx.adobe.com/security/products/magento/apsb26-05.html).

{{b2b-patches}}

### Högdagrar

Den här versionen innehåller följande högdagrar:

#### MyDHL REST API support for DHL shipping integration

Integreringen av DHL-leverans stöder nu även MyDHL REST API:er utöver den befintliga XML-integreringen med DHL Express. Uppdateringen är anpassad efter DHL:s aktuella API-stack och förbereder borttagning av de äldre XML-API:erna.

#### Lägg till kompatibilitet med den senaste Composer-versionen

Adobe Commerce 2.4.7 har uppdaterats med stöd för Composer 2.9.x och är fortfarande kompatibelt med Composer 2.2 LTS.

## 2.4.7-p8

Säkerhetsutgåvan av Adobe Commerce 2.4.7-p8 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.7.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{b2b-patches}}

Den här versionen innehåller följande högdagrar:

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

{{oct-2025-backports}}

### Kända fel

#### Utcheckningssidan kan inte läsa in static.min.js och mixins.min.js

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.7-p7

Säkerhetsutgåvan av Adobe Commerce 2.4.7-p7 innehåller säkerhetsbuggfixar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.7.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.7-p6

Säkerhetsutgåvan av Adobe Commerce 2.4.7-p6 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.7.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Högdagrar

Den här versionen innehåller följande högdagrar:

* **Stöd för MariaDB** - Stöd för MariaDB 10.11 har lagts till.

* **API-prestandaförbättring** - Åtgärdar prestandaförsämring i asynkrona webb-API-slutpunkter som introducerades efter den föregående säkerhetspatchen.<!-- AC-14078 -->

* **Åtkomstkorrigering för CMS Blockerar** - Åtgärdar ett fel där administratörsanvändare med begränsade behörigheter (till exempel tillgång för enbart försäljning) inte kunde visa listsidan för [!UICONTROL CMS Blocks].

  Tidigare påträffade dessa användare ett fel på grund av saknade konfigurationsparametrar efter installation av tidigare säkerhetsuppdateringar.<!-- AC-14087 -->

* **Kompatibilitet för cookie-begränsning** - Korrigerar en bakåtkompatibel ändring som involverar konstanten `MAX_NUM_COOKIES` i ramverket. Den här uppdateringen återställer förväntat beteende och säkerställer kompatibilitet för tillägg och anpassningar som interagerar med cookie-gränser.<!-- AC-14475 -->

* **Asynkrona åtgärder** - Begränsade asynkrona åtgärder för att åsidosätta tidigare kundorder.<!-- AC-13917 -->

## 2.4.7-p5

Säkerhetsutgåvan av Adobe Commerce 2.4.7-p5 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.7.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

>[!BEGINSHADEBOX]

Den här versionen innehåller även stöd för Adobe Commerce [HIPAA-klart tillägg](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview).

>[!ENDSHADEBOX]

### Kända fel

**Problem**: När du installerar 2.4.7-p5 med PHP 8.2 eller senare installeras `paypal/module-braintree` version 4.7.0, som är avsedd för 2.4.8 och senare. För PHP 8.1 används rätt version av Braintree 4.6.1-p5. Den här felmatchningen beror på det lösa beroendet av `adobe-commerce/extensions-metapackage: ~2.0` i metapaketet. Detta påverkar kompatibiliteten och de funktioner som stöds för PHP 8.2+-distributioner.<!-- ACPLTSRV-6276) -->

Dessutom kan Braintree-tillägget version 4.6.1-p5 installeras för version 2.4.7-p4 och 2.4.7-p5, medan vissa användare förväntar sig version 4.6.1-p3 eller p4 på grund av att tidigare strängare beroenden har avspänts för att tillåta tilläggsuppgraderingar inom en versionslinje. <!-- AC-14430 -->

**Tillfällig lösning**: Om du vill vara säker på att du har rätt Braintree-version för PHP-versionen kör du `composer update` och installerar rätt version enligt beroendet för `adobe-commerce/extensions-metapackage:2.0.0`.

## 2.4.7-p4

Säkerhetsutgåvan av Adobe Commerce 2.4.7-p4 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.7.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

Säkerhetsutgåvan av Adobe Commerce 2.4.7-p3 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.7.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Programfixar som ingår i den här versionen

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

Säkerhetsutgåvan av Adobe Commerce 2.4.7-p2 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.7.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Högdagrar

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Programfixar som ingår i den här versionen

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.7-p1 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.7.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Programfix för CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Högdagrar

Den här versionen innehåller följande högdagrar:

* **Uppdatera inställningarna för [engångslösenord (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) för Google-autentiseraren**-Den här uppdateringen krävs för att åtgärda ett fel som uppstod vid en [bakåtkompatibel ändring](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) i 2.4.7. Beskrivningen av fältet **[!UICONTROL OTP Window]** ger nu en korrekt förklaring av inställningen och standardvärdet har ändrats från `1` till `29`.

* **Kompatibilitet med B2B-versioner** - För kompatibilitet med Commerce version 2.4.7-p1 måste handlare som har Adobe Commerce B2B-tillägget uppgradera till [B2B version 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Programfixar som ingår i den här versionen

Adobe Commerce 2.4.7-p1 åtgärdar ett fel som introducerats i omfattningen av UPS-integreringsmigreringen från SOAP till REST API. Detta problem påverkade kunder som levererar utanför USA och förhindrade dem från att använda måtten för kilo och centimeter för paket för att skapa leveranser med UPS. Mer information finns i artikeln [Migrering av UPS-leveransmetodintegrering från SOAP till RESTful API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) i kunskapsbasen.

<!-- Last updated from includes: 2026-03-19 11:29:47 -->
