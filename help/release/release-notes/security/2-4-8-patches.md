---
title: Adobe Commerce 2.4.8 Security Patch Release Notes
description: Läs mer om säkerhetsfelkorrigeringar, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetsuppdateringarna för Adobe Commerce version 2.4.7.
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: c297996273c42481fe9d3ee20ec3b9256e27fb5f
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.8

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p4

Säkerhetsutgåvan av Adobe Commerce 2.4.8-p4 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.8.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB26-05](https://helpx.adobe.com/se/security/products/magento/apsb26-05.html).

{{b2b-patches}}

### Högdagrar

Den här versionen innehåller följande högdagrar:

#### MyDHL REST API support for DHL shipping integration

Integreringen av DHL-leverans stöder nu även MyDHL REST API:er utöver den befintliga XML-integreringen med DHL Express. Uppdateringen är anpassad efter DHL:s aktuella API-stack och förbereder borttagning av de äldre XML-API:erna.

#### Lägg till kompatibilitet med den senaste Composer-versionen

Adobe Commerce 2.4.8 har uppdaterats med stöd för Composer 2.9.x och är fortfarande kompatibelt med Composer 2.2 LTS.

## 2.4.8-p3

Säkerhetsutgåvan av Adobe Commerce 2.4.8-p3 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.8.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-94](https://helpx.adobe.com/se/security/products/magento/apsb25-94.html).

{{b2b-patches}}

### Högdagrar

Den här versionen innehåller följande högdagrar:

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* Åtgärda problem med AVS2E-3874: REST API-svaret för orderdetaljer innehåller nu korrekta värden för attributen `base_row_total` och `row_total` om flera objekt beställdes.

* Korrigering för AC-15446: Korrigerade ett fel i `Magento\Framework\Mail\EmailMessage` där `getBodyText()` försökte anropa en `getTextBody()`-metod som inte finns på `Symfony\Component\Mime\Message`, vilket säkerställer kompatibilitet med Magento 2.4.8-p2 och `magento/framework` 103.0.8-p2.

{{oct-2025-backports}}

### Kända fel

#### Utcheckningssidan kan inte läsa in static.min.js och mixins.min.js

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.8-p2

Säkerhetsutgåvan av Adobe Commerce 2.4.8-p2 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.8.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-71](https://helpx.adobe.com/se/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.8-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.8-p1 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.8.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-50](https://helpx.adobe.com/se/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Högdagrar

Den här versionen innehåller följande högdagrar:

* **API-prestandaförbättring** - Åtgärdar prestandaförsämring i asynkrona webb-API-slutpunkter som introducerades efter den föregående säkerhetspatchen.<!-- AC-14078 -->

* **Åtkomstkorrigering för CMS Blockerar** - Åtgärdar ett fel där administratörsanvändare med begränsade behörigheter (till exempel tillgång för enbart försäljning) inte kunde visa listsidan för [!UICONTROL CMS Blocks].

  Tidigare påträffade dessa användare ett fel på grund av saknade konfigurationsparametrar efter installation av tidigare säkerhetsuppdateringar.<!-- AC-14087 -->

* **Kompatibilitet för cookie-begränsning** - Korrigerar en bakåtkompatibel ändring som involverar konstanten `MAX_NUM_COOKIES` i ramverket. Den här uppdateringen återställer förväntat beteende och säkerställer kompatibilitet för tillägg och anpassningar som interagerar med cookie-gränser.<!-- AC-14475 -->

* **Asynkrona åtgärder** - Begränsade asynkrona åtgärder för att åsidosätta tidigare kundorder.<!-- AC-13917 -->

* **Korrigering för CVE-2025-47110** - Åtgärdar en säkerhetslucka i e-postmallar.<!-- AC-14695 -->

* **Korrigering för VULN-31547** - Åtgärdar ett kategorifel med kanoniska länkar.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

Korrigeringarna för CVE-2025-47110 och VULN-31547 finns också tillgängliga som en isolerad korrigering. Mer information finns i [kunskapsbasartikeln](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50).

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2026-02-20 15:30:03 -->
