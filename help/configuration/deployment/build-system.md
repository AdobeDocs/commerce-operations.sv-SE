---
title: Skapa systeminställningar
description: Lär dig hur du distribuerar Commerce till ett byggsystem.
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Skapa systeminställningar

Du kan ha ett byggsystem som uppfyller följande krav:

- All Commerce-kod står under källkontroll i samma databas som utvecklings- och produktionssystemen
- Se till att alla följande är _ingår_ i källkontroll:

   - `app/etc/config.php`
   - `generated` katalog (och underkataloger)
   - `pub/media` katalog
   - `pub/media/wysiwyg` katalog (och underkataloger)
   - `pub/static` katalog (och underkataloger)

- Måste ha en kompatibel PHP-version installerad
- Composer måste vara installerat
- Ägarskap och behörigheter för filsystemet anges enligt [Krav för dina utvecklings-, bygg- och produktionssystem](../deployment/technical-details.md).
- Build-systemet behöver inte ha Commerce installerat, men koden måste vara tillgänglig för det.

>[!WARNING]
>
>Databasanslutningen behövs inte om den redan finns i `config.php`; se [Exportera konfigurationen](../cli/export-configuration.md). Annars krävs databasanslutningen.

>[!INFO]
>
>Byggmaskinen kan finnas på sin egen värd eller på samma värd som ett installerat Commerce-system.

## Konfigurera byggdatorn

I följande avsnitt beskrivs hur du konfigurerar byggdatorn.

### Installera disposition

Kontrollera först om Composer redan är installerat:

Ange något av följande kommandon i en kommandotolk:

- `composer --help`
- `composer list --help`

Om kommandohjälpen visas är Composer redan installerat.

Om ett fel visas följer du de här stegen för att installera Composer.

Så här installerar du Composer:

1. Ändra till eller skapa en tom katalog på din Commerce-server.

1. Ange följande kommandon:

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

Ytterligare installationsalternativ finns i [Installationsdokumentation för Composer][composer].

### Installera PHP

Installera PHP på [CentOS] eller [Ubuntu].

### Konfigurera byggsystemet

Så här konfigurerar du byggsystemet:

1. Logga in på byggsystemet som, eller växla till, ägare av filsystemet.
1. Hämta Commerce-koden från källkontrollen.

   Använd följande kommando om du använder Git:

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Ändra till Commerce-rotkatalogen och ange:

   ```bash
   composer install
   ```

1. Vänta på att beroenden ska uppdateras.
1. Ange ägarskap:

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   Till exempel:

   ```bash
   chown -R commerce-username:apache .
   ```

1. Öppna om du använder Git `.gitignore` i en textredigerare.
1. Börja var och en av följande rader med en `#` för att kommentera ut dem:

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. Spara ändringarna i `.gitignore` och avsluta textredigeraren.
1. Om du använder Git använder du följande kommandon för att genomföra ändringen:

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   Se [`.gitignore` referens](../reference/config-reference-gitignore.md) för mer information.

1. Build-systemet ska använda [standardläge](../bootstrap/application-modes.md#default-mode) eller [utvecklarläge](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` krävs. Det kan vara antingen `default` eller `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
