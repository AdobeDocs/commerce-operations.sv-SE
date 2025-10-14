---
title: Bästa tillvägagångssätt vid distribution av statiskt innehåll
description: Lär dig hur du undviker problem med statiskt innehåll som inte visas i din Adobe Commerce Store.
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Bästa tillvägagångssätt vid distribution av statiskt innehåll

I den här artikeln beskrivs de bästa sätten att distribuera statiskt innehåll (SCD) i Adobe Commerce för att undvika problem där statiskt innehåll inte skulle vara tillgängligt på din webbplats.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

* Adobe Commerce i molninfrastruktur
* Adobe Commerce lokalt

## God praxis

För att undvika problem med att statiskt innehåll inte är tillgängligt på din webbplats bör du följa dessa metodtips och se till att statiskt innehåll är konfigurerat och distribuerat korrekt:

1. Följ riktlinjerna för distribution:
   * Information om Adobe Commerce lokala versioner (alla versioner) finns i [Distributionsöversikt](../../../configuration/deployment/overview.md) i utvecklardokumentationen.
   * Information om Adobe Commerce molninfrastruktur (alla versioner) finns i [Driftsättningsprocess för molnet](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/deploy/process) och [Statiska strategier för innehållsdistribution](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/deploy/static-content) i utvecklardokumentationen.

1. För Adobe Commerce i molninfrastruktur (alla versioner) måste du se till att verktygen finns i den senaste versionen. Se: [Uppdatera versionen för verktygen](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) i utvecklardokumentationen.
1. För Adobe Commerce i molninfrastruktur (alla versioner) måste du se till att statiskt innehåll distribueras under byggfasen i stället för distributionsfasen. Se [Konfigurationshantering för butiksinställningar - Statisk innehållsdistribution &#x200B;](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure-store/store-settings#cloud-confman-scd-over) i utvecklardokumentationen.
1. Se till att du inte har några långvariga kronijobb och att du inte tar slut på några långvariga kroniprocesser. Långvariga cron-jobb kan ta upp CPU-resurser och potentiellt öka driftsättningstiden avsevärt.
1. För Adobe Commerce lokala (alla versioner) kontrollerar du att processen `php` i CLI har åtkomst till katalogen `pub/static`. Annars kan du råka ut för ett problem där en statisk innehållsdistribution inte kan skriva filer till den katalogen. Mer information: [Åtkomstbehörigheter för filsystem](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html?lang=sv-SE) i utvecklardokumentationen.
1. Kontrollera att katalogen `generated` inte är en delad katalog över byggen. Annars kan byggen misslyckas slumpmässigt. Mer information:
   * Adobe Commerce lokalt (alla versioner): [Teknisk information](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html?lang=sv-SE) i vår utvecklardokumentation.
   * Adobe Commerce i molninfrastruktur (alla versioner): [Distributionsprocess - fas 2: bygge](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#cloud-deploy-over-phases-build) i vår utvecklardokumentation.

1. Kontrollera din SCD-strategi. Strategin *quick* är standard. Mer information:
   * Adobe Commerce lokala (alla versioner): [Statiska distributionsstrategier för filer](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html?lang=sv-SE) i vår utvecklardokumentation.
   * Adobe Commerce i molninfrastruktur (alla versioner): [Distribuera variabler - SCD\_STRATEGY](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#scd_strategy) i vår utvecklardokumentation.

## Ytterligare information

I vår utvecklardokumentation:

* [Behållare för statiskt innehåll](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Statisk innehållssignering](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html?lang=sv-SE)
* [Distribuera variabler - STATIC\_CONTENT\_SYMLINK](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#static_content_symlink)
* [Distributionsflöde](../../../performance/deployment-flow.md)
* [Ingen driftsättning vid driftstopp](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime)
* [Optimera molndistributionen](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/deploy/optimization)
