---
title: '[!DNL Cloud Automation Patching Service (CAPS)]'
description: Lär dig mer om  [!DNL Cloud Automation Patching Service (CAPS)], dess användningsområden, hur du får tillgång till den och bästa metoderna för automatiserad korrigering
hide: true
hidefromtoc: true
source-git-commit: 4bb2d597e93379dbe81bae100ccc0b94b39acf26
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# [!DNL Cloud Automation Patching Service (CAPS)]

[!DNL Cloud Automation Patching Service] ([!DNL CAPS]) är ett verktyg som automatiserar processen att tillämpa och återställa korrigeringsfiler för Adobe Commerce i molnmiljöer. Det ger Commerce projektadministratörer ett smidigt arbetsflöde för att tillämpa och återställa korrigeringsfiler som innehåller inbyggd validering och hälsokontroller för att säkerställa att molnmiljöerna förblir stabila och säkra.

Den här guiden är utformad för Adobe Commerce Cloud-handlare och -partners som vill effektivisera sina patchningsprocesser, minska risken för korrigeringsrelaterade problem, förbättra miljöns säkerhet och stabilitet samt automatisera rutinkorrigeringsåtgärder.

## [!DNL CAPS] ämnen

* **[Åtkomst](access.md)**
* **[Arbetsflöde](workflow.md)**
* **[God praxis](best-practices.md)**
* **[Felsökning](troubleshooting.md)**

## Verktygsöversikt

* **Gränssnittet**
   * Tillgänglighet och statusvisning av korrigeringsfiler i realtid för specifika projekt- och miljökombinationer
   * Omfattande information om patchningsstatus som visar förlopp, fel och andra relevanta meddelanden
   * [!UICONTROL Patch Management Dashboard] för:
      * Visa tillgängliga korrigeringar
      * Använda korrigeringsfiler med en klickning
      * Återställa tidigare tillämpade korrigeringar
      * Övervaka status och resultat för korrigeringsåtgärd

* **Automatiserad korrigeringstjänst med strukturerat arbetsflöde**
   * **Preliminär kontroll** - Verifierar korrigeringens kompatibilitet och miljöberedskap
   * **Laga** - Tillämpar eller återställer korrigeringar automatiskt i integreringsmiljöer
   * **Validering** - Utför hälsokontroller och ser till att viktiga funktioner inte påverkas

* **Säkerhetsfunktioner**
   * Skapar miljöer med tillfällig integrering för testning
   * Verifierar korrigeringskompatibilitet före tillämpning
   * Ger automatisk återställning vid valideringsfel
   * Tillämpar korrigeringar på mappen `m2-hotfixes` med automatisk borttagning vid omversion

## Integreringar med Adobe Commerce Cloud

[!DNL CAPS] är helt integrerat med Adobe Commerce Cloud-infrastrukturen och fungerar sömlöst med dina befintliga molnmiljöer. Programmet utnyttjar molnbaserade funktioner för optimala prestanda, ger detaljerad loggning och övervakning samt är integrerat med supportverktygen i Adobe Commerce Cloud.

## Videosjälvstudie

Lär dig mer om Adobe Cloud Automated Patching Service och hur det här verktyget hjälper användarna att snabbt hitta och använda säkerhetsuppdateringar. I följande video visas hur du kommer åt den via SWAT-kontrollpanelen, väljer projekt och miljö samt lägger till korrigeringsfiler med ett enda klick.

>[!VIDEO](https://video.tv.adobe.com/v/3476247/?learn=on&enablevpops)

## Vanliga användningsområden

* **Säkerhetsuppdateringar** - Tillämpa snabbt viktiga säkerhetsuppdateringar
* **Patch rollback** - Återställ problematiska patchar som tillämpats med [!DNL CAPS] på ett säkert sätt
* **Säkerhetsöverensstämmelse** - Behåll säkerhetsstandarder med automatiserad korrigering
* **Driftstabilitet** - Säkerställ miljöstabilitet genom automatiserad validering
