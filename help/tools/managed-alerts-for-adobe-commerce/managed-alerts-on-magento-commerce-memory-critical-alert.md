---
title: 'Hanterade aviseringar om Adobe Commerce: Minneskritisk avisering'
description: Den här artikeln innehåller felsökningssteg när du får en minneskritisk avisering för Adobe Commerce i  [!DNL New Relic]. Det krävs omedelbara åtgärder för att åtgärda problemet.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: dedaf4eeb9403945ada1a90a82f4be45ff98ec4e
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 0%

---

# Hanterade aviseringar om Adobe Commerce: Minneskritisk avisering

Den här artikeln innehåller felsökningssteg när du får en minneskritisk avisering för Adobe Commerce i [!DNL New Relic]. Det krävs omedelbara åtgärder för att åtgärda problemet.

![Diskkritisk varning](../../assets/managed-alerts/memory-critical-magento-managed.png){width="500"}

## Berörda produkter och versioner

Alla versioner av Adobe Commerce på Cloud Infrastructure Pro-planarkitekturen.

## Problem

Du får en hanterad avisering i [!DNL New Relic] om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar har utvecklats av Adobe för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u> **Gör!** </u>

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar om hur du gör detta finns i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i Commerce installationsguide. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Stegen finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) i Commerce Installationshandbok.

<u>**Gör inte!**</u>

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare stress på CPU eller disk.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

Din webbplats kanske inte svarar (om du inte redan drabbas av ett avbrott i din webbplats) om du utför någon av åtgärderna&quot;Gör inte&quot; innan du har undersökt och löst orsaken till varningen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

>[!WARNING]
>
>Eftersom det här är en viktig varning rekommenderar vi att du slutför **steg 1** innan du försöker felsöka problemet (steg 2 och framåt).

1. Kontrollera om Adobe Commerce supportanmälan finns. Anvisningar finns i [Spåra supportärenden](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) i Commerce Support Knowledge Base. Supporten kan redan ha fått en [!DNL New Relic]-tröskelvärdesvarning, skapat en biljett och börjat arbeta med problemet. Om det inte finns någon biljett skapar du en. Biljetten ska ha följande information:
   * Kontaktorsak: välj **[!UICONTROL New Relic]** ALLVARLIGT meddelande mottaget
   * Beskrivning av aviseringen
   * [[!DNL New Relic] Incidentlänk](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Detta ingår i dina [hanterade aviseringar för Adobe Commerce](managed-alerts-for-magento-commerce.md).

1. Använd [[!DNL New Relic] APM:s infrastruktursida](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) för att identifiera de mest minnesintensiva processerna. Anvisningar om hur du gör detta finns på sidan [[!DNL New Relic] Värdar för infrastrukturövervakning: fliken Processer](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes):
   * Om tjänster som [!DNL Redis], MySQL eller PHP är de viktigaste källorna för minnesförbrukning kan du försöka med följande:
1. Kontrollera att du har de senaste versionerna. Nyare versioner kan ibland åtgärda minnesläckor. Om du inte har den senaste versionen bör du uppgradera. Anvisningar om hur du gör detta finns i [Ändra tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html?lang=sv-SE) i handboken för Commerce on Cloud.
1. Om problemet med tjänsten inte är versionsrelaterat kan du försöka med följande:
1. **MySQL**: Sök efter problem som långvariga frågor, odefinierade primärnycklar och dubblettindex. Anvisningar finns i [De vanligaste databasproblemen i Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=sv-SE) i Commerce Implementeringsspelningsbok.
1. **[!DNL Redis]**: Om [!DNL Redis] är den främsta källan för minnesförbrukning, [skickar du en supportanmälan](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).
1. **PHP**: Om PHP är den främsta källan till minnesförbrukning kan du granska processer som körs genom att köra `ps aufx` i CLI/Terminal. I slutversionen ser du de kroniska jobb och processer som körs. Kontrollera utdata för processernas körningstid. Om det finns en kron med lång exekveringstid kan kronen hänga. Felsökningssteg finns i [Långsam prestanda, kron som körs långsamt och långt](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) och [Kron-jobb som fastnat i körningsstatus](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) i Commerce Support Knowledge Base.
1. Om du fortfarande har problem med att identifiera orsaken till problemet kan du använda [[!DNL New Relic] APM:s transaktionssida](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) för att identifiera transaktioner med prestandaproblem:
   * Sortera transaktioner efter stigande [!DNL Apdex] poäng. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hänvisar till hur nöjda användarna är med svarstiden för dina webbprogram och tjänster. En [[!DNL Apdex score]](managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan indikera en flaskhals (en transaktion med en högre svarstid). Vanligtvis är det databasen, [!DNL &#x200B; Redis] eller PHP. Anvisningar finns i [[!DNL New Relic] Visa transaktioner med högst [!DNL Apdex] missnöjd](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortera transaktioner efter högsta genomströmning, den långsammaste genomsnittliga svarstiden, den mest tidskrävande och andra tröskelvärden. Anvisningar finns i [[!DNL New Relic] [Hitta specifika prestandaproblem]](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Om du fortfarande har problem med att identifiera problemet kan du använda [[!DNL New Relic] APM:s infrastruktursida](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/).
1. Om du inte kan identifiera orsaken till den ökade minnesanvändningen kan du granska aktuella trender för att identifiera problem med nyligen använda koddistributioner eller konfigurationsändringar (till exempel nya kundgrupper och stora ändringar i katalogen). Vi rekommenderar att du granskar de senaste 7 dagarnas aktivitet för att se om det finns några korrelationer i koddistributioner eller ändringar.
1. Om ovanstående metoder inte hjälper dig att hitta orsaken och/eller lösningen inom rimlig tid, begär du en uppgradering eller placerar platsen i underhållsläge om du inte redan har gjort det. Anvisningar finns i [Begära tillfällig storleksändring](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) i Commerce Support Knowledge Base och [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i Commerce Installationshandbok.
1. Om storleken på upp-sidan återställer webbplatsen till normal drift kan du begära en permanent uppstorlek (kontakta ditt Adobe-kontoteam), eller försöka återskapa problemet i din dedikerade mellanlagring genom att köra ett inläsningstest och optimera frågor, eller kod som minskar trycket på tjänsterna. Se [Läs in och stresstestning](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) i Commerce on Cloud Guide.
