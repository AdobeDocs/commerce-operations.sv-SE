---
title: Ange konfigurationsvärden
description: Lär dig hur du anger konfigurationsvärden och ändrar låsta administratörsvärden i Adobe Commerce. Upptäck avancerade konfigurationskommandon och -tekniker.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 5e2d11330d3334df36ba8b3d176fbe2d8bfe0486
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 0%

---

# Ange konfigurationsvärden

{{file-system-owner}}

I det här avsnittet beskrivs avancerade konfigurationskommandon som du kan använda för att:

- Ange ett konfigurationsalternativ från kommandoraden
- Du kan även låsa ett konfigurationsalternativ så att dess värde inte kan ändras i administratören
- Ändra ett konfigurationsalternativ som är låst i administratören

Du kan använda dessa kommandon för att ställa in Commerce-konfigurationen manuellt eller med skript. Du anger konfigurationsalternativ med hjälp av en _konfigurationssökväg_, som är en `/`-avgränsad sträng som unikt identifierar det konfigurationsalternativet. Du hittar konfigurationssökvägar i följande referenser:

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
- `bin/magento config:show` visar sparade konfigurationsvärden. Värden för krypterade inställningar visas som asterisker

## Förutsättningar

Om du vill ange ett konfigurationsvärde måste du känna till minst ett av följande:

- Konfigurationssökvägen
- Om du vill ange ett konfigurationsvärde för ett visst omfång måste du känna till omfångskoden.

  Om du vill ange ett konfigurationsvärde för standardomfånget behöver du inte göra något.

### Hitta konfigurationssökvägen

Se följande referenser:

- [Referens för känsliga och systemspecifika konfigurationssökvägar](../reference/config-reference-sens.md)
- [Referens för sökvägar för betalningskonfiguration](../reference/config-reference-payment.md)
- [Referens för andra konfigurationssökvägar](../reference/config-reference-general.md)
- [Referens för konfigurationssökvägar för Commerce Enterprise B2B-tillägg](../reference/config-reference-b2b.md)

### Hitta scopekoden

Du kan hitta scopekoden antingen i Commerce-databasen eller i Commerce Admin.

**Så här hittar du scopekoden i Admin**:

1. Logga in på administratören som en användare som kan visa webbplatser och lagra vyer.
1. Klicka på **[!UICONTROL Stores]** > Inställningar > **[!UICONTROL All Stores]**.
1. Klicka på namnet på webbplatsen eller butiksvyn i den högra rutan för att se dess kod.

   I följande bild visas ett exempel på en webbplatskod.

   ![Hämta en kod för webbplats- eller butiksvy från administratören](../../assets/configuration/website-code.png)

1. Fortsätt med [Ange värden](#set-values).

**Så här hittar du scopekoden i databasen**:

Scope-koder för webbplatser och butiksvyer lagras i Commerce-databasen i tabellerna `store_website` respektive `store`.

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

   ```
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   Använd värdet i kolumnen `code`.

1. Fortsätt med nästa avsnitt.

## Ange värden

**Så här anger du systemspecifika konfigurationsvärden**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**Så här anger du känsliga konfigurationsvärden**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path
```

I följande tabell beskrivs kommandoparametrarna för `set`:

| Parameter | Beskrivning |
| --- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--scope` | Konfigurationens omfattning. Möjliga värden är `default`, `website` eller `store`. Standardvärdet är `default`. |
| `--scope-code` | Konfigurationens omfattningskod (webbplatskod eller butiksvykod) |
| `-e or --lock-env` | Låser värdet så att det inte kan redigeras i administratören eller ändrar en inställning som redan är låst i Admin. Kommandot skriver värdet till filen `<Commerce base dir>/app/etc/env.php`. |
| `-c or --lock-config` | Låser värdet så att det inte kan redigeras i administratören eller ändrar en inställning som redan är låst i Admin. Kommandot skriver värdet till filen `<Commerce base dir>/app/etc/config.php`. Alternativet `--lock-config` skriver över `--lock-env` om du anger båda alternativen. |
| `path` | _Krävs_. Konfigurationssökvägen |
| `value` | _Krävs_. Konfigurationens värde. Även om det kan skickas som ett separat argument i ett CLI-kommando rekommenderar Adobe att du inte anger det i det ursprungliga kommandot. Kör i stället kommandot utan värdet och ange sedan värdet när du uppmanas till det. Med den här metoden går det inte att skriva känsliga åtkomstvärden till base_history, vilket är det säkraste sättet att ställa in konfigurationen. |

>[!INFO]
>
>Från och med Commerce 2.2.4 ersätter alternativen `--lock-env` och `--lock-config` alternativet `--lock`. Om du använder något av dessa alternativ skrivs värdet direkt till filen `app/etc/env.php` eller `app/etc/config.php` och blir skrivskyddat i Admin. Om du vill importera konfigurationsändringar från de här filerna till databasen kör du kommandot `bin/magento app:config:import`, till exempel efter att du har redigerat eller omdistribuerat filerna manuellt.

Om du anger en felaktig konfigurationssökväg returnerar kommandot ett fel

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

Ange bas-URL:en för webbplatsen `base`:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Ange bas-URL för butiksvyn `test`:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Ange konfigurationsvärden som inte kan redigeras i administratören

Om du använder alternativet `--lock-env` på följande sätt sparar kommandot konfigurationsvärdet i `<Commerce base dir>/app/etc/env.php` och inaktiverar fältet för redigering av det här värdet i Admin.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Du kan använda alternativet `--lock-env` för att ange konfigurationsvärden om Commerce inte är installerat. Du kan dock bara ange värden för standardomfånget.

>[!INFO]
>
>Filen `env.php` är systemspecifik. Överför den inte till ett annat system. Du kan använda den för att skriva över konfigurationsvärden från databasen. Du kan t.ex. ta en databasdump från ett annat system och skriva över `base_url` och andra värden så att du inte behöver ändra databasen.

Om du använder alternativet `--lock-config` på följande sätt sparas konfigurationsvärdet i `<Commerce base dir>/app/etc/config.php`. Fältet för redigering av det här värdet i Admin är inaktiverat.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Du kan använda `--lock-config` för att ange konfigurationsvärden om Commerce inte är installerat. Du kan dock bara ange värden för standardomfånget.

>[!INFO]
>
>Du kan överföra `config.php` till ett annat system om du vill använda samma konfigurationsvärden där. Om du till exempel har ett testsystem, innebär det att du inte behöver ange samma konfigurationsvärden igen om du använder samma `config.php`.

## Visa värdet för konfigurationsinställningarna

Kommandoalternativ:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

där

- `--scope` är konfigurationens omfattning (standard, webbplats, butik). Standardvärdet är `default`
- `--scope-code` är omfångskoden för konfigurationen (webbplatskod eller butiksvykod)
- `path` är konfigurationssökvägen i formatet first_part/second_part/third_part/etc (_required_)

>[!INFO]
>
>Kommandot `bin/magento config:show` visar värdena för alla [krypterade värden](../reference/config-reference-sens.md) som en serie asterisker: `******`.

### Exempel

**Så här visar du alla sparade konfigurationer**:

```bash
bin/magento config:show
```

Resultat:

```
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**Så här visar du alla sparade konfigurationer för `base`-webbplatsen**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Resultat:

```
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**Så här visar du bas-URL:en för standardomfånget**:

```bash
bin/magento config:show web/unsecure/base_url
```

Resultat:

```
web/unsecure/base_url - http://example.com/
```

**Så här visar du bas-URL:en för `base`-webbplatsen**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Resultat:

```
web/unsecure/base_url - http://example-for-website.com/
```

**Så här visar du bas-URL:en för `default` store**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Resultat:

```
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>Omfångskoden kan endast innehålla bokstäver (a-z eller A-Z), siffror (0-9) och understreck (_). Dessutom måste det första tecknet vara en bokstav. Om versaler eller kameravärden används när du skapar en webbplats- eller butiksvy är matchningen inte skiftlägeskänslig för att ge plats för åsidosättning av konfigurationsinställningar via systemvariabler. Se [Använd miljövariabler för att åsidosätta konfigurationsinställningar](../reference/override-config-settings.md#environment-variables).

