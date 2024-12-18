---
title: Adobe Commerce 2.4.7 Security Patch Release Notes
description: Läs mer om säkerhetsfelkorrigeringar, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetsuppdateringarna för Adobe Commerce version 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: cb4f388c90902c2fe1df4a5d84841280fa740104
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.7-p3

Säkerhetsutgåvan av Adobe Commerce 2.4.7-p3 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.7.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Högdagrar

{{$include /help/_includes/release-notes/2024-10/security-foo.md}}

### Programfixar som ingår i den här versionen

{{$include /help/_includes/release-notes/2024-10/hotfixes-included-foo.md}}

## 2.4.7-p2

Säkerhetsutgåvan av Adobe Commerce 2.4.7-p2 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.7.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Högdagrar

{{$include /help/_includes/release-notes/2024-08/security.md}}

### Programfixar som ingår i den här versionen

{{$include /help/_includes/release-notes/2024-08/hotfixes-included.md}}

## 2.4.7-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.7-p1 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.7.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Programfix för CVE-2024-34102

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### Högdagrar

Den här versionen innehåller följande högdagrar:

* **Uppdatera inställningarna för [engångslösenord (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) för Google-autentiseraren**-Den här uppdateringen krävs för att åtgärda ett fel som uppstod vid en [bakåtkompatibel ändring](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) i 2.4.7. Beskrivningen av fältet **[!UICONTROL OTP Window]** ger nu en korrekt förklaring av inställningen och standardvärdet har ändrats från `1` till `29`.

* **Kompatibilitet med B2B-versioner** - För kompatibilitet med Commerce version 2.4.7-p1 måste handlare som har Adobe Commerce B2B-tillägget uppgradera till [B2B version 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Programfixar som ingår i den här versionen

Adobe Commerce 2.4.7-p1 åtgärdar ett fel som introducerats i omfattningen av UPS-integreringsmigreringen från SOAP till REST API. Detta problem påverkade kunder som levererar utanför USA och förhindrade dem från att använda måtten för kilo och centimeter för paket för att skapa leveranser med UPS. Mer information finns i artikeln [Migrering av integrering av UPS-leveransmetoder från SOAP till RESTful API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) i kunskapsbasen.
