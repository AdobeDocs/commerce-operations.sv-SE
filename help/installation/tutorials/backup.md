---
title: Säkerhetskopiera och återställa filsystemet, mediet och databasen
description: Följ de här stegen för att säkerhetskopiera och återställa ditt Adobe Commerce-program.
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Säkerhetskopiera och återställa filsystemet, mediet och databasen

Med det här kommandot kan du säkerhetskopiera:

* Filsystemet (exklusive `var` och `pub/static` kataloger)
* Katalogen `pub/media`
* Databasen

Säkerhetskopior lagras i katalogen `var/backups` och kan återställas när som helst med kommandot [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

Efter säkerhetskopiering kan du [återställa](#rollback) senare.

>[!TIP]
>
>Information om projekt för molninfrastruktur finns i [Ögonblicksbilder och hantering av säkerhetskopiering](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/storage/snapshots) i _molnguiden_.

## Aktivera säkerhetskopiering

Säkerhetskopieringsfunktionen är inaktiverad som standard. Aktivera genom att ange följande CLI-kommando:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**Meddelande om borttagning:**
>Säkerhetskopieringsfunktionen är borttagen från och med 2.1.16, 2.2.7 och 2.3.0. Vi rekommenderar att du undersöker ytterligare säkerhetskopieringstekniker och binära säkerhetskopieringsverktyg (som Percona XtraBackup).

## Ange gräns för öppna filer

Återställning till en tidigare säkerhetskopia kan misslyckas i tysthet, vilket resulterar i att ofullständiga data skrivs till filsystemet eller databasen med kommandot [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

Ibland kan en lång frågesträng få användarens tilldelade minnesutrymme att ta slut på minne på grund av för många rekursiva anrop.

## Ange öppna filer `ulimit`

Vi rekommenderar att du anger de öppna filerna [`ulimit`](https://ss64.com/bash/ulimit.html) för filsystemanvändaren till värdet `65536` eller mer.

Du kan antingen göra detta på kommandoraden eller göra det till en permanent inställning för användaren genom att redigera gränssnittsskriptet.

Innan du fortsätter, om du inte redan har gjort det, växlar du till [filsystemets ägare](../prerequisites/file-system/overview.md).

Kommando:

```bash
ulimit -s 65536
```

Du kan ändra det till ett större värde om det behövs.

>[!NOTE]
>
>Syntaxen för öppna filer `ulimit` beror på det UNIX-skal du använder. Inställningen ovan ska fungera med CentOS och Ubuntu med Bash-skalet. För macOS är dock rätt inställning `ulimit -S 65532`. Mer information finns på en huvudsida eller i en referens till operativsystemet.

Om du vill kan du ange värdet i användarens Bash-skal:

1. Om du inte redan har gjort det växlar du till [filsystemets ägare](../prerequisites/file-system/overview.md).
1. Öppna `/home/<username>/.bashrc` i en textredigerare.
1. Lägg till följande rad:

   ```bash
   ulimit -s 65536
   ```

1. Spara ändringarna i `.bashrc` och avsluta textredigeraren.

>[!WARNING]
>
>Vi rekommenderar att du undviker att ange ett värde för [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) i filen `php.ini` eftersom det kan resultera i ofullständiga återställningar utan felmeddelande.

## Säkerhetskopierar

Kommandoanvändning:

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

Kommandot utför följande uppgifter:

1. Placerar butiken i underhållsläge.
1. Utför något av följande kommandoalternativ.

   | Alternativ | Betydelse | Säkerhetskopians filnamn och plats |
   |--- |--- |--- |
   | `--code` | Säkerhetskopierar filsystemet (förutom var- och pub/static-kataloger). | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | Säkerhetskopiera katalogen pub/media. | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | Säkerhetskopiera databasen. | `var/backups/<timestamp>/_db.sql` |

1. Tar arkivet ur underhållsläge.

Om du till exempel vill säkerhetskopiera filsystemet och databasen

```bash
bin/magento setup:backup --code --db
```

Meddelanden som liknar följande:

```
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1434133011_filesystem.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1434133011_filesystem.tgz
[SUCCESS]: Code backup completed successfully.
DB backup is starting...
DB backup filename: 1434133011_db.sql
DB backup path: /var/www/html/magento2/var/backups/1434133011_db.sql
[SUCCESS]: DB backup completed successfully.
Disabling maintenance mode
```

## Återställning

I det här avsnittet beskrivs hur du återställer en säkerhetskopia som du har gjort tidigare. Du måste känna till filnamnet på den säkerhetskopieringsfil som ska återställas.

Ange följande för att hitta namnet på säkerhetskopiorna:

```bash
bin/magento info:backups:list
```

Den första strängen i namnet på säkerhetskopieringsfilen är tidsstämpeln.

Om du vill återställa en tidigare säkerhetskopia anger du:

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

Om du till exempel vill återställa en mediesäkerhetskopiering med namnet `1440611839_filesystem_media.tgz` anger du

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

Meddelanden som liknar följande:

```
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
