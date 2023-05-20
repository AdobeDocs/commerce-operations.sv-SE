---
title: Åsidosätt konfigurationsinställningar
description: Lär dig hur du använder miljövariabler för att åsidosätta konfigurationsinställningar.
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 0%

---

# Åsidosätt konfigurationsinställningar

I det här avsnittet beskrivs hur du härleder ett miljövariabelnamn med hjälp av en konfigurationssökväg. Du kan åsidosätta Adobe Commerce konfigurationsinställningar med hjälp av systemvariabler. Du kan till exempel åsidosätta värdet för en betalares live-URL i produktionssystemet.

Du kan åsidosätta värdet för _alla_ konfigurationsinställning med hjälp av miljövariabler, Adobe rekommenderar dock att du använder den delade konfigurationsfilen för att behålla konsekventa inställningar. `config.php`och den systemspecifika konfigurationsfilen, `env.php`som beskrivs i [Allmän översikt över distribution](../deployment/overview.md).

>[!TIP]
>
>Kolla in [Konfigurera miljöer](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) ämne i _Guide för Commerce on Cloud Infrastructure_.

## Miljövariabler

Ett miljövariabelnamn består av dess omfång följt av dess konfigurationssökväg i ett visst format. I följande avsnitt beskrivs mer ingående hur du fastställer ett variabelnamn.

Du kan använda variabler för något av följande:

- [Känsliga värden](config-reference-sens.md) måste anges med antingen miljövariabler eller [`magento config:sensitive:set`](../cli/set-configuration-values.md) -kommando.
- Systemspecifika värden måste anges med:

   - Miljövariabler
   - The [`magento config:set`](../cli/set-configuration-values.md) kommando
   - Admin följt av [`magento app:config:dump` kommando](../cli/export-configuration.md)

Konfigurationssökvägar finns i:

- [Referens för känsliga och systemspecifika konfigurationssökvägar](config-reference-sens.md)
- [Referens för sökvägar för betalningskonfiguration](config-reference-payment.md)
- [Referens för konfigurationssökvägar för tillägg i Commerce B2B](config-reference-b2b.md)
- [Andra konfigurationssökvägar - referens](config-reference-general.md)

### Variabelnamn

Det allmänna formatet för systeminställningens variabelnamn följer:

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` kan antingen vara:

- Global omfattning (d.v.s. den globala inställningen för _alla_ scope)

   Globala omfångsvariabler har följande format:

   `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Ett specifikt omfång (d.v.s. inställningen påverkar bara en viss butiksvy eller webbplats)

   Omfångsvariabler för butiksvyn har till exempel följande format:

   `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

   Mer information om omfång finns i:

   - [Steg 1: Hitta värdet för webbplatsens eller butikens vyomfång](#step-1-find-the-website-or-store-view-scope-value)
   - [Ämne i Commerce User Guide om omfattning](https://docs.magento.com/user-guide/configuration/scope.html)
   - [Snabbreferens för omfång](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` är konfigurationssökvägen med två understreck istället för `/`. Mer information finns i [Steg 2: Ange systemvariabler](#step-2-set-global-website-or-store-view-variables).

### Variabelformat

`<SCOPE>` separeras från `<SYSTEM__VARIABLE__NAME>` med två understreck.

`<SYSTEM__VARIABLE__NAME>` härleds från en konfigurationsinställnings _konfigurationssökväg_, som är en `/` avgränsad sträng som unikt identifierar en viss inställning. Ersätt varje `/` i konfigurationssökvägen med två understreck för att skapa systemvariabeln.

Om en konfigurationssökväg innehåller ett understreck finns understreck kvar i variabeln.

En fullständig lista med konfigurationssökvägar finns i:

- [Referens för känsliga och systemspecifika konfigurationssökvägar](config-reference-sens.md)
- [Referens för sökvägar för betalningskonfiguration](config-reference-payment.md)
- [Referens för konfigurationssökvägar för Commerce Enterprise B2B-tillägg](config-reference-b2b.md)
- [Andra konfigurationssökvägar - referens](config-reference-general.md)

## Steg 1: Hitta värdet för webbplatsens eller butikens vyomfång

I det här avsnittet beskrivs hur du kan hitta och ange systemkonfigurationsvärden per _omfång_ (butiksvy eller webbplats). Information om hur du anger globala omfångsvariabler finns i [Steg 2: Ange globala variabler, webbplatsvariabler eller butiksvyvariabler](#step-2-set-global-website-or-store-view-variables).

Omfångsvärden kommer från `store`, `store_group`och `store_website` tabeller.

- The `store` table specifies store view names and codes
- The `store_website` tabellen anger webbplatsnamn och koder

Du kan också hitta kodvärdena med hjälp av Admin.

Så här läser du tabellen:

- `Path in Admin` kolumn

   Värden före kommatecken är sökvägar i Admin-navigeringen. Värden efter kommatecken är alternativ i den högra rutan.

- `Variable name` -kolumnen är namnet på motsvarande miljövariabel.

   Du kan ange systemvärden för dessa konfigurationsparametrar som systemvariabler om du vill.

   - Hela variabelnamnet är alltid ALL CAPS
   - Starta ett variabelnamn med `CONFIG__` (observera två understreck)
   - Du hittar `<STORE_VIEW_CODE>` eller `<WEBSITE_CODE>` del av ett variabelnamn i antingen Admin- eller Commerce-databasen, enligt vad som anges i följande avsnitt.
   - Du kan hitta `<SYSTEM__VARIABLE__NAME>` enligt [Steg 2: Ange globala variabler, webbplatsvariabler eller butiksvyvariabler](#step-2-set-global-website-or-store-view-variables).

### Hitta en webbplats eller ett butiksvyomfång i administratören

I följande tabell sammanfattas hur du söker efter webbplatsvyvärden eller butiksvyvärden i Admin.

| Beskrivning | Sökväg i Admin | Variabelnamn |
|--------------|--------------|----------------------|
| Skapa, redigera och ta bort butiksvyer | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Skapa, redigera och ta bort webbplatser | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

Om du till exempel vill hitta ett värde för webbplatsens eller butikens visningsomfång i Admin:

1. Logga in på administratören som en användare som har behörighet att visa webbplatser.
1. Klicka **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Klicka på namnet på en webbplats eller butiksvy.

   Den högra rutan visas på ungefär följande sätt.

   ![Hitta en webbplatskod](../../assets/configuration/website-code.png)

1. Omfångsnamnet visas i **[!UICONTROL Code]** fält.
1. Fortsätt med [Steg 2: Ange globala variabler, webbplatsvariabler eller butiksvyvariabler](#step-2-set-global-website-or-store-view-variables).

### Söka efter en webbplats eller en butiksvy i databasen

Så här hämtar du dessa värden från databasen:

1. Logga in på utvecklingssystemet som filsystemsägare om du inte redan har gjort det.
1. Ange följande kommando:

   ```bash
   mysql -u <database-username> -p
   ```

1. På `mysql>` anger du följande kommandon i den ordning som visas:

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

1. Använd värdet från `code` kolumn som scopenamn, inte `name` värde.

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

| Beskrivning | Sökväg i administratören (utelämnar) **Lager** > **Inställningar** > **Konfiguration**) | Variabelnamn |
|--------------|--------------|----------------------|
| Värdnamn för Elasticsearch-server | Katalog > **Katalog**, **Värdnamn för Elasticsearch Server** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearch serverport | Katalog > **Katalog**, **Elasticsearch Server-port** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Leveranslands ursprung | Försäljning > **Leveransinställningar** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| URL för anpassad administratör | Avancerat > **Administratör** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Anpassad administratörssökväg | Avancerat > **Administratör** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Exempel

I det här avsnittet visas hur du söker efter värden för vissa exempelvariabler.

### Värdnamn för Elasticsearch-server

Så här hittar du variabelnamnet för global minification i HTML:

1. Bestäm omfånget.

   Det är det globala omfånget, så variabelnamnet börjar med `CONFIG__DEFAULT__`

1. Resten av variabelnamnet är `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Resultat**: Variabelnamnet är `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Leveranslands ursprung

Så här hittar du variabelnamnet för ursprungsland:

1. Bestäm omfånget.

   Hitta omfånget i [databas](#find-a-website-or-store-view-scope-in-the-database) som beskrivs i steg 1: Hitta värdet för webbplatsens eller butikens visningsomfång. (Du kan också hitta värdet i Admin enligt [tabell i steg 2: Ange globala variabler, webbplatsvariabler eller butiksvyvariabler](#step-2-set-global-website-or-store-view-variables.

   Omfånget kan till exempel vara `CONFIG__WEBSITES__DEFAULT`.

1. Resten av variabelnamnet är `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Resultat**: Variabelnamnet är `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Så här använder du miljövariabler

Ange konfigurationsvärden som variabler med PHP:s [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) associera array. Du kan ange värden i alla PHP-skript som körs när Commerce körs.

>[!TIP]
>
>Ställa in variabelvärden i `index.php` eller `pub/index.php` fungerar inte alltid som förväntat eftersom olika programstartpunkter kan användas beroende på webbserverkonfigurationen. Genom att montera `$_ENV` direktiv i `app/bootstrap.php` -filen, oavsett vilken programstartpunkt det gäller, `$_ENV` Direktiv körs alltid sedan `app/bootstrap.php` filen läses in som en del av Commerce-arkitekturen.

Ett exempel på två inställningar `$_ENV` värden följer:

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Ett steg-för-steg-exempel visas i [Ange konfigurationsvärden med hjälp av systemvariabler](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- Använd värden som du anger i dialogrutan `$_ENV` array, du måste ange `variables_order = "EGPCS"`(Miljö, Get, Post, Cookie och Server) i `php.ini` -fil. Mer information finns i [PHP-dokumentation](https://www.php.net/manual/en/ini.core.php).
>
>- Om du försöker åsidosätta konfigurationsinställningarna med hjälp av [Project Web Interface](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)måste variabelnamnet föregås av `env:`. Till exempel:
>
>![Exempel på miljövariabel](../../assets/configuration/cloud-console-envvariable.png)
