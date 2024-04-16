---
title: Uppgradera
description: Följ de här stegen för att uppgradera lokala distributioner av Adobe Commerce.
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---


# Uppgradera

Du kan uppgradera _lokal_ distributioner av Adobe Commerce eller Magento Open Source från kommandoraden om du har installerat programmet av:

- Hämta Composer-metapaketet med `composer create-project` -kommando.
- Installerar det komprimerade arkivet.

>[!NOTE]
>
>- Information om projekt för molninfrastruktur för Adobe Commerce finns på [Uppgradera Commerce-version](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html) i molnguiden.
>- Använd inte den här metoden för att uppgradera om du klonade GitHub-databasen. Se [Uppgradera en Git-baserad installation](../developer/git-installs.md).

Följande instruktioner visar hur du uppgraderar med Composer-pakethanteraren. Adobe Commerce 2.4.2 har nu stöd för Composer 2. Om du försöker uppgradera från &lt;2.4.1 måste du först uppgradera till en version som är kompatibel med Composer 2 (till exempel 2.4.2) med Composer 1 _före_ uppgradera till Composer 2 för >2.4.2-uppgraderingar. Dessutom måste du köra en [version som stöds](../../installation/system-requirements.md) PHP.

>[!WARNING]
>
>Förfarandet för uppgradering av Adobe Commerce har ändrats. Du måste installera en ny version av `magento/composer-root-update-plugin` paket (se [krav](../prepare/prerequisites.md)). Dessutom har kommandona för uppgradering ändrats från `composer require magento/<package_name>` till `composer require-commerce magento/<package_name>`.

## Innan du börjar

Du måste fylla i [uppgraderingskrav](../prepare/prerequisites.md) för att förbereda miljön innan du startar uppgraderingsprocessen.

## Hantera paket

>[!NOTE]
>
>Se exemplen i slutet av det här avsnittet för hjälp med att ange olika versionsnivåer. Exempel: kvalitetspatchar och säkerhetspatchar. Om du inte hittar dessa paket i Composer kontaktar du Adobe Commerce Support.

1. Växla till underhållsläge för att förhindra åtkomst till din butik under uppgraderingsprocessen.

   ```bash
   bin/magento maintenance:enable
   ```

   Se [Aktivera eller inaktivera underhållsläge](../../installation/tutorials/maintenance-mode.md) för ytterligare alternativ. Du kan också skapa en [sida för anpassat underhållsläge](../troubleshooting/maintenance-mode-options.md).

1. Om du startar uppgraderingsprocessen medan asynkrona processer, som meddelandeköanvändare, körs, kan det medföra att data skadas. Inaktivera alla kroniska jobb för att förhindra att data skadas.

   _Adobe Commerce om molninfrastruktur:_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source:_

   ```bash
   bin/magento cron:remove
   ```

1. Starta alla meddelandekökonsumenter manuellt för att se till att alla meddelanden förbrukas.

   ```bash
   bin/magento cron:run --group=consumers
   ```

   Vänta på att kron-jobbet slutförs. Du kan övervaka jobbets status med ett processvisningsprogram eller genom att köra `ps aux | grep 'bin/magento queue'` kommandot flera gånger tills alla processer är slutförda.

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

   - `<product>` —(Obligatoriskt) Paketet som ska uppgraderas. För lokala installationer måste detta värde vara antingen `product-community-edition` eller `product-enterprise-edition`.

   - `<version>` —(Obligatoriskt) Den version av Adobe Commerce eller Magento Open Source som du uppgraderar till. Till exempel: `2.4.3`.

   - `--no-update` —(Obligatoriskt) Inaktiverar den automatiska uppdateringen av beroenden.

   - `--interactive-root-conflicts` —(Valfritt) Du kan interaktivt visa och uppdatera inaktuella värden från tidigare versioner eller anpassade värden som inte matchar den version du uppgraderar till.

   - `--force-root-updates` —(Valfritt) Åsidosätter alla anpassade värden som står i konflikt med de förväntade Commerce-värdena.

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

### Exempel - Kvalitetskorrigering

Patchar för kvalitet innehåller i första hand funktioner _och_ säkerhetskorrigeringar. De kan dock ibland innehålla nya bakåtkompatibla funktioner. Använd Composer för att hämta en kvalitetskorrigering.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### Exempel - Säkerhetsuppdatering

Säkerhetsuppdateringar innehåller endast säkerhetskorrigeringar. De är utformade för att göra uppgraderingsprocessen snabbare och enklare. Säkerhetsuppdateringar använder namnkonventionen för Composer `2.4.x-px`.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
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

1. _(Valfritt)_ Starta om lack.

   Om du använder Varnish för sidcachelagring startar du om det:

   ```bash
   service varnish restart
   ```

## Kontrollera ditt arbete

Om du vill kontrollera om uppgraderingen lyckades öppnar du din butiks-URL i en webbläsare. Om uppgraderingen misslyckades läses inte butiken in korrekt.

Om programmet misslyckas med en  `We're sorry, an error has occurred while generating this email.` fel:

1. Återställ [ägarskap och behörigheter för filsystem](../../installation/prerequisites/file-system/configure-permissions.md) som en användare med `root` behörighet.
1. Rensa följande kataloger:
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Kontrollera butiken i webbläsaren igen.
