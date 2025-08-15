---
title: 'Hanterade varningar för Adobe Commerce: CPU-varningsmeddelanden'
description: Den här artikeln innehåller felsökningssteg när du får en CPU-varning för Adobe Commerce i  [!DNL New Relic]. Det krävs omedelbara åtgärder för att åtgärda problemet.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 0abcf21b-2ccf-42f5-8823-99282fccadcf
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# Hanterade varningar för Adobe Commerce: CPU-varningsmeddelanden

Den här artikeln innehåller felsökningssteg när du får en CPU-varning för Adobe Commerce i [!DNL New Relic]. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![CPU-varning](../../assets/managed-alerts/cpu-warning-magento-managed.png){width="500"}

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur Pro planarkitektur

## Problem

Du får en avisering i [!DNL New Relic] om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar har utvecklats av Adobe för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u> **Gör!** </u>

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera sajten i underhållsläge omedelbart om sajten inte svarar helt. Anvisningar om hur du gör detta finns i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i Commerce installationshandbok. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar om hur du gör detta finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) i Commerce installationshandbok.

<u>**Gör inte!**</u>

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare stress på CPU eller disk.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

1. Använd [[!DNL New Relic] APM:s transaktionssida](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) för att identifiera transaktioner med prestandaproblem:
   * Sortera transaktioner efter stigande [!DNL Apdex] poäng. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hänvisar till hur nöjda användarna är med svarstiden för dina webbprogram och tjänster. [Ett lågt [!DNL Apdex] poäng](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce) kan indikera en flaskhals (en transaktion med en högre svarstid). Vanligtvis är det databasen, [!DNL Redis] eller PHP. Anvisningar finns i [!DNL New Relic] [Visa transaktioner med högst [!DNL Apdex] missnöjd](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#apdex-dissat).
   * Sortera transaktioner efter högsta genomströmning, långsammast genomsnittlig svarstid, mest tidskrävande och andra tröskelvärden. Anvisningar finns i [[!DNL New Relic] Hitta specifika prestandaproblem](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Om du fortfarande har problem med att identifiera källan använder du [[!DNL New Relic] APM:s infrastruktursida](https://docs.newrelic.com/docs/infrastructure/infrastructure-data/infrastructure-ui-pages/infra-hosts-ui-page/) för att identifiera resurskrävande tjänster. Anvisningar om hur du gör detta finns på sidan [!DNL New Relic] [Värdar för infrastrukturövervakning: [!UICONTROL Processes tab]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Om du identifierar källan kommer SSH in i miljön för att undersöka ytterligare. Anvisningar om hur du gör detta finns i [SSH i din miljö](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) i handboken för Commerce on Cloud.
1. Om du fortfarande har svårt att identifiera källan:
   * Granska de senaste trenderna för att identifiera problem med de senaste koddistributionerna eller konfigurationsändringarna (t.ex. nya kundgrupper och stora förändringar i katalogen). Vi rekommenderar att du granskar de senaste sju dagarnas aktivitet för att se eventuella samband i koddistributioner eller ändringar.
   * Du bör kontrollera och inaktivera platta kataloger. Anvisningar om hur du gör detta finns i [Långsamma prestanda, långsamma och långvariga kron](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) i Commerce Support Knowledge Base.
   * Om du misstänker att du har en DDoS-attack kan du försöka blockera robottrafiken. Anvisningar finns i [Så här blockerar du skadlig trafik för Adobe Commerce på snabbnivå](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level) i Commerce Support Knowledge Base.
1. Om problemet verkar vara tillfälligt utför du åtgärder som att uppgradera eller försätter platsen i underhållsläge. Anvisningar om hur du gör detta finns i [Begär tillfällig storleksändring](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) i Commerce Support Knowledge Base och i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i Commerce installationshandbok. Om storleken på upp-sidan återställer webbplatsen till normal drift kan du begära en permanent uppstorlek (kontakta ditt Adobe-kontoteam) eller försöka återskapa problemet i din dedikerade mellanlagring genom att köra ett inläsningstest och optimera frågor, eller kod som minskar trycket på tjänsterna. Anvisningar om hur du gör detta finns i [Läs in och stresstestning](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) i Commerce on Cloud Guide.
