---
title: Avinstallera moduler
description: Följ de här stegen för att avinstallera en Adobe Commerce-modul.
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Avinstallera moduler

I det här avsnittet beskrivs hur du avinstallerar en eller flera moduler. Under avinstallationen kan du ta bort modulens kod, databasschema och databasdata. Du kan skapa säkerhetskopior först så att du kan återställa data senare.

Du bör endast avinstallera en modul om du är säker på att du inte kommer att använda den. I stället för att avinstallera en modul kan du inaktivera den enligt beskrivningen i [Aktivera eller inaktivera moduler](manage-modules.md).

>[!NOTE]
>
>Det här kommandot kontrollerar att endast beroenden som har deklarerats i filen `composer.json` har deklarerats. Om du avinstallerar en modul som _inte_ har definierats i filen `composer.json` avinstalleras modulen med det här kommandot utan att någon kontroll av beroenden görs. Det här kommandot tar _inte_ bort modulens kod från filsystemet. Du måste använda filsystemverktyg för att ta bort modulens kod (till exempel `rm -rf <path to module>`). Som ett alternativ kan du [inaktivera](manage-modules.md) moduler som inte är Composer.

Kommandoanvändning:

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

Där `{ModuleName}` anger modulnamnet i formatet `<VendorName>_<ModuleName>`. Kundmodulens namn är till exempel `Magento_Customer`. Om du vill visa en lista med modulnamn anger du `magento module:status`

Avinstallationskommandot för modulen utför följande åtgärder:

1. Verifierar att de angivna modulerna finns i kodbasen och är paket som har installerats av Composer.

   Det här kommandot fungerar _endast_ med moduler definierade som Composer-paket.

1. Kontrollerar om det finns beroenden till andra moduler och avslutar kommandot om det finns några beroenden som inte uppfylls.

   Du kan undvika detta genom att antingen avinstallera alla moduler samtidigt eller avinstallera de beroende modulerna först.

1. Begär bekräftelse att fortsätta.
1. Placerar butiken i underhållsläge.
1. Bearbetar följande kommandoalternativ.

   | Alternativ | Betydelse | Säkerhetskopians filnamn och plats |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | Säkerhetskopierar filsystemet (exklusive `var`- och `pub/static`-kataloger). | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | Säkerhetskopierar katalogen pub/media. | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | Säkerhetskopierar databasen. | `var/backups/<timestamp>_db.gz` |

1. Om `--remove-data` anges tar du bort databasschemat och data som definierats i modulens `Uninstall` -klasser.

   Anropar metoden `uninstall` i klassen `Uninstall` för varje angiven modul som ska avinstalleras. Den här klassen måste ärva från [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. Tar bort angivna moduler från databastabellen `setup_module`.
1. Tar bort angivna moduler från modullistan i [distributionskonfigurationen](../../configuration/reference/deployment-files.md).
1. Tar bort kod från kodbasen med `composer remove`.

   >[!NOTE]
   >
   >Om du avinstallerar modulen _always_ körs `composer remove`. Alternativet `--remove-data` tar bort databasdata och schema som definieras av modulens `Uninstall`-klass.

1. Rensar cachen.
1. Uppdateringsgenererade klasser.
1. Om `--clear-static-content` anges rensas [genererade statiska vyfiler](../../configuration/cli/static-view-file-deployment.md).
1. Tar arkivet ur underhållsläge.

Om du till exempel försöker avinstallera en modul som en annan modul är beroende av visas följande meddelande:

```
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

Ett alternativ är att avinstallera båda modulerna efter säkerhetskopiering av modulens filsystem, `pub/media` filer och databastabeller, men _inte_ tar bort modulens databasschema eller data:

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

Meddelanden som liknar följande:

```
You are about to remove code and/or database tables. Are you sure?[y/N]y
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Media backup is starting...
Media backup filename: 1435261098_filesystem_media.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Media backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_media.tgz
[SUCCESS]: Media backup completed successfully.
DB backup is starting...
DB backup filename: 1435261098_db.gz (The archive can be uncompressed with 7-Zip on Windows systems)
DB backup path: /var/www/html/magento2/var/backups/1435261098_db.gz
[SUCCESS]: DB backup completed successfully.
You are about to remove a module(s) that might have database data. Remove the database data manually after uninstalling, if desired.
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module registry in database
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module list in deployment configuration
Removing code from Magento codebase:
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing magento/sample-module-modifycontent (1.0.0)
Removing Magento/SampleModifycontent
  - Removing magento/sample-module-minimal (1.0.0)
Removing Magento/SampleMinimal
Writing lock file
Generating autoload files
Cache cleared successfully.
Generated classes cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option. Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>Fel visas om du försöker avinstallera en modul som är beroende av en annan modul. I så fall kan du inte avinstallera en modul. Du måste avinstallera båda.

## Återställ filsystemet, databasen eller mediefilerna

Använd följande kommando om du vill återställa kodbasen till det läge där du säkerhetskopierade den:

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

Där `<filename>` är namnet på säkerhetskopieringsfilen i katalogen `<app_root>/var/backups`. Om du vill visa en lista över säkerhetskopierade filer anger du `magento info:backups:list`

>[!WARNING]
>
>Med det här kommandot tas de angivna filerna eller databasen bort innan de återställs. Alternativet `--media-file` tar till exempel bort medieresurser under katalogen `pub/media` innan den angivna återställningsfilen återställs. Kontrollera att du inte har ändrat det filsystem eller den databas som du vill behålla innan du använder det här kommandot.

>[!NOTE]
>
>Om du vill visa en lista över tillgängliga säkerhetskopieringsfiler anger du `magento info:backups:list`

Det här kommandot utför följande uppgifter:

1. Placerar butiken i underhållsläge.
1. Verifierar namnet på säkerhetskopieringsfilen.
1. Om du anger en fil för kodinspelning:

   a. Verifierar att målplatserna för återställningen är skrivbara (observera att mapparna `pub/static` och `var` ignoreras).

   b. Tar bort alla filer och kataloger under programinstallationskatalogen.

   c. Extraherar arkivfilen till målplatserna.

1. Om du anger en databasåterställningsfil:

   a. Släpper hela databasen.

   b. Återställer databasen med hjälp av säkerhetskopian av databasen.

1. Om du anger en medieåterställningsfil:

   a. Verifierar att målplatserna för återställningen är skrivbara.

   b. Tar bort alla filer och kataloger under `pub/media`

   c. Extraherar arkivfilen till målplatserna.

1. Tar arkivet ur underhållsläge.

Om du till exempel vill återställa en säkerhetskopia av kod (det vill säga ett filsystem) anger du följande kommandon i den ordning som visas:

* Visa en lista över säkerhetskopior:

  ```bash
  magento info:backups:list
  ```

* Återställ en säkerhetskopia av filen med namnet `1433876616_filesystem.tgz`:

  ```bash
  magento setup:rollback --code-file="1433876616_filesystem.tgz"
  ```

  Meddelanden som liknar följande:

  ```
  Enabling maintenance mode
  Code rollback is starting ...
  Code rollback filename: 1433876616_filesystem.tgz
  Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
  [SUCCESS]: Code rollback has completed successfully.
  Disabling maintenance mode
  ```

>[!NOTE]
>
>Om du vill köra kommandot `magento` igen utan att ändra kataloger kan du behöva ange `cd pwd`.
