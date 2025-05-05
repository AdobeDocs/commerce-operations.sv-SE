---
user-guide-title: Installationshandbok
user-guide-description: Lär dig hur du installerar Adobe Commerce för lokala distributioner.
feature: Install
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---


# Installationshandbok {#installation-guide}

- [Ökning](overview.md)
- [Systemkrav](system-requirements.md)
- Förutsättningar {#prerequisites}
   - [Översikt](prerequisites/overview.md)
   - Filsystem {#file-system}
      - [Ökning](prerequisites/file-system/overview.md)
      - [Konfigurera behörigheter](prerequisites/file-system/configure-permissions.md)
   - Webbserver {#web-server}
      - [Nginx](prerequisites/web-server/nginx.md)
      - [Apache](prerequisites/web-server/apache.md)
   - Databasserver {#database-server}
      - [MySQL](prerequisites/database/mysql.md)
      - [Fjärranslutningar](prerequisites/database/mysql-remote.md)
   - Sökmotor {#search-engine}
      - [Ökning](prerequisites/search-engine/overview.md)
      - [AWS OpenSearch](prerequisites/search-engine/aws-opensearch.md)
      - [Konfigurera Nginx](prerequisites/search-engine/configure-nginx.md)
      - [Konfigurera Apache](prerequisites/search-engine/configure-apache.md)
   - [PHP](prerequisites/php-settings.md)
   - [Message Broker](prerequisites/rabbitmq.md)
   - [Säkerhet](prerequisites/security.md)
   - [Autentiseringsnycklar](prerequisites/authentication-keys.md)
   - [Adobe Commerce](prerequisites/commerce.md)
   - [Valfri programvara](prerequisites/optional-software.md)
- [Snabbstart](composer.md)
- [Avancerad installation](advanced.md)
- Post-installationssteg {#next-steps}
   - [Verifiera installationen](next-steps/verify.md)
   - [Konfigurera programmet](next-steps/configuration.md)
   - [Ange en mask (valfritt)](next-steps/set-umask.md)
   - Installera exempeldata (valfritt) {#sample-data}
      - [Ökning](sample-data/overview.md)
      - [Hämta Composer-paket](sample-data/composer-packages.md)
      - [Klona Git-databaser](sample-data/git-repositories.md)
      - [Ta bort eller uppdatera moduler](sample-data/remove-or-update.md)
- Tutorials {#tutorials}
   - [Säkerhetskopiera och återställa filsystemet, mediet och databasen](tutorials/backup.md)
   - [Kontrollera databasstatus](tutorials/database-status.md)
   - [Konfigurera beteende för meddelandekonsument](tutorials/message-consumers.md)
   - [Konfigurera låsprovidern](tutorials/lock-provider.md)
   - [Konfigurera butiken](tutorials/store.md)
   - [Skapa, redigera eller låsa upp administratörskonton](tutorials/admin.md)
   - [Skapa eller uppdatera distributionskonfigurationen](tutorials/deployment.md)
   - [Skapa databasschemat](tutorials/database.md)
   - [Visa eller ändra Admin URI](tutorials/admin-uri.md)
   - [Aktivera eller inaktivera underhållsläge](tutorials/maintenance-mode.md)
   - [Aktivera eller inaktivera moduler](tutorials/manage-modules.md)
   - [Installera ett tillägg](tutorials/extensions.md)
   - [Installera Commerce](tutorials/install.md)
   - [Förbättra säkerheten genom att ändra dokumentroten](tutorials/docroot.md)
   - [Avinstallera språkpaket](tutorials/language-packages.md)
   - [Avinstallera moduler](tutorials/uninstall-modules.md)
   - [Avinstallera eller installera om Commerce](tutorials/uninstall.md)
   - [Avinstallera teman](tutorials/themes.md)
   - [Uppgradera databasschemat](tutorials/database-upgrade.md)
- [Återgå till åtgärdsguiderna](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html?lang=sv-SE)
