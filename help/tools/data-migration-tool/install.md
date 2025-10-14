---
title: Installera  [!DNL Data Migration Tool]
description: Lär dig hur du installerar  [!DNL Data Migration Tool] för överföring av data mellan Magento 1 och Magento 2.
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Installera [!DNL Data Migration Tool]

>[!INFO]
>
>Versionerna av Magento och [!DNL Data Migration Tool] måste matcha.


Se till att du använder *samma version* av både Magento 2 och [!DNL Data Migration Tool]. För Magento version 2.2.0 måste du till exempel också använda [!DNL Data Migration Tool] version 2.2.0.

## Kontrollera din version

Använd någon av följande metoder för att verifiera din version av Magento:

- [Disposition](#composer-metapackage)
- [GitHub-databas](#github-repository)

### Metapaket för disposition

Om du hämtade Magento-programmet med ett Composer-metapaket anger du följande kommando:

```bash
php <magento_root>/bin/magento --version
```

### GitHub-databas

Om du klonade Magento 2 GitHub-databasen anger du följande kommandon:

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

Om du för närvarande befinner dig i grenen `develop` måste du ändra till en [släppt gren](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) innan du fortsätter.

Om du inte har installerat Adobe Commerce än [installerar du det nu](../../installation/prerequisites/commerce.md).
Om du klonar GitHub-databasen kontrollerar du att du har checkat ut en versionstagg enligt beskrivningen i [(Contributor) klona GitHub-databasen &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## Sök efter släppta versioner av [!DNL Data Migration Tool]

Gå till sidan [Releaser](https://github.com/magento/data-migration-tool/releases) i GitHub-databasen [!DNL Data Migration Tool] om du vill hitta tillgängliga frisläppta versioner.

## Installera [!DNL Data Migration Tool]

Du kan installera [!DNL Data Migration Tool] från:

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Kontrollera att du har:

- Slutförde alla aktiviteter som nämns i avsnittet [Förhandsvillkor](prerequisites.md)
- [Verifierade version](install.md#check-your-version) av Magento 2

### Installera från `repo.magento.com`

Om du vill installera [!DNL Data Migration Tool] måste du uppdatera `composer.json` i Magento rotinstallationskatalog för att ange platsen för [!DNL Data Migration Tool]-paketet.

1. Logga in på programservern som, eller växla till, ägare av [filsystemet](../../installation/prerequisites/file-system/overview.md).
1. Byt till programmets rotkatalog.
1. Ange följande kommandon:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Där `<version>` måste matcha versionen av Magento 2-kodbasen.

   För version 2.2.0 anger du:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. Ange dina [autentiseringsnycklar](../../installation/prerequisites/authentication-keys.md) när du uppmanas till detta. Din offentliga nyckel är ditt användarnamn. Din privata nyckel är ditt lösenord.

### Installera från GitHub

Om du har klonat GitHub-databasen följer du stegen nedan för att installera [!DNL Data Migration Tool].

1. Logga in på programservern som, eller växla till, ägare av [filsystemet](../../installation/prerequisites/file-system/overview.md).
1. Byt till programmets rotkatalog.
1. Ange följande kommandon:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   där `<version>` måste matcha versionen av Magento 2-kodbasen.

   För version 2.2.0 anger du:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Kontrollera version av installerad [!DNL Data Migration Tool]

1. Ändra till din [!DNL Data Migration Tool]-katalog: `<vendor>/magento/data-migration-tool`.

1. Öppna [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) i en textredigerare.

1. Posten `version` i den filen är versionen av [!DNL Data Migration Tool].
