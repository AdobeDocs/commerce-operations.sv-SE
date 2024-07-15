---
title: Inställningar för datamigrering
description: Lär dig hur du börjar migrera inställningar från Magento 1 till Magento 2 med  [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Inställningar för datamigrering

Läget `Settings` migrerar butiker, webbplatser och systemkonfigurationer som frakt, betalning och skatteinställningar. Enligt vår datamigrering [order](overview.md#migration-order) bör du migrera inställningarna först.

Innan du börjar utför du följande steg:

1. Logga in på programservern som [filsystemsägare](../../../installation/prerequisites/file-system/overview.md).

1. Ändra till katalogen `/bin` eller se till att den har lagts till i systemet `PATH`.

>[!NOTE]
>
>Kontrollera att Magento 2 har distribuerats i `default`-läge. Utvecklarläget kan orsaka valideringsfel i migreringsverktyget.


Mer information finns i avsnittet om [de första stegen](overview.md#first-steps).

## Kör kommandot för migrering av inställningar

Starta migrering av inställningar genom att köra:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Var:

* `[-r|--reset]` är ett valfritt argument som startar migreringen från början. Du kan använda det här argumentet för att testa migrering

* `[-a|--auto]` är ett valfritt argument som förhindrar att migreringen stoppas när integritetskontrollfel påträffas.

* `{<path to config.xml>}` är den absoluta filsystemsökvägen till migreringsverktygets [`config.xml`](../configure.md#configure-migration-in-vendor-folder)-fil. Det här argumentet är obligatoriskt.

>[!NOTE]
>
>Det här kommandot migrerar inte alla konfigurationsinställningar. Kontrollera alla inställningar i Magento 2 Admin innan du fortsätter.


Meddelandet `Migration completed` visas när inställningarna har överförts.

## Konfigurera anpassade migreringsregler

Du kan ignorera, byta namn på eller ändra systemkonfigurationerna när du migrerar inställningar. För detta anger du anpassade regler i filen `settings.xml`.

1. Logga in på programservern som, eller växla till, ägare av [filsystemet](../../../installation/prerequisites/file-system/overview.md).

1. Byt till följande katalog:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Om programmet till exempel är installerat i `/var/www/html` finns filen `settings.xml.dist` i någon av följande kataloger:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Om du vill skapa en `settings.xml`-fil från det angivna exemplet kör du:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Gör ändringarna i `settings.xml`.

1. Om du vill ange det nya namnet på inställningsfilen för mappning ändrar du taggen `<settings_map_file>` i filen `path/to/config.xml`.

Mer information finns i avsnittet [Migreringsläge för inställningar](../technical-specification.md#settings-migration-mode) i verktygets [specifikation](../technical-specification.md).

## Nästa migreringssteg

* [Migrera data](data.md)
