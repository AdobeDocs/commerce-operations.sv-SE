---
title: 'Hanterade aviseringar om Adobe Commerce: CPU Critical Alert'
description: Den här artikeln innehåller felsökningssteg när du får en viktig CPU-varning för Adobe Commerce i  [!DNL New Relic]. Det krävs omedelbara åtgärder för att åtgärda problemet.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: b30266b8f39989103ca70fa3e57ade8cea9b0dcc
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Hanterade aviseringar om Adobe Commerce: CPU Critical Alert

Den här artikeln innehåller felsökningssteg när du får en viktig CPU-varning för Adobe Commerce i [!DNL New Relic]. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![Diskkritisk varning](../../assets/managed-alerts/cpu-critical-magento-managed.png){width="500"}

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur Pro planarkitektur

## Problem

Du får en hanterad avisering i [!DNL New Relic] om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar har utvecklats av Adobe Commerce för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u>**Gör!**</u>:

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar om hur du gör detta finns i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i Commerce installationshandbok. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar om hur du gör detta finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) i Commerce installationshandbok.

<u>**Gör inte!**</u>:

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare stress på CPU eller disk.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

Din webbplats kanske inte svarar (om du inte redan har ett avbrott i din webbplats) om du utför någon av åtgärderna&quot;Gör inte&quot; innan du har undersökt och löst orsaken till varningen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

>[!WARNING]
>
>Eftersom det här är en viktig varning rekommenderar vi att du slutför **steg 1** innan du försöker felsöka problemet (steg 2 och framåt).

Kontrollera om Adobe Commerce supportanmälan finns. Anvisningar finns i [Spåra supportärenden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) i Commerce Support Knowledge Base. Supporten kan ha fått en [!DNL New Relic]-tröskelvärdesvarning, skapat en biljett och börjat arbeta med problemet. Om det inte finns någon biljett skapar du en. Biljetten ska ha följande information:

1. Kontaktorsak: välj **[!UICONTROL New Relic CRITICAL alert received]**.
1. Beskrivning av aviseringen.
1. [[!DNL New Relic] Incidentlänk](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Detta ingår i dina [hanterade aviseringar för Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Använd [[!DNL New Relic] APM:s transaktionssida](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) för att identifiera transaktioner med prestandaproblem:
   * Sortera transaktioner efter stigande Apdex-poäng. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hänvisar till hur nöjda användarna är med svarstiden för dina webbprogram och tjänster. En [låg [!DNL Apdex] poäng](managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan indikera en flaskhals (en transaktion med en högre svarstid). Vanligtvis är den relaterad till databasen, [!DNL Redis] eller PHP. Anvisningar finns i New Relic [Visa transaktioner med högst [!DNL Apdex] missnöjd](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortera transaktioner efter högsta genomströmning, långsammast genomsnittlig svarstid, mest tidskrävande och andra tröskelvärden. Anvisningar finns i [!DNL New Relic] [Hitta specifika prestandaproblem](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Om du fortfarande har problem med att identifiera källan använder du [[!DNL New Relic] APM:s infrastruktursida](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) för att identifiera resurskrävande tjänster. Anvisningar om hur du gör detta finns på sidan [!DNL New Relic] [Värdar för infrastrukturövervakning: fliken Processer ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Om du identifierar källan kommer SSH in i miljön för att undersöka ytterligare. Anvisningar om hur du gör detta finns i [SSH i din miljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) i handboken för Commerce on Cloud.
1. Om du fortfarande har svårt att identifiera källan:
   * Granska de senaste trenderna för att identifiera problem med de senaste koddistributionerna eller konfigurationsändringarna (t.ex. nya kundgrupper och stora förändringar i katalogen). Vi rekommenderar att du granskar de senaste sju dagarnas aktivitet för att se eventuella samband i koddistributioner eller ändringar.
   * Du bör kontrollera och inaktivera platta kataloger. Anvisningar om hur du gör detta finns i [Långsamma prestanda, långsamma och långvariga kron](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) i Commerce Support Knowledge Base.
   * Om du misstänker att du har en DDoS-attack kan du försöka blockera robottrafiken. Anvisningar finns i [Så här blockerar du skadlig trafik för Adobe Commerce i molninfrastruktur på snabbnivå](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level) i Commerce Support Knowledge Base.
1. Om problemet verkar vara tillfälligt utför du åtgärder som att uppgradera eller försätter platsen i underhållsläge. Anvisningar finns i [Begära tillfällig storleksändring](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) i Commerce Support Knowledge Base och [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i Commerce installationshandbok. Om storleken på upp-sidan återställer webbplatsen till normal drift kan du begära en permanent uppstorlek (kontakta ditt Adobe-kontoteam) eller försöka återskapa problemet i din dedikerade mellanlagring genom att köra ett inläsningstest och optimera frågor eller kod som minskar trycket på tjänsterna. Anvisningar finns i [Läs in och stresstestning](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) i Commerce i molnguiden.
