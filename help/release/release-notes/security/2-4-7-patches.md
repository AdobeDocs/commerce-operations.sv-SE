---
title: Adobe Commerce 2.4.7 Security Patch Release Notes
description: Läs mer om säkerhetsfelkorrigeringar, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetsuppdateringarna för Adobe Commerce version 2.4.7.
source-git-commit: 4ed23e2a8319ff97f8206f752cf1cbe2e73ea5c5
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.7-p1 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.7.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Säkerhetsmarkering

Den här versionen innehåller en uppdatering av [engångslösenordsinställningar](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) för att Google Authenticator ska kunna lösa ett fel som uppstod i [bakåtkompatibel ändring](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) i 2.4.7. Beskrivningen av **[!UICONTROL OTP Window]** fältet ger nu en korrekt förklaring av inställningen och standardvärdet har ändrats från `1` till `29`.

### Programfixar som ingår i den här versionen

Adobe Commerce 2.4.7-p1 åtgärdar ett fel som introducerats i omfattningen av UPS-integreringsmigreringen från SOAP till REST API. Detta problem påverkade kunder som levererar utanför USA och förhindrade dem från att använda måtten för kilo och centimeter för paket för att skapa leveranser med UPS. Se [Migrering av integrering av UPS-leveransmetoder från SOAP till RESTful API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) kunskapsbasartikel för mer information.
