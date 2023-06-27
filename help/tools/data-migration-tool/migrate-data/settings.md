---
title: Inställningar för datamigrering
description: Lär dig hur du börjar migrera inställningar från Magento 1 till Magento 2 med [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Inställningar för datamigrering

The `Settings` Läget migrerar butiker, webbplatser och systemkonfigurationer som frakt, betalning och skatteinställningar. Enligt vår datamigrering [order](overview.md#migration-order)bör du migrera inställningarna först.

Innan du börjar utför du följande steg:

1. Logga in på programservern som [ägare av filsystem](../../../installation/prerequisites/file-system/overview.md).

1. Ändra till `/bin` eller se till att den läggs till i systemet `PATH`.

>[!NOTE]
>
>Se till att Magento 2 distribueras i `default` läge. Utvecklarläget kan orsaka valideringsfel i migreringsverktyget.


Se [första steget](overview.md#first-steps) för mer information.

## Kör kommandot för migrering av inställningar

Starta migrering av inställningar genom att köra:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Var:

* `[-r|--reset]` är ett valfritt argument som startar migreringen från början. Du kan använda det här argumentet för att testa migrering

* `[-a|--auto]` är ett valfritt argument som förhindrar att migreringen stoppas när integritetskontrollfel påträffas.

* `{<path to config.xml>}` är den absoluta filsystemsökvägen till migreringsverktygets [`config.xml`](../configure.md#configure-migration-in-vendor-folder) fil, det här argumentet är obligatoriskt.

>[!NOTE]
>
>Det här kommandot migrerar inte alla konfigurationsinställningar. Kontrollera alla inställningar i Magento 2 Admin innan du fortsätter.


The `Migration completed` visas när inställningarna har överförts.

## Konfigurera anpassade migreringsregler

Du kan ignorera, byta namn på eller ändra systemkonfigurationerna när du migrerar inställningar. För detta anger du dina anpassade regler i `settings.xml` -fil.

1. Logga in på programservern som eller växla till [ägare av filsystem](../../../installation/prerequisites/file-system/overview.md).

1. Ändra till följande katalog:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Om programmet till exempel är installerat i `/var/www/html`, `settings.xml.dist` filen finns i någon av följande kataloger:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Skapa en `settings.xml` från exempelfilen, kör:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Gör ändringarna i `settings.xml`.

1. Om du vill ange det nya namnet på inställningsfilen för mappning ändrar du `<settings_map_file>` -taggen i `path/to/config.xml` -fil.

Mer information finns i [Migreringsläge för inställningar](../technical-specification.md#settings-migration-mode) i verktygets [specifikation](../technical-specification.md).

## Nästa migreringssteg

* [Migrera data](data.md)
