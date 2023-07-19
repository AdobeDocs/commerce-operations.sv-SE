---
title: Ange konfigurationsvärden
description: Lär dig hur du anger konfigurationsvärden och ändrar värden som är låsta i Admin.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 78a7e99ecaba6a6f7982123f5bd67efc740ec2ef
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---

# Ange konfigurationsvärden

{{file-system-owner}}

I det här avsnittet beskrivs avancerade konfigurationskommandon som du kan använda för att:

- Ange ett konfigurationsalternativ från kommandoraden
- Du kan även låsa ett konfigurationsalternativ så att dess värde inte kan ändras i administratören
- Ändra ett konfigurationsalternativ som är låst i administratören

Du kan använda dessa kommandon för att ställa in Commerce-konfigurationen manuellt eller med skript. Du anger konfigurationsalternativ med en _konfigurationssökväg_, som är en `/`-avgränsad sträng som unikt identifierar det konfigurationsalternativet. Du hittar konfigurationssökvägar i följande referenser:

- [Referens för känsliga och systemspecifika konfigurationssökvägar](../reference/config-reference-sens.md)
- [Referens för sökvägar för betalningskonfiguration](../reference/config-reference-payment.md)
- [Allmän referens för konfigurationssökvägar](../reference/config-reference-general.md)
- [Referens för konfigurationssökvägar för Commerce Enterprise B2B-tillägg](../reference/config-reference-b2b.md)

Du kan ange värden vid följande tidpunkter:

- Innan du installerar Commerce kan du bara ange konfigurationsvärden för standardomfånget eftersom det är det enda giltiga omfånget.

- När du har installerat Commerce kan du ange konfigurationsvärden för alla webbplatser och butiksvyer.

Använd följande kommandon:

- `bin/magento config:set` anger alla icke-känsliga konfigurationsvärden med dess konfigurationssökväg
- `bin/magento config:sensitive:set` anger alla känsliga konfigurationsvärden med dess konfigurationssökväg
- `bin/magento config:show` visar sparade konfigurationsvärden, värden för krypterade inställningar visas som asterisker

## Förutsättningar

Om du vill ange ett konfigurationsvärde måste du känna till minst ett av följande:

- Konfigurationssökvägen
- Om du vill ange ett konfigurationsvärde för ett visst omfång måste du känna till omfångskoden.

  Om du vill ange ett konfigurationsvärde för standardomfånget behöver du inte göra något.

### Hitta konfigurationssökvägen

Se följande referenser:

- [Referens för känsliga och systemspecifika konfigurationssökvägar](../reference/config-reference-sens.md)
- [Referens för sökvägar för betalningskonfiguration](../reference/config-reference-payment.md)
- [Andra konfigurationssökvägar - referens](../reference/config-reference-general.md)
- [Referens för konfigurationssökvägar för Commerce Enterprise B2B-tillägg](../reference/config-reference-b2b.md)

### Hitta scopekoden

Du kan hitta scopekoden antingen i Commerce-databasen eller i Commerce Admin.

**Så här hittar du scopekoden i Admin**:

1. Logga in på administratören som en användare som kan visa webbplatser och lagra vyer.
1. Klicka **[!UICONTROL Stores]** > Inställningar > **[!UICONTROL All Stores]**.
1. Klicka på namnet på webbplatsen eller butiksvyn i den högra rutan för att se dess kod.

   I följande bild visas ett exempel på en webbplatskod.

   ![Hämta en webbplats eller butiksvykod från administratören](../../assets/configuration/website-code.png)

1. Fortsätt med [Ange värden](#set-values).

**Så här hittar du scopekoden i databasen**:

Omfångskoder för webbplatser och butiksvyer lagras i Commerce-databasen i `store_website` och `store` tabeller.

1. Anslut till Commerce-databasen.

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. Ange följande kommandon:

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   Ett exempelresultat följer:

   ```terminal
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   Använd värdet i `code` kolumn.

1. Fortsätt med nästa avsnitt.

## Ange värden

**Ange systemspecifika konfigurationsvärden**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**Ange känsliga konfigurationsvärden**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

I följande tabell beskrivs `set` kommandoparametrar:

| Parameter | Beskrivning |
| --- | --- |
| `--scope` | Konfigurationens omfattning. Möjliga värden är `default`, `website`, eller `store`. Standardvärdet är `default`. |
| `--scope-code` | Konfigurationens omfattningskod (webbplatskod eller butiksvykod) |
| `-e or --lock-env` | Låser värdet så att det inte kan redigeras i administratören eller ändrar en inställning som redan är låst i Admin. Kommandot skriver värdet till `<Commerce base dir>/app/etc/env.php` -fil. |
| `-c or --lock-config` | Låser värdet så att det inte kan redigeras i administratören eller ändrar en inställning som redan är låst i Admin. Kommandot skriver värdet till `<Commerce base dir>/app/etc/config.php` -fil. The `--lock-config` alternativ skriver över `--lock-env` om du anger båda alternativen. |
| `path` | _Obligatoriskt_. Konfigurationssökvägen |
| `value` | _Obligatoriskt_. Konfigurationens värde |

>[!INFO]
>
>Från och med Commerce 2.2.4 `--lock-env` och `--lock-config` alternativ ersätta `--lock` alternativ.
>
>Om du använder `--lock-env` eller `--lock-config` om du vill ange eller ändra ett värde måste du använda [`bin/magento app:config:import` kommando](../cli/import-configuration.md) om du vill importera inställningen innan du öppnar Admin eller Storefront.

Om du anger en felaktig konfigurationssökväg returnerar det här kommandot ett fel

```text
The "wrong/config/path" does not exist
```

Se något av följande avsnitt för mer information:

- [Ange konfigurationsvärden som kan redigeras i administratören](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Ange konfigurationsvärden som inte kan redigeras i administratören](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Ange konfigurationsvärden som kan redigeras i administratören

Använd `bin/magento config:set` _utan_ `--lock-env` eller `--lock-config` för att skriva värdet till databasen. Värden som du anger på det här sättet kan redigeras i Admin.

Här följer några exempel på hur du anger en bas-URL för butik:

Ange bas-URL för standardomfånget:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Ange bas-URL för `base` webbplats:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Ange bas-URL för `test` butiksvy:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Ange konfigurationsvärden som inte kan redigeras i administratören

Om du använder `--lock-env`  enligt följande sparar kommandot konfigurationsvärdet i `<Commerce base dir>/app/etc/env.php` och inaktiverar fältet för redigering av det här värdet i Admin.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Du kan använda `--lock-env` alternativ för att ange konfigurationsvärden om Commerce inte är installerat. Du kan dock bara ange värden för standardomfånget.

>[!INFO]
>
>The `env.php` filen är systemspecifik. Du bör inte överföra den till ett annat system. Du kan använda den för att skriva över konfigurationsvärden från databasen. Du kan t.ex. ta en databasdump från ett annat system och skriva över `base_url` och andra värden så att du inte behöver ändra databasen.

Om du använder `--lock-config` enligt följande sparas konfigurationsvärdet i `<Commerce base dir>/app/etc/config.php`. Fältet för redigering av det här värdet i Admin är inaktiverat.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Du kan använda `--lock-config` för att ange konfigurationsvärden om Commerce inte är installerat. Du kan dock bara ange värden för standardomfånget.

>[!INFO]
>
>Du kan överföra `config.php` till ett annat system för att använda samma konfigurationsvärden där. Om du till exempel har ett testsystem använder du samma `config.php` betyder att du inte behöver ange samma konfigurationsvärden igen.

## Visa värdet för konfigurationsinställningarna

Kommandoalternativ:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

där

- `--scope` är omfattningen av konfigurationen (standard, webbplats, butik). Standardvärdet är `default`
- `--scope-code` är konfigurationens omfattningskod (webbplatskod eller butiksvykod).
- `path` är konfigurationssökvägen i formatet first_part/second_part/third_part/etc (_obligatoriskt_)

>[!INFO]
>
>The `bin/magento config:show` -kommandot visar värdena för [krypterade värden](../reference/config-reference-sens.md) som en serie asterisker: `******`.

### Exempel

**Visa alla sparade konfigurationer**:

```bash
bin/magento config:show
```

Resultat:

```terminal
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**Visa alla sparade konfigurationer för `base` webbplats**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Resultat:

```terminal
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**Visa bas-URL:en för standardomfånget**:

```bash
bin/magento config:show web/unsecure/base_url
```

Resultat:

```terminal
web/unsecure/base_url - http://example.com/
```

**Visa bas-URL:en för `base` webbplats**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Resultat:

```terminal
web/unsecure/base_url - http://example-for-website.com/
```

**Visa bas-URL:en för `default` store**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Resultat:

```terminal
web/unsecure/base_url - http://example-for-store.com/
```
