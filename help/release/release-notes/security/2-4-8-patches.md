---
title: Adobe Commerce 2.4.8 Security Patch Release Notes
description: Läs mer om säkerhetsfelkorrigeringar, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetsuppdateringarna för Adobe Commerce version 2.4.7.
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: a5cdc9ee2d8c8632c40e0ced62182d5275b8b942
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.8

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p2

Säkerhetsutgåvan av Adobe Commerce 2.4.8-p2 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.8.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.8-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.8-p1 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som identifierats i tidigare versioner av 2.4.8.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

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

Korrigeringarna för CVE-2025-47110 och VULN-31547 finns också tillgängliga som en isolerad korrigering. Mer information finns i [kunskapsbasartikeln](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50).

>[!ENDSHADEBOX]
