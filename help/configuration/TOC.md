---
user-guide-title: Konfigurationshandbok
user-guide-description: Konfigurera Adobe Commerce programfunktioner och -tjänster.
feature: Configuration
source-git-commit: 1850301e0b7f1abbc54613209940dd63d16ef145
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# Konfigurationshandbok {#configuration-guide}

+ [Ökning](overview.md)
+ Allmänna inställningar {#setup}
   + [Programinitiering och bootstrap](bootstrap/initialization.md)
   + [Programlägen](bootstrap/application-modes.md)
   + [Bootstrap-parametrar](bootstrap/set-parameters.md)
   + [Profilering](bootstrap/mage-profiler.md)
   + [Sökvägar till baskatalog](bootstrap/mage-directory.md)
+ Distribution {#deployment}
   + [Distributionsöversikt](deployment/overview.md)
   + [Driftsättning av en dator](deployment/single-machine.md)
   + [Driftsättning av pipeline](deployment/technical-details.md)
   + [Förutsättningar](deployment/prerequisites.md)
   + [Installation av utvecklingssystem](deployment/development-system.md)
   + [Skapa systeminställningar](deployment/build-system.md)
   + [Installation av produktionssystem](deployment/production-system.md)
   + [Åtkomstbehörigheter för filsystem](deployment/file-system-permissions.md)
   + Exempel {#examples}
      + [Använda en delad konfiguration](deployment/example-shared-configuration.md)
      + [Använda CLI-kommandon](deployment/example-using-cli.md)
      + [Använda miljövariabler](deployment/example-environment-variables.md)
+ Cache {#cache}
   + [Översikt över cachelagring](cache/caching-overview.md)
   + [Cache-typer](cache/cache-types.md)
   + [Cachealternativ](cache/cache-options.md)
   + [L2-cache](cache/level-two-cache.md)
   + Redis {#redis}
      + [Konfigurera Redis](cache/config-redis.md)
      + [Använd Redis för standardcache](cache/redis-pg-cache.md)
      + [Använd Redis för sessionslagring](cache/redis-session.md)
   + Valkey {#valkey}
      + [Konfigurera Valkey](cache/config-valkey.md)
      + [Använd Valkey för standardcache](cache/valkey-pg-cache.md)
      + [Använd Valkey för sessionslagring](cache/valkey-session.md)
   + Varnish {#varnish}
      + [Finska - översikt](cache/config-varnish.md)
      + [Installera lack](cache/config-varnish-install.md)
   + [Webbserver](cache/config-varnish-server.md)
   + [Konfigurera Commerce-program](cache/configure-varnish-commerce.md)
   + [Avancerad lack-konfiguration](cache/config-varnish-advanced.md)
   + [Cacherensning](cache/use-varnish-cache.md)
   + [Cachelagra flera varianter](cache/use-multiple-varnish-cache.md)
   + [Verifiera lack-konfiguration](cache/config-varnish-final.md)
   + [Varnish ESI block](cache/use-varnish-esi.md)
   + [Cache för statiskt innehåll](cache/static-content-signing.md)
+ Kommandorad {#cli}
   + [Kommandoradsverktyg](cli/config-cli.md)
   + [Gemensamma kommandon](cli/common-cli-commands.md)
   + [Aktivera loggning](cli/enable-logging.md)
   + [Hantera cachen](cli/manage-cache.md)
   + [Hantera index](cli/manage-indexers.md)
   + [Konfigurera cron-jobb](cli/configure-cron-jobs.md)
   + [Kompilera kod](cli/code-compiler.md)
   + [Åtgärdsläge](cli/set-mode.md)
   + [Starta användare i meddelandekön](cli/start-message-queues.md)
   + [URN highlighter](cli/urn-highlighter.md)
   + [Beroenderapporter](cli/dependency-reports.md)
   + [Lokalisering](cli/localization.md)
   + Konfigurationshantering {#configuration-management}
      + [Ange värden](cli/set-configuration-values.md)
      + [Exportinställningar](cli/export-configuration.md)
      + [Importera data](cli/import-configuration.md)
   + Statisk vy {#static-view}
      + [Distributionsstrategier](cli/static-view-file-strategy.md)
      + [Distribuera statiska vyfiler](cli/static-view-file-deployment.md)
   + [Skapa symboler](cli/create-symlinks.md)
   + [Kör enhetstester](cli/unit-tests.md)
   + [Konvertera layoutfiler](cli/convert-layout-files.md)
   + [Generera data för prestandatestning](cli/generate-data.md)
   + [Kör supportprogram (endast Commerce)](cli/run-support-utilities.md)
+ Konfigurationsfiler {#files}
   + [Konfigurationsfiler för distribution](reference/deployment-files.md)
   + [Konfigurationstyper](reference/config-create-types.md)
   + [Modulfiler](reference/module-files.md)
   + [Modulutdata](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [gitignore](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ Konfigurationssökvägar {#paths}
   + [Allmänt](reference/config-reference-general.md)
   + [B2B-tillägg](reference/config-reference-b2b.md)
   + [Katalog](reference/config-reference-catalog.md)
   + [Kunder](reference/config-reference-customers.md)
   + [Betalningsmetoder](reference/config-reference-payment.md)
   + [Försäljning](reference/config-reference-sales.md)
   + [Tjänster](reference/config-reference-services.md)
   + [Känsliga och systemspecifika inställningar](reference/config-reference-sens.md)
   + [Åsidosätt konfigurationsinställningar](reference/override-config-settings.md)
+ Kronjobb {#crons}
   + [Kronjobb och grupper](cron/custom-cron.md)
   + [Anpassa crons-referens](cron/custom-cron-reference.md)
   + [Konfigurera ett anpassat cron-jobb](cron/custom-cron-tutorial.md)
+ Loggar {#logs}
   + [Anpassade loggar](logs/custom-logging.md)
   + [Logggränssnitt](logs/logger-interface.md)
   + [Loggdatabasaktivitet](logs/database-activity.md)
   + [Skriva till en anpassad loggfil](logs/custom-log-files.md)
+ Meddelandeköer {#message-queues}
   + [Ramverk för meddelandekö](queues/message-queue-framework.md)
   + [Hantera meddelandeköer](queues/manage-message-queues.md)
   + [Konfigurera Amazon MQ](queues/aws-mq.md)
   + [Konsumenter](queues/consumers.md)
+ Flera platser {#multi-sites}
   + [Flera webbplatser och vyer](multi-sites/ms-overview.md)
   + [Stegnings-ID för databasentitet](multi-sites/change-increment-id.md)
   + [Konfigurera i Admin](multi-sites/ms-admin.md)
   + [Konfigurera med Nginx](multi-sites/ms-nginx.md)
   + [Konfigurera med Apache](multi-sites/ms-apache.md)
+ Sökmotor {#search}
   + [Översikt över sökmotorer](search/overview-search.md)
   + [Konfigurera sökmotor](search/configure-search-engine.md)
   + [Filter med stoppord](search/search-stopwords.md)
+ Säkerhet {#security}
   + [Säkerhet - översikt](security/overview.md)
   + [Lösenordshashning](security/password-hashing.md)
   + [Cacheförgiftning](security/cache-poisoning.md)
   + [Secure cron PHP](security/secure-cron-php.md)
   + [Säkerhetstext](security/security-txt.md)
   + [Klicka på jacking Exploits](security/xframe-options.md)
+ Lagring {#storage}
   + [Databasprofilerare](storage/db-profiler.md)
   + Fjärrlagring {#remote-storage}
      + [Fjärrlagringsmodul](remote-storage/remote-storage.md)
      + [AWS S3-bucket](remote-storage/remote-storage-aws-s3.md)
      + [Storleksändring av bild](remote-storage/remote-storage-image-resize.md)
      + [Fjärrlagring för molnet](remote-storage/cloud-support.md)
   + Sessionslagring {#session-storage}
      + [Sessionslagringsplats](storage/sessions.md)
      + [cachelagrad för sessionslagring](storage/memcached.md)
      + [cachelagrad i CentOS](storage/memcache-centos.md)
      + [cachelagrad på Ubuntu](storage/memcache-ubuntu.md)
   + Dela databas {#split-db}
      + [Översikt över delad databas](storage/multi-master.md)
      + [Automatisk konfiguration](storage/multi-master-masterdb.md)
      + [Manuell konfiguration](storage/multi-master-manual.md)
      + [Verifiera delad databas](storage/multi-master-verify.md)
      + [Databasreplikering](storage/multi-master-replication.md)
      + [Återgå till en databas](storage/revert-split-database.md)
+ [Återgå till åtgärdsguiderna](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)