---
title: Utför en uppgradering
description: Följ de här stegen för att uppgradera ett Adobe Commerce- eller Magento Open Source-projekt.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---


# Uppgradera

Du kan uppgradera ditt Adobe Commerce- eller Magento Open Source-program från kommandoraden om du har installerat programmet genom att:

- Hämtar [metapackage](https://glossary.magento.com/metapackage) med `composer create-project` -kommando.
- Installerar det komprimerade arkivet.

>[!NOTE]
>
>Använd inte den här metoden för att uppgradera om du klonade GitHub-databasen. Istället kan du se [Uppgradera en Git-baserad installation](../developer/git-installs.md) för uppgraderingsinstruktioner.

Följande instruktioner visar hur du uppgraderar med Composer. Adobe Commerce 2.4.2 har nu stöd för Composer 2. Om du försöker uppgradera från &lt;2.4.1 måste du först uppgradera till en version som är kompatibel med Composer 2 (t.ex. 2.4.2) med Composer 1 _före_ uppgradera till Composer 2 för >2.4.2-uppgraderingar. Dessutom måste du köra en [version som stöds](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) PHP.

>[!WARNING]
>
>Förfarandet för uppgradering av Adobe Commerce och Magento Open Source har ändrats. Du måste installera en ny version av `magento/composer-root-update-plugin` paket (se [krav](../prepare/prerequisites.md)). Dessutom har kommandona för uppgradering ändrats från `composer require magento/<package_name>` till `composer require-commerce magento/<package_name>`.

## Innan du börjar

Du måste fylla i [uppgraderingskrav](../prepare/prerequisites.md) för att förbereda miljön innan du startar uppgraderingsprocessen.

## Hantera paket

>[!NOTE]
>
>Se exemplen i slutet av det här avsnittet för hjälp med att ange olika versionsnivåer. Till exempel en mindre release, kvalitetskorrigering och säkerhetskorrigering. Adobe Commerce-kunder har tillgång till patchar två veckor före det allmänna tillgänglighetsdatumet (GA). Förhandsversionspaket är bara tillgängliga via Composer. Du kan inte hitta dem på hämtningsportalen eller GitHub förrän GA. Om du inte hittar dessa paket i Composer kontaktar du Adobe Commerce Support.

1. Växla till underhållsläge för att förhindra åtkomst till din butik under uppgraderingsprocessen.

   ```bash
   bin/magento maintenance:enable
   ```

   Se [Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html) för ytterligare alternativ. Du kan också skapa en [sida för anpassat underhållsläge](https://devdocs.magento.com/guides/v2.4/comp-mgr/trouble/cman/maint-mode.html).

1. Skapa en säkerhetskopia av `composer.json` -fil.

   ```bash
   cp composer.json composer.json.bak
   ```

1. Lägg till eller ta bort specifika paket utifrån dina behov.

   Om du till exempel uppgraderar från Magento Open Source till Adobe Commerce tar du bort paketet Magento Open Source.

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   Du kan också uppgradera exempeldata.

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce:_

      ```bash
      composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
      ```

   - _Magento Open Source:_

      ```bash
      composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
      ```

1. Uppgradera instansen med följande `composer require-commerce` kommandosyntax:

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   Kommandoalternativen är:

   - `<product>` —(Obligatoriskt) Paketet som ska uppgraderas. För lokala installationer måste värdet vara antingen `product-community-edition` eller `product-enterprise-edition`.

   - `<version>` —(Obligatoriskt) Den version av Adobe Commerce eller Magento Open Source som du uppgraderar till. Till exempel: `2.4.3`.

   - `--no-update` —(Obligatoriskt) Inaktiverar den automatiska uppdateringen av beroenden.

   - `--interactive-root-conflicts` —(Valfritt) Du kan interaktivt visa och uppdatera inaktuella värden från tidigare versioner eller anpassade värden som inte matchar den version du uppgraderar till.

   - `--force-root-updates` —(Valfritt) Åsidosätter alla anpassade värden som står i konflikt med de förväntade Magento-värdena.

   - `--help` —(Valfritt) Anger användningsinformation om plugin-programmet.
   Om ingen `--interactive-root-conflicts` eller `--force-root-updates` Om du anger det behåller kommandot de befintliga värden som är i konflikt och ett varningsmeddelande visas. Mer information om plugin-programmet finns i [Plugin-användning VIKTIGT](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. Uppdatera beroenden.

   ```bash
   composer update
   ```

### Exempel - lista över tillgängliga versioner

Se en fullständig lista över tillgängliga 2.4.x-versioner:

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### Exempel - Mindre version

Mindre releaser innehåller nya funktioner, kvalitetskorrigeringar och säkerhetskorrigeringar. Använd Composer för att ange en mindre release. Om du till exempel vill ange metapaketet Magento Open Source 2.4.3:

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.0 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.0 --no-update
```

### Exempel - Kvalitetskorrigering

Patchar för kvalitet innehåller i första hand funktioner _och_ säkerhetskorrigeringar. De kan dock ibland innehålla nya bakåtkompatibla funktioner. Använd Composer för att hämta en kvalitetskorrigering. Om du till exempel vill ange metapaketet Magento Open Source 2.4.1:

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3 --no-update
```

### Exempel - Säkerhetsuppdatering

Säkerhetsuppdateringar innehåller endast säkerhetskorrigeringar. De är utformade för att göra uppgraderingsprocessen snabbare och enklare.

Säkerhetsuppdateringar använder namnkonventionen för Composer `2.4.x-px`. Använd Composer för att ange en korrigering.

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3-p1 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3-p1 --no-update
```

## Uppdatera metadata

1. Uppdatera `"name"`, `"version"`och `"description"` fälten i `composer.json` vid behov.

   >[!NOTE]
   >
   >Uppdatera metadata i `composer.json` filen är helt ytlig, inte funktionell.

1. Använd uppdateringar.

   ```bash
   composer update
   ```

1. Rensa `var/` och `generated/` underkataloger:

   ```bash
   rm -rf var/cache/*
   ```

   ```bash
   rm -rf var/page_cache/*
   ```

   ```bash
   rm -rf generated/code/*
   ```

   >[!NOTE]
   >
   >Om du använder en annan cache-lagring än filsystemet, till exempel Redis eller Memcache, måste du även rensa cacheminnet manuellt där.

1. Uppdatera databasschemat och data.

   ```bash
   bin/magento setup:upgrade
   ```

1. Inaktivera underhållsläge.

   ```bash
   bin/magento maintenance:disable
   ```

1. _(Valfritt)_ Starta om Varnish.

   Om du använder Varnish för sidcachelagring startar du om det:

   ```bash
   service varnish restart
   ```

## Kontrollera ditt arbete

Öppna din butiks-URL i en webbläsare för att kontrollera om uppgraderingen lyckades. Om uppgraderingen misslyckades läses inte butiken in korrekt.

Om programmet misslyckas med en  `We're sorry, an error has occurred while generating this email.` fel:

1. Återställ [ägarskap och behörigheter för filsystem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html) som en användare med `root` behörighet.
1. Rensa följande kataloger:
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Kontrollera butiken i webbläsaren igen.