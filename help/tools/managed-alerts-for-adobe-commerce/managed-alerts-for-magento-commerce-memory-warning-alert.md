---
title: 'Hanterade aviseringar för Adobe Commerce: Minnesvarning'
description: Den här artikeln innehåller felsökningssteg för när du får en minnesvarning för Adobe Commerce i  [!DNL New Relic]. Det krävs omedelbara åtgärder för att åtgärda problemet.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 0910a431-bf2c-469e-81e2-92c8d9be3249
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Hanterade aviseringar för Adobe Commerce: Minnesvarning

Den här artikeln innehåller felsökningssteg för när du får en minnesvarning för Adobe Commerce i [!DNL New Relic]. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![minnesvarning](../../assets/managed-alerts/memory-warning-magento-managed.png){width="500"}

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur Pro planarkitektur

## Problem

Du får en avisering i [!DNL New Relic] om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar har utvecklats av Adobe Commerce för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u>**Gör!**</u>:

* Vi rekommenderar att du avbryter alla schemalagda distributioner tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar om hur du gör detta finns i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i Commerce installationshandbok. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar om hur du gör detta finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) i Commerce installationshandbok.

<u>**Gör inte!**</u>:

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare stress på CPU eller disk.
* Utför några större administrativa uppgifter (dvs. administratören, import/export av data).
* Rensa cachen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

1. Använd [[!DNL New Relic] APM:s infrastruktursida](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) för att identifiera de mest minnesintensiva processerna. Anvisningar finns i [[!DNL New Relic] [sidan Värdar för infrastrukturövervakning: [!UICONTROL Processes] tab]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes). Om tjänster som [!DNL Redis] eller MySQL är den främsta källan för minnesförbrukning kan du försöka med följande:

   * Kontrollera att du har den senaste versionen. Nyare versioner kan ibland åtgärda minnesläckor. Om du inte har den senaste versionen bör du uppgradera. Anvisningar om hur du gör detta finns i [Ändra tjänster](https://experienceleague.adobe.com/sv/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) i handboken för Commerce on Cloud.
   * Om du fortfarande inte kan identifiera källan till ökad minnesförbrukning söker du efter MySQL-problem som långvariga frågor, odefinierade primärnycklar och dubblerade index. Anvisningar finns i [De vanligaste databasproblemen i Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=sv-SE) i Commerce Implementeringsspelningsbok.
   * Om det inte finns några MySQL-problem söker du efter PHP-problem. Granska pågående processer genom att köra `ps aufx` i CLI/Terminal. I slutversionen ser du vilka kroniska jobb och processer som körs. Kontrollera utdata för processernas körningstid. Om det finns en kron med lång exekveringstid kan kronen hänga. Se [Låga prestanda, långsamma och långvariga kroner](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) och [Cron-jobb som fastnat i körningsstatus](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) i Commerce Support Knowledge Base för felsökning.

1. Om du fortfarande har problem med att identifiera orsaken till problemet kan du använda [[!DNL New Relic] APM:s transaktionssida](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) för att identifiera transaktioner med prestandaproblem:

   * Sortera transaktioner efter stigande [!DNL Apdex] poäng. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hänvisar till hur nöjda användarna är med svarstiden för dina webbprogram och tjänster. En [låg [!DNL Apdex] poäng](managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan indikera en flaskhals (en transaktion med en högre svarstid). Vanligtvis är det databasen, [!DNL Redis] eller PHP. Anvisningar finns i New Relic [Visa transaktioner med högst [!DNL Apdex] missnöjd](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortera transaktioner efter högsta genomströmning, den långsammaste genomsnittliga svarstiden, den mest tidskrävande och andra tröskelvärden. Anvisningar finns i [[!DNL New Relic] Hitta specifika prestandaproblem](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Om du fortfarande har problem med att identifiera problemet kan du använda [[!DNL New Relic] APM:s infrastruktursida](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/).

1. Om du inte kan identifiera orsaken till den ökade minnesanvändningen kan du granska aktuella trender för att identifiera problem med nyligen använda koddistributioner eller konfigurationsändringar (till exempel nya kundgrupper och stora ändringar i katalogen). Vi rekommenderar att du granskar de senaste sju dagarnas aktivitet för att se eventuella samband i koddistributioner eller ändringar.

1. Om ovanstående metoder inte hjälper dig att hitta orsaken och/eller lösningen inom rimlig tid, begär du en uppgradering eller placerar platsen i underhållsläge om du inte redan har gjort det. Anvisningar finns i [Begära tillfällig storleksändring](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) i Commerce Support Knowledge Base och [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i Commerce installationshandbok.

1. Om storleken på upp-sidan återställer webbplatsen till normal drift kan du begära en permanent uppstorlek (kontakta ditt Adobe-kontoteam), eller försöka återskapa problemet i din dedikerade mellanlagring genom att köra ett inläsningstest och optimera frågor, eller kod som minskar trycket på tjänsterna. Läs mer i [Läs in och stresstestning](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) i Commerce on Cloud Guide.
