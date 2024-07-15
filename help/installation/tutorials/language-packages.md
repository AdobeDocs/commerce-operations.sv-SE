---
title: Avinstallera språkpaket
description: Följ de här stegen för att avinstallera ett Adobe Commerce-språkpaket.
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Avinstallera språkpaket

I det här avsnittet beskrivs hur du avinstallerar ett eller flera språkpaket, inklusive språkpaketets kod från filsystemet. Du kan skapa säkerhetskopior först så att du kan återställa data senare.

Det här kommandot avinstallerar *endast* språkpaket som anges i `composer.json`, med andra ord språkpaket som tillhandahålls som Composer-paket. Om språkpaketet inte är ett Composer-paket måste du avinstallera det manuellt genom att ta bort språkpaketkoden från filsystemet.

Du kan återställa säkerhetskopior när som helst med kommandot [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

Kommandoanvändning:

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

Avinstallationskommandot för språkpaket utför följande åtgärder:

1. Kontrollerar om det finns beroenden. I så fall avslutas kommandot.

   Du kan undvika detta genom att antingen avinstallera alla beroende språkpaket samtidigt eller genom att avinstallera de beroende språkpaketen först.

1. Om `--backup code` anges säkerhetskopierar du filsystemet (exklusive `var` och `pub/static` kataloger) till `var/backups/<timestamp>_filesystem.tgz`
1. Tar bort språkpaketfiler från kodbasen med `composer remove`.
1. Rensar cachen.

Om du till exempel försöker avinstallera ett språkpaket som ett annat språkpaket är beroende av visas följande meddelande:

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

Ett alternativ är att avinstallera båda språkpaketen efter säkerhetskopiering av kodbasen:

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

Meddelanden som liknar följande:

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing vendorname/language-en_us (dev-master)
Removing Magento/LanguageEn_us
  - Removing vendorname/language-en_br (dev-master)
  - Removing vendorname/language-en_br (dev-master)
Writing lock file
Generating autoload files
```
