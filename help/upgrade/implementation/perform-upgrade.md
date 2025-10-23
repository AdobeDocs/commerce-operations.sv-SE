---
title: Uppgradera
description: Följ de här stegen för att uppgradera lokala distributioner av Adobe Commerce.
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: 4cf6f81ce43ddcccf20db12b8735f29a151d420d
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 0%

---


# Uppgradera

Du kan uppgradera _lokala_-distributioner av Adobe Commerce-programmet från kommandoraden om du har installerat programmet av:

- Hämtar Composer-metapaketet med kommandot `composer create-project`.
- Installerar det komprimerade arkivet.

>[!NOTE]
>
>- Information om projekt för molninfrastruktur finns i [Uppgradera Commerce-version](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html) i molnhandboken.
>- Använd inte den här metoden för att uppgradera om du klonade GitHub-databasen. Se [Uppgradera en Git-baserad installation](../developer/git-installs.md).

Följande instruktioner visar hur du uppgraderar med Composer-pakethanteraren. Adobe Commerce 2.4.2 har nu stöd för Composer 2. Om du försöker uppgradera från &lt;2.4.1 måste du först uppgradera till en version som är kompatibel med Composer 2 (t.ex. 2.4.2) med Composer 1 _innan_ du uppgraderar till Composer 2 för >2.4.2. Dessutom måste du köra en [version](../../installation/system-requirements.md) av PHP som stöds.

>[!WARNING]
>
>Förfarandet för uppgradering av Adobe Commerce har ändrats. Du måste installera en ny version av paketet `magento/composer-root-update-plugin` (se [Krav](../prepare/prerequisites.md)). Dessutom har kommandona för uppgradering ändrats från `composer require magento/<package_name>` till `composer require-commerce magento/<package_name>`.

## Innan du börjar

Du måste slutföra uppgraderingskraven för [uppgraderingen](../prepare/prerequisites.md) för att kunna förbereda miljön innan du startar uppgraderingsprocessen.

>[!IMPORTANT]
>
>Adobe Commerce version 2.4.6-p13 innehåller inte paketet `magento/inventory-composer-installer` som krävs för smidig uppgradering från äldre mindre versioner med bakåtkompatibla ändringar.<br>
>&#x200B;>Om du uppgraderar från 2.3 till 2.4.6-p13 kör du följande kommando för att installera paketet `magento/inventory-composer-installer` innan du uppgraderar:
>&#x200B;>`composer require magento/inventory-composer-installer`

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

   _Adobe Commerce i molninfrastrukturen :_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source :_

   ```bash
   bin/magento cron:remove
   ```

1. Starta alla meddelandekökonsumenter manuellt för att se till att alla meddelanden förbrukas.

   ```bash
   bin/magento cron:run --group=consumers
   ```

   Vänta på att kron-jobbet slutförs. Du kan övervaka statusen för jobbet med ett processvisningsprogram eller genom att köra kommandot `ps aux | grep 'bin/magento queue'` flera gånger tills alla processer är slutförda.

1. Skapa en säkerhetskopia av filen `composer.json`.

   ```bash
   cp composer.json composer.json.bak
   ```

1. Lägg till eller ta bort specifika paket utifrån dina behov.

   Om du till exempel uppgraderar från Magento Open Source till Adobe Commerce tar du bort Magento Open Source-paketet.

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   Du kan också uppgradera exempeldata.

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce :_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
     ```

   - _Magento Open Source :_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
     ```

1. Uppgradera din instans med följande `composer require-commerce`-kommandosyntax:

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   Kommandoalternativen är:

   - `<product>` —(Obligatoriskt) Paketet som ska uppgraderas. För lokala installationer måste värdet vara antingen `product-community-edition` eller `product-enterprise-edition`.

   - `<version>` —(Obligatoriskt) Den version av Adobe Commerce som du uppgraderar till. Exempel: `2.4.3`.

   - `--no-update` —(Obligatoriskt) Inaktiverar den automatiska uppdateringen av beroenden.

   - `--interactive-root-conflicts` - (Valfritt) Gör att du interaktivt kan visa och uppdatera inaktuella värden från tidigare versioner eller anpassade värden som inte matchar den version du uppgraderar till.

   - `--force-root-updates` —(Valfritt) Åsidosätter alla anpassade värden som står i konflikt med de förväntade Commerce-värdena.

   - `--help` —(Valfritt) Anger användningsinformation om plugin-programmet.

   Om varken `--interactive-root-conflicts` eller `--force-root-updates` anges behåller kommandot de befintliga värden som är i konflikt och visar ett varningsmeddelande. Mer information om plugin-programmet finns i [Viktigt om plugin-användning](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

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

Kvalitetsuppdateringar innehåller i första hand funktionella _- och_-säkerhetskorrigeringar. De kan dock ibland innehålla nya bakåtkompatibla funktioner. Använd Composer för att hämta en kvalitetskorrigering.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### Exempel - Säkerhetsuppdatering

Säkerhetsuppdateringar innehåller endast säkerhetskorrigeringar. De är utformade för att göra uppgraderingsprocessen snabbare och enklare. Säkerhetsuppdateringar använder Composer-namnkonventionen `2.4.x-px`.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
```

## Uppdatera metadata

1. Uppdatera fälten `"name"`, `"version"` och `"description"` i filen `composer.json` efter behov.

   >[!NOTE]
   >
   >Uppdatering av metadata i filen `composer.json` är helt ytliga, fungerar inte.

1. Använd uppdateringar.

   ```bash
   composer update
   ```

1. Rensa underkatalogerna `var/` och `generated/`:

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

Om programmet misslyckas med felet `We're sorry, an error has occurred while generating this email.`:

1. Återställ [filsystemets ägarskap och behörigheter](../../installation/prerequisites/file-system/configure-permissions.md) som en användare med `root`-behörighet.
1. Rensa följande kataloger:
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Kontrollera butiken i webbläsaren igen.
