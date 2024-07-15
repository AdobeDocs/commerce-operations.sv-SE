---
title: Avinstallera teman
description: Följ de här stegen för att avinstallera ett Adobe Commerce-tema.
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Avinstallera teman

Innan du använder det här kommandot måste du känna till den relativa sökvägen till temat. Teman finns i en underkatalog till `<magento_root>/app/design/<area name>`. Du måste ange sökvägen till temat som börjar med området, som antingen är `frontend` (för butiksteman) eller `adminhtml` (för administratörsteman).

Sökvägen till Luma-temat som ingår i Adobe Commerce är till exempel `frontend/Magento/luma`.

Mer information om teman finns i [temastruktur](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## Översikt över avinstallation av teman

I det här avsnittet beskrivs hur du avinstallerar ett eller flera teman, och du kan även ta med temats kod från filsystemet. Du kan skapa säkerhetskopior först så att du kan återställa data senare.

Det här kommandot avinstallerar *endast* teman som anges i `composer.json`, med andra ord teman som tillhandahålls som Composer-paket. Om temat inte är ett Composer-paket måste du avinstallera det manuellt genom att:

* Uppdaterar nodinformationen `parent` i `theme.xml` för att ta bort referenser till temat.
* Tar bort temakod från filsystemet.

  [Mer information om temarv](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## Avinstallera teman

Kommandoanvändning:

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

Plats

* `{theme path}` är den relativa sökvägen till temat och börjar med områdesnamnet. Sökvägen till det tomma temat som ingår i Adobe Commerce är till exempel `frontend/Magento/blank`.
* `--backup-code` säkerhetskopierar kodbasen enligt beskrivningen i efterföljande stycken.
* `--clear-static-content` rensar genererade [statiska vyfiler](../../configuration/cli/static-view-file-deployment.md), vilket krävs för att statiska vyfiler ska visas korrekt.

Kommandot utför följande uppgifter:

1. Verifierar att de angivna temasökvägarna finns. Annars avslutas kommandot.
1. Verifierar att temat är ett Composer-paket. Annars avslutas kommandot.
1. Kontrollerar om det finns beroenden och avslutar kommandot om det finns några beroenden som inte uppfylls.

   Du kan undvika detta genom att antingen avinstallera alla teman samtidigt eller avinstallera dem beroende på tema först.

1. Verifierar att temat inte används. Om det används avslutas kommandot.
1. Verifierar att temat inte är basen för det virtuella temat. Om det är basen för ett virtuellt tema avslutas kommandot.
1. Placerar butiken i underhållsläge.
1. Om `--backup-code` anges säkerhetskopierar du kodbasen, exklusive katalogerna `pub/static`, `pub/media` och `var`.

   Namnet på säkerhetskopieringsfilen är `var/backups/<timestamp>_filesystem.tgz`

   Du kan återställa säkerhetskopior när som helst med kommandot [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

1. Tar bort teman från databastabellen `theme`.
1. Ta bort teman från kodbasen med `composer remove`.
1. Rensar cachen.
1. Rensar genererade klasser
1. Om `--clear-static-content` anges rensas [genererade statiska vyfiler](../../configuration/cli/static-view-file-deployment.md).

Om du till exempel försöker avinstallera ett tema som ett annat tema är beroende av visas följande meddelande:

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

Ett alternativ är att avinstallera båda temana samtidigt enligt följande för att säkerhetskopiera kodbasen:

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

Meddelanden som liknar följande:

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from database
Loading composer repositories with package information
Updating dependencies (including require-dev)
Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from Magento codebase
  - Removing ExampleCorp/sample-module-theme-depend (dev-master)
Removing ExampleCorp/SampleThemeDepend
  - Removing ExampleCorp/sample-module-theme (dev-master)
Removing ExampleCorp/SampleTheme
Writing lock file
Generating autoload files
Cache cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option.
Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>Om du vill avinstallera ett Admin-tema måste du även ta bort det från komponentens konfiguration för beroendeinjicering, `<component root directory>/etc/di.xml`.
