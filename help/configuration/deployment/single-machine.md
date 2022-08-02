---
title: Driftsättning av en dator
description: Lär dig hur du distribuerar uppdateringar till Commerce på en produktionsserver med kommandoraden.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 1%

---

# Driftsättning av en dator

Det här avsnittet innehåller anvisningar om hur du distribuerar uppdateringar till Commerce på en produktionsserver med kommandoraden. Den här processen gäller tekniska användare som ansvarar för butiker som körs på en enda dator med vissa teman och språkområden installerade.

## Antaganden

- Du installerade Commerce med [Disposition].
- Du installerar uppdateringar direkt på servern.

>[!WARNING]
>
>Den här guiden gäller inte om du använder den `git clone` för att installera Commerce.
>Medverkande utvecklare bör använda [den här guiden][install] för att uppdatera sin Commerce-installation.

## Distributionssteg

1. Logga in på produktionsservern som eller växla till [ägare av filsystem][file-owner].

1. Ändra katalog till Commerce-baskatalogen:

   ```bash
   cd <Commerce base directory>
   ```

1. Aktivera underhållsläge med kommandot:

   ```bash
   bin/magento maintenance:enable
   ```

1. Använd uppdateringar i Commerce eller dess komponenter med följande kommandomönster:

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **package**: Namnet på det paket som du vill uppdatera.

   Exempel:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **version**: Målversionen för det paket som du vill uppdatera.

1. Uppdatera komponenter med Composer:

   ```bash
   composer update
   ```

1. Uppdatera databasschemat och data:

   ```bash
   bin/magento setup:upgrade
   ```

1. Kompilera koden:

   ```bash
   bin/magento setup:di:compile
   ```

1. Distribuera statiskt innehåll:

   ```bash
   bin/magento setup:static-content:deploy
   ```

1. Rensa cacheminnet:

   ```bash
   bin/magento cache:clean
   ```

1. Avsluta underhållsläge:

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://devdocs.magento.com/guides/v2.4/install-gde/install/prepare-install.html
[composer]: https://devdocs.magento.com/guides/v2.4/install-gde/composer.html
[file-owner]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html#magento-file-system-owner
