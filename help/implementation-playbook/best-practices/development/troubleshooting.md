---
title: Felsökning av bästa praxis
description: Lär dig hur du felsöker implementeringsproblem i Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Felsökning av bästa praxis

Följ dessa metodtips för effektiv felsökning av Adobe Commerce i molninfrastrukturfrågor.

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur

## God praxis

| Ärendetyp | God praxis | Resurs |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Distributionsproblem | **Följ vedertagna distributionsmetoder.** 13 % av supportbiljetterna innehåller distributionsproblem. De bästa metoderna har uppdaterats för att innehålla sätt att förhindra många av dessa orsaker. | [Bästa tillvägagångssätt för byggen och distribution](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) i utvecklardokumentationen. |
| Problem med att ordna webbplatser | **Använd felsökningsfunktionen för webbplats ned.** kroner kan vara långdragna och kan köra över varandra. De orsakar många avbrott och prestandaproblem. | [Felsökaren för att stänga av webbplats](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) och [Så här återställer du cron-jobb](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) i vår kunskapsbas för support. |
| Prestandaproblem | **Om du inte använder Adobe Commerce banner kan du inaktivera den.** När banderollen är aktiverad men inte används, används resurser för att söka till databasen när de inte behövs, vilket kommer att orsaka prestandaproblem. | [Inaktivera Adobe Commerce Banner-utdata för att förbättra prestanda](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) i vår kunskapsbas för support. |
| Sök efter problem | **MySQL-katalogsökmotorn har tagits bort i Adobe Commerce 2.4.0.** Du måste ha Elasticsearch-värdkonfiguration och konfigurerad innan du installerar version 2.4.0. Mer information finns i Installera och konfigurera Elasticsearch i utvecklardokumentationen. | [Konfigurera tjänsten Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html) i utvecklardokumentationen. |
| Anpassade fel | **Distribuera inte under högtider.** Om du lägger till och tar bort användare utlöses en distribution. | [Ingen driftsättning vid driftstopp](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) finns i utvecklardokumentationen. |
| Databasfel och databasproblem | **Databasproblem orsakar distribuering (problem med anslutning), prestanda och driftstopp.** Många innehåller fel eller otillräckligt databasutrymme. | [MariaDB-felkoder](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [Hantera lagringsutrymme](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (inklusive databas) i utvecklardokumentationen. |
| Konfigurationsproblem | **Indexera efter schema i stället för index vid Spara.** Det här är den mest effektiva indexeringskonfigurationen. Index vid Spara kommer att orsaka fullständig omindexering. | [Konfigurera indexerare](../../../configuration/cli/manage-indexers.md#configure-indexers) i utvecklardokumentationen. |
| Anpassade kodproblem | **Kontrollera dina långsamma frågeloggar för att se om det finns möjligheter att identifiera och eventuellt avsluta processer som tar för lång tid att slutföra.** Långsamma frågor kan orsaka databasdeadlocks, vilket kan leda till webbplatshämtningar och prestandaproblem. | [Kontrollerar långsamma frågor och processer som tar för lång tid i MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| Tilläggsproblem | **Använd endast verifierade tillägg på Commerce Marketplace.** | [Tillägg för Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Resursproblem | **Övervaka tillgängligt minne och utrymme och optimera lagring.** Du kan ha ledigt utrymme före en åtgärd som förbrukar stora resurser (till exempel distribution). Dålig optimering av fillagring (t.ex. för många stora bilder) kan också bidra till otillräckligt utrymme. Låga resurser orsakar prestandaproblem, driftstopp, driftstopp och driftsättningsfel. | [Hantera diskutrymme](https://devdocs.magento.com/cloud/project/manage-disk-space.html) i vår utvecklardokumentation. [Fillagringen är låg/slut och vissa sidinläsningar är långsamma](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) i vår kunskapsbas för support. |
