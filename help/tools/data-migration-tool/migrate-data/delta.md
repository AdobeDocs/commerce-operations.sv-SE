---
title: Migrera ändringar
description: Lär dig hur du migrerar endast data som har ändrats sedan den senaste datamigreringen för Magento 1 med [!DNL Data Migration Tool].
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# Migrera ändringar

Med verktyget för inkrementell migrering installerar du deltabeller (med prefix) `m2_cl_*`) och utlösare (för att spåra ändringar) i Magento 1-databasen under [migrering av data](data.md). Dessa tabeller och utlösare är viktiga för att du ska kunna migrera endast de ändringar som gjorts i Magento 1 sedan du senast migrerade data. Dessa ändringar är:

* Data som kunderna lagt till via butiken (skapade order, recensioner och ändringar i kundprofiler)

* Alla åtgärder med order, produkter och kategorier på panelen Admin

>[!NOTE]
>
>Alla andra nya eller uppdaterade enheter som anges via administratören, till exempel attribut eller CMS-sidor, ingår inte i den stegvisa migreringen och migreras inte.


Innan du börjar utför du följande steg:

1. Logga in på programservern som [filsystemets ägare](../../../installation/prerequisites/file-system/overview.md).
1. Ändra till `/bin` eller se till att den läggs till i systemet `PATH`.

Se [första steget](overview.md#first-steps) för mer information.

## Kör kommandot för stegvis migrering

Om du vill börja migrera stegvisa ändringar kör du:

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Var:

* `[-r|--reset]` är ett valfritt argument som startar migreringen från början. Du kan använda det här argumentet för att testa migrering.

* `[-a|--auto]` är ett valfritt argument som förhindrar att migreringen stoppas när integritetskontrollfel påträffas.

* `{<path to config.xml>}` är den absoluta filsystemsökvägen till `config.xml`; det här argumentet är obligatoriskt.

>[!NOTE]
>
>Inkrementell migration är en kontinuerlig process. startas om automatiskt var femte sekund. Använd CTRL-C för att avbryta migreringsprocessen.


## Migrera data som skapats av tillägg från tredje part

I `Delta` läge, [!DNL Data Migration Tool] migrerar data som bara skapats av Magento egna moduler och ansvarar inte för kod eller tillägg som skapats av tredjepartsutvecklare. Om dessa tillägg skapade data i storefront-databasen och handlaren vill ha dessa data i Magento 2 - konfigurationsfiler för [!DNL Data Migration Tool] bör skapas och ändras i enlighet med detta.

Om ett tillägg har egna tabeller, och du behöver spåra ändringar för deltamigrering, gör du så här:

1. Lägg till de tabeller som ska spåras i `deltalog.xml` fil
1. Skapa ytterligare en delta-klass som utökar `Migration\App\Step\AbstractDelta`
1. Lägg till namnet på den nyligen skapade klassen i delta-lägesavsnittet i `config.xml`
