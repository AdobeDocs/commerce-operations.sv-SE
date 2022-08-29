---
title: Installera [!DNL Data Migration Tool]
description: Lär dig hur du installerar [!DNL Data Migration Tool] att överföra data mellan Magento 1 och Magento 2.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
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

Om du laddade ned Magento med en [Disposition](https://glossary.magento.com/composer) metapackage, ange följande kommando:

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

Om du är i `develop` gren, du måste ändra till <a href="https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/dev_downgrade.html">frisläppt gren</a> innan du fortsätter.

Om du inte har installerat Magento än [installera nu](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html).
Om du klonar GitHub-databasen kontrollerar du att du har checkat ut en versionstagg enligt beskrivningen i [(Contributor) Klona Magento-databasen](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/dev_install.html).

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

1. Logga in på Magento-servern som eller växla till [ägare av filsystem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Byt till rotkatalog för Magento 2.
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

1. Ange [autentiseringsnycklar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html). Din offentliga nyckel är ditt användarnamn; din privata nyckel är ditt lösenord.

### Installera från GitHub

Om du har klonat Magento 2 från GitHub-databasen följer du stegen nedan för att installera [!DNL Data Migration Tool].

1. Logga in på Magento-servern som eller växla till [ägare av filsystem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Byt till rotkatalog för Magento 2.
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
