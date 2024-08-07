---
user-guide-title: Implementera spelningsbok
user-guide-description: Läs om strategier för att planera och implementera en framgångsrik Adobe Commerce-webbplats.
mini-toc-levels: 3
source-git-commit: 36a2a86cbafab1e4913573b1c8431524ba43dc6a
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# Implementera spelningsbok {#implementation-playbook}

- [Ökning](overview.md)
- Commerce {#intro}
   - [Om Adobe Commerce](intro/about-commerce.md)
   - [Principer för plattformsutveckling](intro/platform-development.md)
- Projektomfång {#project-scope}
   - [Kunskap är makt](project-scope/knowledge.md)
   - [Viktiga intressenter](project-scope/key-stakeholders.md)
   - [Process och tidslinje](project-scope/process-timeline.md)
   - [Leveranser](project-scope/deliverables.md)
   - [Kontrollistor för krav](project-scope/requirement-checklists.md)
- Utveckling {#development}
   - [plattformsverktyg](development/platform-tools.md)
   - [Projekthanteringsverktyg](development/project-management-tools.md)
   - [Metod för projektgenomförande](development/delivery.md)
   - [Kvalitetskontroll](development/quality-control.md)
- Planering och styrning {#planning}
   - [Leverans och planering](planning/delivery.md)
   - [Ansvar och ägarskap](planning/ownership.md)
   - [Projektstyrning](planning/governance.md)
- Arkitektur och integreringar {#architecture}
   - [Företagsreferens](architecture/enterprise-blueprint.md)
   - Global referensarkitektur {#global-reference-architecture}
      - [Ökning](architecture/global-reference/overview.md)
      - [Exempel](architecture/global-reference/examples.md)
      - Composer-utveckling {#composer}
         - [Ökning](architecture/global-reference/composer/overview.md)
         - [Projektstruktur](architecture/global-reference/composer/project-structure.md)
         - [Tips och råd](architecture/global-reference/composer/tips-and-tricks.md)
- Infrastruktur och distribution {#infrastructure}
   - [Ökning](infrastructure/overview.md)
   - Självvärd {#self-hosting}
      - [Ökning](infrastructure/self-hosting/overview.md)
      - [Lokal infrastruktur](infrastructure/self-hosting/on-premises.md)
      - [Säkerhetskoncept](infrastructure/self-hosting/security-concepts.md)
      - [Övervaka telemetri och verktyg](infrastructure/self-hosting/monitoring-tools.md)
      - [idéer om katastrofåterställning](infrastructure/self-hosting/disaster-recovery-ideas.md)
      - [Prestandapstips](infrastructure/self-hosting/performance-tips.md)
   - Molninfrastruktur {#cloud}
      - [Ökning](infrastructure/cloud/overview.md)
      - [Regioner](infrastructure/cloud/regions.md)
      - [Technologies](infrastructure/cloud/technology.md)
      - [Säkerhet och efterlevnad](infrastructure/cloud/security.md)
   - Prestandaoptimering {#performance}
      - [Vanliga problem](infrastructure/performance/optimization.md)
      - [Benchmarks](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- Starta beredskap {#launch}
   - [Ökning](launch/overview.md)
   - [Steg före start](launch/pre-launch-steps.md)
   - [Starta steg](launch/launch-steps.md)
   - [Steg för att starta Post](launch/post-launch-steps.md)
- Underhåll och support {#maintenance}
   - [Ökning](maintenance/overview.md)
   - [Adobe Managed Services](maintenance/adobe-managed-services.md)
- God praxis {#best-practices}
   - [Ökning](best-practices/phases.md)
   - Planerar {#planning}
      - [Ökning](best-practices/planning/overview.md)
      - [Kataloghantering](best-practices/planning/catalog-management.md)
      - [Konfiguration av platser, butiker och butiksvy](best-practices/planning/sites-stores-store-views.md)
      - [Rapporteringskonfiguration](best-practices/planning/reporting-configuration.md)
      - [Databaskonfiguration för &#x200B; i molnet](best-practices/planning/database-on-cloud.md)
      - [MySQL-konfiguration](best-practices/planning/mysql-configuration.md)
      - [Redis-tjänstkonfiguration](best-practices/planning/redis-service-configuration.md)
      - [OPcache-minnesstorlek](best-practices/planning/opcache-memory-size.md)
      - [Cachestorlek för Realpath](best-practices/planning/realpath-cache-size.md)
      - [Tillägg](best-practices/planning/extensions.md)
      - [Eskaleringar av partners](best-practices/planning/partner-escalation.md)
      - [Betalningslagringsbearbetning](best-practices/planning/payment-processing-storage.md)
   - Utveckling {#development}
      - [Ökning](best-practices/development/overview.md)
      - [Allmän bästa praxis](best-practices/development/general.md)
      - [Kodhantering](best-practices/development/code-management.md)
      - [Kodgranskning](best-practices/development/code-review.md)
      - [Felsökning](best-practices/development/debugging.md)
      - [Undantagshantering](best-practices/development/exception-handling.md)
      - [Git-förgreningar](best-practices/development/git-branching.md)
      - [Ändra storlek på katalogbild](best-practices/development/catalog-image-resizing.md)
      - [Bildoptimering](best-practices/development/image-optimization.md)
      - [Felsökning](best-practices/development/troubleshooting.md)
      - [Optimera CSS- och JS-filer](best-practices/development/optimize-css-js-files.md)
      - [Privata innehållsblock](best-practices/development/private-content-block-configuration.md)
      - [Statisk innehållsdistribution](best-practices/development/static-content-deployment.md)
      - [Ändra databastabeller](best-practices/development/modifying-core-and-third-party-tables.md)
      - [Ändrar kärnkod och tredjepartskod](best-practices/development/modifying-core-and-third-party-code.md)
   - Starta {#launch}
      - [Ökning](best-practices/launch/overview.md)
      - [Konfigurera webbcrawler](best-practices/launch/robots-txt.md)
      - [Skydda er webbplats och infrastruktur](best-practices/launch/security-best-practices.md)
   - Underhåll {#maintenance}
      - [Ökning](best-practices/maintenance/overview.md)
      - [Prestanda för granskningsfronder](best-practices/maintenance/frontend-performance.md)
      - [Optimera backend-prestanda](best-practices/maintenance/backend-performance.md)
      - [Indexerarkonfiguration](best-practices/maintenance/indexer-configuration.md)
      - [Lappa i stor skala](best-practices/maintenance/patching-at-scale.md)
      - [Beställningsbehandling](best-practices/maintenance/order-processing-configuration.md)
      - [Åtgärda problem med databasprestanda](best-practices/maintenance/resolve-database-performance-issues.md)
      - [Svara på säkerhetsincidenter](best-practices/maintenance/respond-to-security-incident.md)
      - [Schemalägga administratörsuppdateringar på produktionsplatser](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [Uppdatera tjänster](best-practices/maintenance/update-services.md)
      - [Checklista för uppgradering](best-practices/maintenance/upgrade-checklist.md)
      - [Krav för uppgradering av MariaDB](best-practices/maintenance/mariadb-upgrade.md)
- [Återgå till åtgärdsguiderna](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
