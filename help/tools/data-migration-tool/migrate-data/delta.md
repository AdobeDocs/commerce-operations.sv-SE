---
title: Migrera ändringar
description: Lär dig hur du migrerar endast data som har ändrats sedan din senaste datamigrering för Magento 1 med  [!DNL Data Migration Tool].
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Migrera ändringar

Med verktyget för inkrementell migrering installeras deltalogtabeller (med prefixet `m2_cl_*`) och utlösare (för att spåra ändringar) i Magento 1-databasen under [datamigreringen](data.md). Dessa tabeller och utlösare är viktiga för att du ska kunna migrera endast de ändringar som gjorts i Magento 1 sedan du senast migrerade data. Dessa ändringar är:

* Data som kunderna lagt till via butiken (skapade order, recensioner och ändringar i kundprofiler)

* Alla åtgärder med order, produkter och kategorier på panelen Admin

>[!NOTE]
>
>Alla andra nya eller uppdaterade enheter som anges via administratören, till exempel attribut eller CMS-sidor, ingår inte i den stegvisa migreringen och migreras inte.


Innan du börjar utför du följande steg:

1. Logga in på programservern som [ägare av filsystemet](../../../installation/prerequisites/file-system/overview.md).
1. Ändra till katalogen `/bin` eller se till att den har lagts till i systemet `PATH`.

Mer information finns i avsnittet om [de första stegen](overview.md#first-steps).

## Kör kommandot för stegvis migrering

Om du vill börja migrera stegvisa ändringar kör du:

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Var:

* `[-r|--reset]` är ett valfritt argument som startar migreringen från början. Du kan använda det här argumentet för att testa migrering.

* `[-a|--auto]` är ett valfritt argument som förhindrar att migreringen stoppas när integritetskontrollfel påträffas.

* `{<path to config.xml>}` är den absoluta filsystemsökvägen till `config.xml`. Det här argumentet är obligatoriskt.

>[!NOTE]
>
>Inkrementell migrering är en kontinuerlig process som startas om automatiskt var femte sekund. Använd CTRL-C för att avbryta migreringsprocessen.


## Migrera data som skapats av tillägg från tredje part

I `Delta`-läget migrerar [!DNL Data Migration Tool] endast data som skapats av Magento egna moduler och ansvarar inte för koden eller tilläggen som skapats av tredjepartsutvecklare. Om dessa tillägg skapade data i storefront-databasen och handlaren vill ha dessa data i Magento 2, ska konfigurationsfilerna för [!DNL Data Migration Tool] skapas och ändras i enlighet med detta.

Om ett tillägg har egna tabeller, och du behöver spåra ändringar för deltamigrering, gör du så här:

1. Lägg till de tabeller som ska spåras i filen `deltalog.xml`
1. Skapa en ytterligare delta-klass som utökar `Migration\App\Step\AbstractDelta`
1. Lägg till namnet på den nyligen skapade klassen i delta-lägesavsnittet i `config.xml`
