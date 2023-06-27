---
title: Installera [!DNL Data Migration Tool]
description: Lär dig hur du installerar [!DNL Data Migration Tool] att överföra data mellan Magento 1 och Magento 2.
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Installera [!DNL Data Migration Tool]

>[!INFO]
>
>Magento och [!DNL Data Migration Tool] måste matcha.


Se till att du använder *samma frisläppta version* Magento 2 och [!DNL Data Migration Tool]. För Magento version 2.2.0 måste du till exempel också använda [!DNL Data Migration Tool] version 2.2.0.

## Kontrollera din version

Använd någon av följande metoder för att verifiera din version av Magento:

- [Disposition](#composer-metapackage)
- [GitHub-databas](#github-repository)

### Metapaket för disposition

Om du hämtade Magento med Composer-metapaketet anger du följande kommando:

```bash
php <magento_root>/bin/magento --version
```

### GitHub-databas

Om du klonade GitHub-databasen Magento 2 anger du följande kommandon:

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

Om du är i `develop` gren, du måste ändra till [frisläppt gren](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) innan du fortsätter.

Om du inte har installerat Adobe Commerce eller Magento Open Source än [installera nu](../../installation/prerequisites/commerce.md).
Om du klonar GitHub-databasen kontrollerar du att du har checkat ut en versionstagg enligt beskrivningen i [(Contributor) Klona GitHub-databasen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## Hitta släppta versioner av [!DNL Data Migration Tool]

Gå till [Utgåvor](https://github.com/magento/data-migration-tool/releases) sidan på [!DNL Data Migration Tool] GitHub-databas för att hitta tillgängliga versioner.

## Installera [!DNL Data Migration Tool]

Du kan installera [!DNL Data Migration Tool] från:

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Kontrollera att du har:

- Slutförde alla uppgifter som anges i [Förhandsvillkor](prerequisites.md) section
- [Versionen har verifierats](install.md#check-your-version) av programvaran Magento 2

### Installera från `repo.magento.com`

Så här installerar du [!DNL Data Migration Tool]måste du uppdatera `composer.json` i Magento rotinstallationskatalog där platsen för [!DNL Data Migration Tool] paket.

1. Logga in på programservern som, eller växla till [ägare av filsystem](../../installation/prerequisites/file-system/overview.md).
1. Byt till programmets rotkatalog.
1. Ange följande kommandon:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Plats `<version>` måste matcha versionen av kodbasen Magento 2.

   För version 2.2.0 anger du till exempel:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. Ange [autentiseringsnycklar](../../installation/prerequisites/authentication-keys.md). Din offentliga nyckel är ditt användarnamn; din privata nyckel är ditt lösenord.

### Installera från GitHub

Om du har klonat GitHub-databasen följer du stegen nedan för att installera [!DNL Data Migration Tool].

1. Logga in på programservern som, eller växla till [ägare av filsystem](../../installation/prerequisites/file-system/overview.md).
1. Byt till programmets rotkatalog.
1. Ange följande kommandon:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   där `<version>` måste matcha versionen av kodbasen Magento 2.

   För version 2.2.0 anger du till exempel:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Kontrollera version av installerat [!DNL Data Migration Tool]

1. Byt till [!DNL Data Migration Tool] katalog: `<vendor>/magento/data-migration-tool`.

1. Öppna [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) i en textredigerare.

1. The `version` i den filen är versionen av [!DNL Data Migration Tool].
