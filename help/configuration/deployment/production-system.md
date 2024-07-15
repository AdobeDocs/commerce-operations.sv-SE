---
title: Installation av produktionssystem
description: Lär dig hur du konfigurerar ett produktionssystem för Commerce-programmet.
exl-id: e678e97e-d9f2-4f24-bb6b-1994a2a1167c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Installation av produktionssystem

Du kan ha ett produktionssystem. Alla följande måste vara true:

- All Commerce-kod har källkontroll i samma databas som utvecklings- och byggsystemen
- Kontrollera att alla följande är _inkluderade_ i källkontrollen:

   - `app/etc/config.php`
   - `generated`-katalog (och underkataloger)
   - `pub/media`-katalog
   - `pub/media/wysiwyg`-katalog (och underkataloger)
   - `pub/static`-katalog (och underkataloger)

- Commerce 2.2 eller senare måste installeras och ställas in för [produktionsläget](../bootstrap/application-modes.md#production-mode)
- Den har ägarskap och behörigheter för filsystemet inställda enligt beskrivningen i [Krav för ditt utvecklings-, bygg- och produktionssystem](../deployment/prerequisites.md).

## Konfigurera en produktionsmaskin

Så här konfigurerar du en produktionsmaskin:

1. När du har installerat Commerce eller dragit in det från källkontrollen loggar du in på produktionsservern som, eller växlar till, ägaren av filsystemet.
1. Skapa `~/.ssh/.composer/auth.json` om du inte redan har gjort det.

   Skapa katalogen:

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Skapa `auth.json` i den katalogen.

   `auth.json` måste innehålla dina [autentiseringsnycklar](../../installation/prerequisites/authentication-keys.md).

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
1. Öppna `env.php` i en textredigerare och ändra nödvändiga värden (till exempel databasanslutningsinformation).
1. Kör kommandot [`magento config:set`](../cli/set-configuration-values.md) eller [`magento config:set-sensitive`](../cli/set-configuration-values.md) för att ange värden för systemspecifika respektive känsliga konfigurationsvärden.

   I följande avsnitt visas ett exempel.

## Ange konfigurationsvärden i produktionssystemet

I det här avsnittet beskrivs hur du anger känsliga värden i produktionssystemet med hjälp av kommandot `magento config:sensitive:set`.

Så här anger du känsliga värden:

1. Sök efter ett värde som ska anges med hjälp av den [känsliga värdereferensen](../reference/config-reference-sens.md).
1. Anteckna konfigurationssökvägen för inställningen.
1. Logga in i produktionssystemet som, eller växla till, ägare av filsystemet.
1. Gå till Commerce installationskatalog.
1. Ange följande kommando:

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   Om du till exempel vill ange värdet `1234` för YouTube API-nyckeln anger du

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   Du kan också ange ett eller flera värden interaktivt enligt följande:

   ```bash
   bin/magento config:sensitive:set -i
   ```

   Ange ett värde för varje känslig inställning när du uppmanas till det eller tryck på Retur om du vill hoppa över ett värde och gå till nästa.

1. Logga in på Admin för att bekräfta att värdet har angetts.
1. Leta reda på inställningen i Admin.

   Nyckelinställningen för YouTube API finns till exempel i **Lagrar** > Inställningar > **Konfiguration** > **Katalog** > **Katalog** > **Produktvideo**.

   Inställningen visas i Admin och kan inte redigeras. I bilden nedan visas ett exempel.

   ![Känslig inställning i administratören](../../assets/configuration/sensitive-set.png)
