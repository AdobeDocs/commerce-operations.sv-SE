---
title: Installation av produktionssystem
description: Lär dig hur du skapar ett produktionssystem för Commerce-programmet.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Installation av produktionssystem

Du kan ha ett produktionssystem. Alla följande måste vara true:

- All Commerce-kod finns i källkontrollen i samma databas som utvecklings- och konstruktionssystemen
- Se till att alla följande är _ingår_ i källkontroll:

   - `app/etc/config.php`
   - `generated` katalog (och underkataloger)
   - `pub/media` katalog
   - `pub/media/wysiwyg` katalog (och underkataloger)
   - `pub/static` katalog (och underkataloger)

- Commerce 2.2 eller senare måste installeras och ställas in för [produktionsläge](../bootstrap/application-modes.md#production-mode)
- Ägarskap och behörigheter för filsystemet anges enligt [Krav för dina utvecklings-, bygg- och produktionssystem](../deployment/prerequisites.md).

## Konfigurera en produktionsmaskin

Så här konfigurerar du en produktionsmaskin:

1. När du har installerat Commerce eller dragit in det från källkontrollen loggar du in på produktionsservern som, eller växlar till, ägaren av filsystemet.
1. Skapa `~/.ssh/.composer/auth.json` om du inte redan har gjort det.

   Skapa katalogen:

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Skapa `auth.json` i den katalogen.

   `auth.json` måste innehålla [autentiseringsnycklar](../../installation/prerequisites/authentication-keys.md).

   Ett exempel följer:

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Spara ändringarna i `auth.json`.
1. Kopiera `<Commerce root dir>/app/etc/env.php` från utvecklingssystemet till produktionssystemet.
1. Öppna `env.php` i en textredigerare och ändra de värden som behövs (till exempel databasanslutningsinformation).
1. Kör [`magento config:set`](../cli/set-configuration-values.md) eller [`magento config:set-sensitive`](../cli/set-configuration-values.md) om du vill ange värden för systemspecifika eller känsliga konfigurationsvärden.

   I följande avsnitt visas ett exempel.

## Ange konfigurationsvärden i produktionssystemet

I det här avsnittet beskrivs hur du ställer in känsliga värden i produktionssystemet med hjälp av `magento config:sensitive:set` -kommando.

Så här anger du känsliga värden:

1. Söka efter ett värde som ska anges med [referens för känsligt värde](../reference/config-reference-sens.md).
1. Anteckna konfigurationssökvägen för inställningen.
1. Logga in i produktionssystemet som, eller växla till, ägare av filsystemet.
1. Ändra till installationskatalogen för Commerce.
1. Ange följande kommando:

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   Om du till exempel vill ange värdet för YouTube API-nyckeln till `1234`, ange

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   Du kan också ange ett eller flera värden interaktivt enligt följande:

   ```bash
   bin/magento config:sensitive:set -i
   ```

   Ange ett värde för varje känslig inställning när du uppmanas till det eller tryck på Retur om du vill hoppa över ett värde och gå till nästa.

1. Logga in på administratören för att verifiera att värdet har angetts.
1. Leta reda på inställningen i Admin.

   Nyckelinställningen för YouTube API finns i **Lager** > Inställningar > **Konfiguration** > **Katalog** > **Katalog** > **Produktvideo**.

   Inställningen visas i Admin och kan inte redigeras. I bilden nedan visas ett exempel.

   ![Känslig inställning i administratören](../../assets/configuration/sensitive-set.png)
