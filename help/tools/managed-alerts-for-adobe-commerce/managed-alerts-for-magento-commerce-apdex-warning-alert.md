---
title: 'Hanterade aviseringar för Adobe Commerce: [!DNL Apdex] varningsmeddelande'
description: Den här artikeln innehåller felsökningssteg för när du får en [!DNL Apdex] varningsvarning för Adobe Commerce in [!DNL New Relic]. The [!DNL Apdex] score mäter hur nöjda användarna är med svarstiden för webbprogram och -tjänster. Det krävs omedelbara åtgärder för att åtgärda problemet.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 0e1e0e001cfe07d7404b4dd9f53c1608df1e0c25
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---


# Hanterade aviseringar för Adobe Commerce: [!DNL Apdex] varning

Den här artikeln innehåller felsökningssteg för när du får en [!DNL Apdex]-varning för Adobe Commerce i [!DNL New Relic]. [!DNL Apdex]-poängen mäter hur nöjda användarna är med svarstiden för webbprogram och tjänster. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![apdex-varning](../../assets/managed-alerts/apdex-warning-magento-managed.png){width="500"}

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur Pro planarkitektur
* Adobe Commerce om molninfrastruktur - arkitektur för Starter-plan

## Problem

Du får en hanterad avisering i [!DNL New Relic] om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar har utvecklats av Adobe för att ge säljarna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u> **Gör!** </u>

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar om hur du gör detta finns i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i Commerce installationshandbok. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar om hur du gör detta finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) i Commerce installationshandbok.

<u>**Gör inte!**</u>

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare stress på CPU eller disk.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

1. Identifiera källan till problemet genom att använda [[!DNL New Relic APM's] transaktionssidan](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) för att identifiera transaktioner med prestandaproblem:
   * Sortera transaktioner efter stigande [!DNL Apdex scores]. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hänvisar till hur nöjda användarna är med svarstiden för dina webbprogram och tjänster. En [låg [!DNL Apdex] poäng](managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan indikera en flaskhals (en transaktion med en högre svarstid). Vanligtvis är det databasen, [!DNL Redis] eller PHP. Anvisningar finns i [[!DNL New Relic] Visa transaktioner med högst [!DNL Apdex] missnöjd](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortera transaktioner efter högsta genomströmning, den långsammaste genomsnittliga svarstiden, den mest tidskrävande och andra tröskelvärden. Anvisningar finns i [[!DNL New Relic] Hitta specifika prestandaproblem](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Använd [[!DNL New Relic] APM:s infrastruktursida](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) för att identifiera resurskrävande processer. Anvisningar finns på sidan [[!DNL New Relic] Värdar för infrastrukturövervakning: [!UICONTROL Processes] tab](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Om tjänster som [!DNL Redis] eller MySQL är den främsta källan för minnesförbrukning kan du försöka med följande:
   * Kontrollera att du har den senaste versionen. Nyare versioner kan ibland åtgärda minnesläckor. Om du inte har den senaste versionen bör du uppgradera. Anvisningar om hur du gör detta finns i [Ändra tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) i handboken för Commerce on Cloud.
1. Om problemet inte orsakas av tjänstversioner:
   * Kontrollera om det finns andra MySQL-problem, som långvariga frågor, odefinierade primärnycklar och dubblerade index. Anvisningar finns i [De vanligaste databasproblemen i Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) i Commerce Implementeringsspelningsbok.
   * Sök efter andra PHP-problem. Granska pågående processer genom att köra `ps aufx` i CLI/Terminal. I slutversionen ser du de kroniska jobb och processer som körs. Kontrollera utdata för processernas körningstid. Om det finns en kron med lång exekveringstid kan kronen hänga. Felsökningssteg finns i [Långsamma prestanda, långsamma och långvariga kroner](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) och [Kronjobb som fastnat i körningsstatus](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) i Commerce Support Knowledge Base.
1. När en potentiell källa till problemet har identifierats kan SSH ta sig in i miljön för att undersöka saken ytterligare. Anvisningar om hur du gör detta finns i [SSH i din miljö](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) i handboken för Commerce on Cloud.
1. Om du fortfarande har svårt att identifiera källan bör du granska de senaste trenderna för att identifiera problem med nyligen använda koddistributioner eller konfigurationsändringar (till exempel nya kundgrupper och stora ändringar i katalogen). Vi rekommenderar att du granskar de senaste sju dagarnas aktivitet för att se eventuella samband i koddistributioner eller ändringar.
1. Om du inte kan hitta en lösning inom rimlig tid kan du begära en uppgradering eller placera platsen i underhållsläge om du inte redan har gjort det. Anvisningar om hur du gör detta finns i [Begär tillfällig storleksändring](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) i Commerce Support Knowledge Base och i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i Commerce installationshandbok.
1. Om [upsize](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) återställer webbplatsen till normal drift kan du begära en permanent uppstorlek (kontakta ditt Adobe-kontoteam) eller försöka återskapa problemet i din dedikerade mellanlagring genom att köra ett inläsningstest och optimera frågor eller kod som minskar trycket på tjänsterna. Läs mer i [Läs in och stresstestning](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) i Commerce on Cloud Guide.
