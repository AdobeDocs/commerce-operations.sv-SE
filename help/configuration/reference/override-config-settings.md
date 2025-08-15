---
title: Åsidosätt konfigurationsinställningar
description: Lär dig hur du använder miljövariabler för att åsidosätta konfigurationsinställningar.
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---

# Åsidosätt konfigurationsinställningar

I det här avsnittet beskrivs hur du härleder ett miljövariabelnamn med hjälp av en konfigurationssökväg. Du kan åsidosätta Adobe Commerce konfigurationsinställningar med hjälp av systemvariabler. Du kan till exempel åsidosätta värdet för en betalares live-URL i produktionssystemet.

Du kan åsidosätta värdet för konfigurationsinställningen _any_ med hjälp av systemvariabler, men Adobe rekommenderar att du behåller konsekventa inställningar med hjälp av den delade konfigurationsfilen `config.php` och den systemspecifika konfigurationsfilen `env.php`, vilket beskrivs i [Allmän distributionsöversikt](../deployment/overview.md).

>[!TIP]
>
>Ta en titt på ämnet [Konfigurera miljöer](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html?lang=sv-SE) i guiden _Commerce om molninfrastruktur_.

## Miljövariabler

Ett miljövariabelnamn består av dess omfång följt av dess konfigurationssökväg i ett visst format. I följande avsnitt beskrivs mer ingående hur du fastställer ett variabelnamn.

Du kan använda variabler för något av följande:

- [Känsliga värden](config-reference-sens.md) måste anges med antingen miljövariabler eller kommandot [`magento config:sensitive:set`](../cli/set-configuration-values.md).
- Systemspecifika värden måste anges med:

   - Miljövariabler
   - Kommandot [`magento config:set`](../cli/set-configuration-values.md)
   - Admin följt av kommandot [`magento app:config:dump`](../cli/export-configuration.md)

Konfigurationssökvägar finns i:

- [Referens för känsliga och systemspecifika konfigurationssökvägar](config-reference-sens.md)
- [Referens för sökvägar för betalningskonfiguration](config-reference-payment.md)
- [Referens för konfigurationssökvägar för Commerce B2B-tillägg](config-reference-b2b.md)
- [Referens för andra konfigurationssökvägar](config-reference-general.md)

### Variabelnamn

Det allmänna formatet för systeminställningens variabelnamn följer:

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` kan vara antingen:

- Global omfattning (d.v.s. den globala inställningen för _alla_ scope)

  Globala omfångsvariabler har följande format:

  `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Ett specifikt omfång (d.v.s. inställningen påverkar bara en viss butiksvy eller webbplats)

  Omfångsvariabler för butiksvyn har till exempel följande format:

  `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

  Mer information om omfång finns i:

   - [Steg 1: Hitta omfångsvärdet för webbplatsen eller butiksvyn](#step-1-find-the-website-or-store-view-scope-value)
   - [Commerce User Guide topic on scope](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/setup/websites-stores-views#scope-settings)
   - [Snabbreferens för omfång](https://experienceleague.adobe.com/sv/docs/commerce-admin/config/scope-change#scope-quick-reference)

`<SYSTEM__VARIABLE__NAME>` är konfigurationssökvägen med två understreck i stället för `/`. Mer information finns i [Steg 2: Ange systemvariabler](#step-2-set-global-website-or-store-view-variables).

### Variabelformat

`<SCOPE>` separeras från `<SYSTEM__VARIABLE__NAME>` med två understreck.

`<SYSTEM__VARIABLE__NAME>` härleds från en konfigurationsinställnings _konfigurationssökväg_, som är en `/` avgränsad sträng som unikt identifierar en viss inställning. Ersätt varje `/`-tecken i konfigurationssökvägen med två understreck för att skapa systemvariabeln.

Om en konfigurationssökväg innehåller ett understreck finns understreck kvar i variabeln.

En fullständig lista över konfigurationssökvägar finns i:

- [Referens för känsliga och systemspecifika konfigurationssökvägar](config-reference-sens.md)
- [Referens för sökvägar för betalningskonfiguration](config-reference-payment.md)
- [Referens för konfigurationssökvägar för Commerce Enterprise B2B-tillägg](config-reference-b2b.md)
- [Referens för andra konfigurationssökvägar](config-reference-general.md)

## Steg 1: Hitta omfångsvärdet för webbplatsen eller butiksvyn

I det här avsnittet beskrivs hur du kan hitta och ange systemkonfigurationsvärden per _scope_ (butiksvy eller webbplats). Information om hur du anger globala omfångsvariabler finns i [Steg 2: Ange globala variabler, webbplatsvariabler eller butiksvyvariabler](#step-2-set-global-website-or-store-view-variables).

Omfångsvärden kommer från tabellerna `store`, `store_group` och `store_website`.

- Tabellen `store` anger namn och koder för butiksvyn
- Tabellen `store_website` anger webbplatsnamn och koder

Du kan också hitta kodvärdena med hjälp av Admin.

Så här läser du tabellen:

- `Path in Admin`-kolumn

  Värden före kommatecken är sökvägar i Admin-navigeringen. Värden efter kommatecken är alternativ i den högra rutan.

- `Variable name`-kolumnen är namnet på motsvarande miljövariabel.

  Du kan ange systemvärden för dessa konfigurationsparametrar som systemvariabler om du vill.

   - Hela variabelnamnet är alltid ALL CAPS
   - Starta ett variabelnamn med `CONFIG__` (observera två understreck)
   - Du kan hitta delen `<STORE_VIEW_CODE>` eller `<WEBSITE_CODE>` av ett variabelnamn i antingen Admin- eller Commerce-databasen, vilket visas i följande avsnitt.
   - Du kan hitta `<SYSTEM__VARIABLE__NAME>` enligt beskrivningen i [Steg 2: Ange globala variabler, webbplatsvariabler eller butiksvyvariabler](#step-2-set-global-website-or-store-view-variables).

### Hitta en webbplats eller ett butiksvyomfång i administratören

I följande tabell sammanfattas hur du söker efter webbplatsvyvärden eller butiksvyvärden i Admin.

| Beskrivning | Sökväg i Admin | Variabelnamn |
|--------------|--------------|----------------------|
| Skapa, redigera och ta bort butiksvyer | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Skapa, redigera och ta bort webbplatser | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

Om du till exempel vill hitta ett värde för webbplatsens eller butikens visningsomfång i Admin:

1. Logga in på administratören som en användare som har behörighet att visa webbplatser.
1. Klicka på **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Klicka på namnet på en webbplats eller butiksvy.

   Den högra rutan visas på ungefär följande sätt.

   ![Hitta en webbplatskod](../../assets/configuration/website-code.png)

1. Omfångsnamnet visas i fältet **[!UICONTROL Code]**.
1. Fortsätt med [Steg 2: Ange globala variabler, webbplatsvariabler eller butiksvyvariabler](#step-2-set-global-website-or-store-view-variables).

### Söka efter en webbplats eller en butiksvy i databasen

Så här hämtar du dessa värden från databasen:

1. Logga in på utvecklingssystemet som filsystemsägare om du inte redan har gjort det.
1. Ange följande kommando:

   ```bash
   mysql -u <database-username> -p
   ```

1. Vid uppmaningen `mysql>` anger du följande kommandon i den ordning som visas:

   ```shell
   use <database-name>;
   ```

1. Använd följande SQL-frågor för att hitta relevanta värden:

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   Ett exempel följer:

   ```shell
   mysql> SELECT * FROM STORE_WEBSITE;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

1. Använd värdet från kolumnen `code` som scopenamn, inte värdet `name`.

   Om du till exempel vill ange en konfigurationsvariabel för Testwebbplats använder du följande format:

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   där `<SYSTEM__VARIABLE__NAME>` kommer från nästa avsnitt.

## Steg 2: Ange globala variabler, webbplatsvariabler eller butiksvyvariabler

I det här avsnittet beskrivs hur du ställer in systemvariabler.

- Om du vill ange värden för det globala omfånget (dvs. alla webbplatser, butiker och butiksvyer) startar du variabelnamnet med `CONFIG__DEFAULT__`.

- Om du vill ange ett värde för en viss butiksvy eller webbplats startar du variabelnamnet enligt beskrivningen i [Steg 1: Hitta omfångsvärdet](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- Den sista delen av variabelnamnet är konfigurationssökvägen, som är unik för varje konfigurationsinställning.

[Se några exempel](#examples).

I följande tabell visas några exempelvariabler.

| Beskrivning | Sökväg i Admin (utelämnar **Lagrar** > **Inställningar** > **Konfiguration**) | Variabelnamn |
|--------------|--------------|----------------------|
| Elasticsearch servervärdnamn | Katalog > **Katalog**, **värdnamn för Elasticsearch-server** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearch serverport | Katalog > **Katalog**, **Elasticsearch Server-port** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Leveranslands ursprung | Försäljning > **Leveransinställningar** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| URL för anpassad administratör | Avancerat > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Anpassad administratörssökväg | Avancerat > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Exempel

I det här avsnittet visas hur du söker efter värden för vissa exempelvariabler.

### Elasticsearch servervärdnamn

Så här hittar du variabelnamnet för den globala HTML-miniatyrbilden:

1. Bestäm omfattningen.

   Det är det globala omfånget så variabelnamnet börjar med `CONFIG__DEFAULT__`

1. Resten av variabelnamnet är `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Resultat**: Variabelnamnet är `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Leveranslands ursprung

Så här hittar du variabelnamnet för ursprungsland:

1. Bestäm omfattningen.

   Hitta omfånget i [databasen](#find-a-website-or-store-view-scope-in-the-database) enligt beskrivningen i steg 1: Hitta omfångsvärdet för webbplatsen eller butiksvyn. (Du kan också hitta värdet i Admin enligt tabellen [i steg 2: Ange globala variabler, webbplatsvariabler eller butiksvyvariabler ]&#x200B;(#step-2-set-global-website-or-store-view-variables.)

   Omfånget kan till exempel vara `CONFIG__WEBSITES__DEFAULT`.

1. Resten av variabelnamnet är `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Resultat**: Variabelnamnet är `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Så här använder du miljövariabler

Ange konfigurationsvärden som variabler med PHP:s [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) -associerade array. Du kan ange värden i alla PHP-skript som körs när Commerce körs.

>[!TIP]
>
>Att ange variabelvärden i `index.php` eller `pub/index.php` fungerar inte alltid som förväntat eftersom olika programstartpunkter kan användas beroende på webbserverkonfigurationen. Genom att placera `$_ENV` direktiv i filen `app/bootstrap.php`, oavsett vilka programstartpunkter som är olika, körs alltid `$_ENV` -direktiven eftersom filen `app/bootstrap.php` läses in som en del av Commerce-arkitekturen.

Ett exempel på hur du ställer in två `$_ENV`-värden följer:

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Ett steg-för-steg-exempel visas i [Ange konfigurationsvärden med hjälp av miljövariabler](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- Om du vill använda värden som du anger i `$_ENV`-arrayen måste du ange `variables_order = "EGPCS"`(Environment, Get, Post, Cookie och Server) i `php.ini`-filen. Mer information finns i [PHP-dokumentation](https://www.php.net/manual/en/ini.core.php).
>
>- Om du försöker åsidosätta konfigurationsinställningarna med [Project Web Interface](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=sv-SE#configure-the-project) för Adobe Commerce i molninfrastruktur måste du lägga till variabelnamnet som `env:`. Exempel:
>
>![Exempel på miljövariabel](../../assets/configuration/cloud-console-envvariable.png)
