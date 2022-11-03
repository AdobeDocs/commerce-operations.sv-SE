---
title: Felsökning av bästa praxis
description: Lär dig hur du felsöker implementeringsproblem i Adobe Commerce.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# Felsökning av bästa praxis

Följ dessa metodtips för effektiv felsökning av Adobe Commerce i molninfrastrukturfrågor.

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur

## God praxis

| Ärendetyp | God praxis | Resurs |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Distributionsproblem | **Följ vedertagna rutiner för driftsättning.** 13 % av supportbiljetterna innehåller distributionsproblem. De bästa metoderna har uppdaterats för att innehålla sätt att förhindra många av dessa orsaker. | [Bästa tillvägagångssätt för byggen och driftsättningen](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) i vår dokumentation för utvecklare. |
| Problem med att ordna webbplatser | **Använd felsökaren för Plats ned.** Kronerna kan vara långa och kan överlappa varandra. De orsakar många avbrott och prestandaproblem. | [Felsökare för nedtryckt webbplats](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) och [Återställa cron-jobb](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) i vår kunskapsbas. |
| Prestandaproblem | **Om du inte använder Adobe Commerce banner kan du inaktivera den.** När banderollen är aktiverad men inte används, används resurser för att söka till databasen när de inte behövs, vilket kommer att orsaka prestandaproblem. | [Inaktivera Adobe Commerce Banner-utdata för att förbättra prestandan](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html i vår kunskapsbas för support. |
| Sök efter problem | **Sökmotorn för MySQL-katalogen har tagits bort i Adobe Commerce 2.4.0.** Du måste ha konfigurerat värddatorn Elasticsearch innan du kan installera version 2.4.0. Mer information finns i Installera och konfigurera Elasticsearch i utvecklardokumentationen. | [Konfigurera tjänsten Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html) i vår dokumentation för utvecklare. |
| Anpassade fel | **Driftsätt inte under högtider.** Om du lägger till och tar bort användare utlöses en distribution. | [Driftsättning utan driftstopp](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) i vår dokumentation för utvecklare. |
| Databasfel och databasproblem | **Databasproblem orsakar driftsättningsproblem (när det gäller postkrok), prestanda och driftstopp.** Många innebär fel eller otillräckligt databasutrymme. | [MariaDB-felkoder](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [Hantera lagringsutrymme](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (inklusive databas) i vår utvecklardokumentation. |
| Konfigurationsproblem | **Indexera efter schema i stället för index vid Spara.** Detta är den mest effektiva indexeringskonfigurationen. Index vid Spara kommer att orsaka fullständig omindexering. | [Konfigurera indexerare](../../../configuration/cli/manage-indexers.md#configure-indexers) i vår dokumentation för utvecklare. |
| Anpassade kodproblem | **Kontrollera dina långsamma frågeloggar för att se om det finns möjligheter att identifiera och eventuellt avsluta processer som tar för lång tid att slutföra.** Långsamma frågor kan orsaka databaslås, vilket kan leda till att webbplatsen laddas ned och prestandaproblem kan uppstå. | [Kontrollera långsamma frågor och processer som tar för lång tid i MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| Tilläggsproblem | **Använd endast verifierade tillägg på Commerce Marketplace.** | [Tillägg för Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Resursproblem | **Övervaka tillgängligt minne och tillgängligt utrymme och optimera lagringsutrymmet.** Du kan ha ledigt utrymme innan en åtgärd som förbrukar stora resurser (till exempel distribution). Dålig optimering av fillagring (t.ex. för många stora bilder) kan också bidra till otillräckligt utrymme. Låga resurser orsakar prestandaproblem, driftstopp, driftstopp och driftsättningsfel. | [Hantera diskutrymme](https://devdocs.magento.com/cloud/project/manage-disk-space.html) i vår dokumentation för utvecklare, [Fillagringen är låg/slut, vissa sidinläsningar tar lång tid](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) i vår kunskapsbas. |
