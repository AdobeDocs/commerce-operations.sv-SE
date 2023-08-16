---
title: Migreringsöversikt
description: Lär dig hur du börjar migrera data från Magento 1 till Magento 2 med [!DNL Data Migration Tool].
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Migreringsöversikt

Innan du startar migreringen ska du stoppa alla kron-jobb i Magento 1.

Följ följande allmänna regler för en lyckad migrering under migreringsprocessen:

1. **Gör inte** göra ändringar i Magento 1 Admin, utom för orderhantering (frakt, skapa faktura och kreditnotor)
1. **Gör inte** ändra kod
1. **Gör inte** gör ändringar i Magento 2 Admin och storefront

>[!TIP]
>
>Alla åtgärder i Magento 1-butiken är tillåtna.

## Kör [!DNL Data Migration Tool]

I det här avsnittet visas hur du kör [!DNL Data Migration Tool] om du vill migrera inställningar, data eller inkrementella ändringar.

### Första steget

1. Logga in på programservern som, eller växla till, en användare med behörighet att skriva till filsystemet. Se [växla till filsystemets ägare](../../../installation/prerequisites/file-system/overview.md).

   Om du använder basskalet kan du använda följande syntax för att växla till filsystemets ägare och ange kommandot samtidigt:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Om filsystemets ägare inte tillåter inloggningar kan du göra följande:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Om du vill köra Magento-kommandon från en katalog lägger du till `<magento_root>/bin` till ditt system `PATH`.

   Eftersom skal har olika syntax bör du använda en referens som [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Exempel på basgränssnitt för CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Du kan också köra kommandona på följande sätt:

   - `cd <magento_root>/bin` och kör dem som `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` är en underkatalog till webbserverns docroot.

### Kommandosyntax

Nedan visas ett typiskt kommandoexempel:

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Var:

- `<mode>` kan vara: [`settings`](settings.md), [`data`](data.md), eller [`delta`](delta.md)
- `[-r|--reset]` är ett valfritt argument som startar migreringen från början. Du kan använda det här argumentet för att testa migrering.
- `[-a|--auto]` är ett valfritt argument som förhindrar att migreringen stoppas när integritetskontrollfel påträffas.
- `{<path to config.xml>}` är den absoluta filsystemsökvägen till `config.xml`; det här argumentet krävs.

>[!NOTE]
>
>Loggar skrivs till `<magento_root>/var/` katalog.


## Migreringsorder

När vi skapade [!DNL Data Migration Tool]antog vi följande dataöverföringssekvens:

1. [Inställningar](settings.md)
1. [Data](data.md)
1. [Ändringar](delta.md)

Vi rekommenderar starkt att du migrerar data i samma ordning.
