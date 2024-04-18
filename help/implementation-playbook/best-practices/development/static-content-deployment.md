---
title: Bästa tillvägagångssätt vid distribution av statiskt innehåll
description: Lär dig hur du undviker problem med statiskt innehåll som inte visas i din Adobe Commerce Store.
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
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
   * Information om Adobe Commerce lokala versioner (alla versioner) finns på [Distributionsöversikt](../../../configuration/deployment/overview.md) i vår dokumentation för utvecklare.
   * Information om Adobe Commerce om molninfrastruktur (alla versioner) finns på [Driftsättningsprocess i molnet](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) och [Strategier för distribution av statiskt innehåll](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) i vår dokumentation för utvecklare.

1. För Adobe Commerce i molninfrastruktur (alla versioner) måste du se till att verktygen finns i den senaste versionen. Se: [Uppdatera versionen av verktygen](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) i vår dokumentation för utvecklare.
1. För Adobe Commerce i molninfrastruktur (alla versioner) måste du se till att statiskt innehåll distribueras under byggfasen i stället för distributionsfasen. Se: [Konfigurationshantering för lagringsinställningar - prestanda för statisk innehållsdistribution](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) i vår dokumentation för utvecklare.
1. Se till att du inte har några långvariga kronijobb och att du inte tar slut på några långvariga kroniprocesser. Långvariga cron-jobb kan ta upp processorresurser och potentiellt öka driftsättningstiden avsevärt.
1. För Adobe Commerce lokalt (alla versioner) kontrollerar du att `php` i CLI har tillgång till `pub/static` katalog. Annars kan du råka ut för ett problem där en statisk innehållsdistribution inte kan skriva filer till den katalogen. Mer information: [Åtkomstbehörigheter för filsystem](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) i vår dokumentation för utvecklare.
1. Kontrollera `generated` katalogen är inte en delad katalog över byggen, annars kan byggen misslyckas slumpmässigt. Mer information:
   * Lokal Adobe Commerce (alla versioner): [Teknisk information](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) i vår dokumentation för utvecklare.
   * Adobe Commerce om molninfrastruktur (alla versioner): [Driftsättningsprocess - fas 2: bygge](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) i vår dokumentation för utvecklare.

1. Kontrollera din SCD-strategi. The *snabbhet* strategi är standard. Mer information:
   * Lokal Adobe Commerce (alla versioner): [Distributionsstrategier för statiska filer](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) i vår dokumentation för utvecklare.
   * Adobe Commerce om molninfrastruktur (alla versioner): [Distribuera variabler - SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) i vår dokumentation för utvecklare.

## Ytterligare information

I vår utvecklardokumentation:

* [Behållare för statiskt innehåll](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Statisk innehållssignering](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [Distribuera variabler - STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [Distributionsflöde](../../../performance/deployment-flow.md)
* [Driftsättning utan driftstopp](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [Optimera molndistributionen](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)
