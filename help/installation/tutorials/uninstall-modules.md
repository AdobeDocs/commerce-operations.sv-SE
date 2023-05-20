---
title: Avinstallera moduler
description: Följ de här stegen för att avinstallera en Adobe Commerce- eller Magento Open Source-modul.
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# Avinstallera moduler

I det här avsnittet beskrivs hur du avinstallerar en eller flera moduler. Under avinstallationen kan du ta bort modulens kod, databasschema och databasdata. Du kan skapa säkerhetskopior först så att du kan återställa data senare.

Du bör endast avinstallera en modul om du är säker på att du inte kommer att använda den. I stället för att avinstallera en modul kan du inaktivera den enligt beskrivningen i [Aktivera eller inaktivera moduler](manage-modules.md).

>[!NOTE]
>
>Det här kommandot kontrollerar att endast beroenden som deklarerats i `composer.json` -fil. Om du avinstallerar en modul som är _not_ definieras i `composer.json` avinstallerar det här kommandot modulen utan att kontrollera om det finns beroenden. Det här kommandot gör _not_ Ta dock bort modulens kod från filsystemet. Du måste använda filsystemverktygen för att ta bort modulens kod (till exempel `rm -rf <path to module>`). Som ett alternativ kan du [disable](manage-modules.md) icke-dispositionsmoduler.

Kommandoanvändning:

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

Plats `{ModuleName}` anger modulnamnet i `<VendorName>_<ModuleName>` format. Kundmodulens namn är till exempel `Magento_Customer`. Om du vill visa en lista med modulnamn anger du `magento module:status`

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
   | `--backup-code` | Säkerhetskopierar filsystemet (förutom `var` och `pub/static` kataloger). | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | Säkerhetskopierar katalogen pub/media. | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | Säkerhetskopierar databasen. | `var/backups/<timestamp>_db.gz` |

1. If `--remove-data` har angetts tar du bort databasschemat och data som definierats i modulens `Uninstall` klasser.

   För varje angiven modul som ska avinstalleras anropas `uninstall` metoden i `Uninstall` klassen. Den här klassen måste ärva från [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. Tar bort de angivna modulerna från `setup_module` databastabell.
1. Tar bort de angivna modulerna från modullistan i [distributionskonfiguration](../../configuration/reference/deployment-files.md).
1. Tar bort kod från kodbasen med `composer remove`.

   >[!NOTE]
   >
   >Avinstallera en modul _alltid_ körningar `composer remove`. The `--remove-data` tar bort databasdata och schema som definieras av modulens `Uninstall` klassen.

1. Rensar cachen.
1. Uppdateringsgenererade klasser.
1. If `--clear-static-content` anges, rengöringar [genererade statiska vyfiler](../../configuration/cli/static-view-file-deployment.md).
1. Tar arkivet ur underhållsläge.

Om du till exempel försöker avinstallera en modul som en annan modul är beroende av visas följande meddelande:

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

Ett alternativ är att avinstallera båda modulerna efter säkerhetskopiering av modulens filsystem, `pub/media` filer och databastabeller, men _not_ ta bort modulens databasschema eller data:

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

Meddelanden som liknar följande:

```terminal
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
>Fel visas om du försöker avinstallera en modul som är beroende av en annan modul. I så fall kan du inte avinstallera en modul; du måste avinstallera båda.

## Återställ filsystemet, databasen eller mediefilerna

Använd följande kommando om du vill återställa kodbasen till det läge där du säkerhetskopierade den:

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

Plats `<filename>` är namnet på säkerhetskopieringsfilen i `<app_root>/var/backups` katalog. Om du vill visa en lista över säkerhetskopierade filer anger du `magento info:backups:list`

>[!WARNING]
>
>Med det här kommandot tas de angivna filerna eller databasen bort innan de återställs. Till exempel `--media-file` alternativet tar bort medieresurser under `pub/media` katalog före återställning från den angivna återställningsfilen. Kontrollera att du inte har ändrat det filsystem eller den databas som du vill behålla innan du använder det här kommandot.

>[!NOTE]
>
>Om du vill visa en lista över tillgängliga säkerhetskopieringsfiler anger du `magento info:backups:list`

Det här kommandot utför följande uppgifter:

1. Placerar butiken i underhållsläge.
1. Verifierar namnet på säkerhetskopieringsfilen.
1. Om du anger en fil för kodinspelning:

   a. Verifierar att målplatserna för återställningen är skrivbara (observera att `pub/static` och `var` mappar ignoreras).

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

* Återställa en filsäkerhetskopia med namnet `1433876616_filesystem.tgz`:

   ```bash
   magento setup:rollback --code-file="1433876616_filesystem.tgz"
   ```

   Meddelanden som liknar följande:

   ```terminal
   Enabling maintenance mode
   Code rollback is starting ...
   Code rollback filename: 1433876616_filesystem.tgz
   Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
   [SUCCESS]: Code rollback has completed successfully.
   Disabling maintenance mode
   ```

>[!NOTE]
>
>Så här kör du `magento` utan att ändra kataloger kan du behöva ange `cd pwd`.
