---
title: Importera data från konfigurationsfiler
description: Importera konfigurationsinställningar för Adobe Commerce från konfigurationsfiler.
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---


# Importera konfigurationsinställningar

{{file-system-owner}}

När du konfigurerar ett produktionssystem med Commerce 2.2 [distributionsmodell för pipeline](../deployment/technical-details.md)måste du _import_ konfigurationsinställningar från `config.php` och `env.php` till databasen.
Dessa inställningar omfattar konfigurationssökvägar och -värden, webbplatser, butiker, butiksvyer och teman.

När du har importerat webbplatser, butiker, vyer och teman kan du skapa produktattribut och tillämpa dem på webbplatser, butiker och butiksvyer i produktionssystemet.

>[!INFO]
>
>The `bin/magento app:config:import` kommandot bearbetar inte konfiguration som lagras i miljövariabler.

## Importera, kommando

Kör följande kommando på produktionssystemet för att importera data från konfigurationsfilerna (`config.php` och `env.php`) till databasen:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Använd det valfria `[-n, --no-interaction]` för att importera data utan interaktion.

Om du anger `bin/magento app:config:import` utan den valfria flaggan måste du bekräfta ändringarna.

Om konfigurationsfilen till exempel innehåller en ny webbplats och en ny butik visas följande meddelande:

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Fortsätt importen genom att ange `yes`.

Om distributionskonfigurationsfilerna innehåller data som ska importeras visas ett meddelande som liknar följande:

```terminal
Start import:
Some information about importing
```

Om distributionskonfigurationsfilerna inte innehåller några data att importera visas ett meddelande som liknar följande:

```terminal
Start import:
Nothing to import
```

## Vad vi importerar

I följande avsnitt beskrivs i detalj vilka data vi importerar.

### Systemkonfiguration

I Commerce används värden direkt i `system` arrayen i `config.php` eller `env.php` i stället för att importera dem till databasen, eftersom de kräver vissa för- och efterbearbetningsåtgärder.

Värdet för konfigurationssökvägen `web/secure/base_url` måste valideras med [serverdel](https://glossary.magento.com/backend) modeller.

#### Backend-modeller

Servermodeller är en mekanism för bearbetning av ändringar i systemkonfigurationen.
Du definierar serverdelsmoduler i `<module_name>/adminhtml/system.xml`.

Alla backend-modeller måste utöka [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) klassen.

När vi importerar backend-modeller sparas inte konfigurationsvärdena.

### Konfiguration av webbplatser, butiker och butiksgrupper

Vi importerar följande typer av konfigurationer.
(Dessa konfigurationer finns under `scopes` array in `config.php`.)

- `websites`: webbplatsrelaterad konfiguration
- `groups`: lagrar relaterad konfiguration
- `stores`: butiksvyer relaterad konfiguration

De föregående konfigurationerna kan importeras i följande lägen:

- `create`: `config.php` innehåller nya enheter (`websites`, `groups`, `stores`) som inte finns i produktionsmiljön
- `update`: `config.php` innehåller entiteter (`websites`, `groups`, `stores`) som skiljer sig från produktionsmiljön
- `delete`: `config.php` gör _not_ innehåller entiteter (`websites`, `groups`, `stores`) som finns i produktionsmiljön

>[!INFO]
>
>Vi importerar inte roten [kategori](https://glossary.magento.com/category) som är kopplade till butiker. Du måste associera en rotkategori med en butik med Commerce [Administratör](https://glossary.magento.com/admin).

### Temakonfiguration

Temakonfigurationen innehåller alla teman som är registrerade i ert handelssystem; data kommer direkt från `theme` databastabell. (Temakonfigurationen finns i `themes` array in `config.php`.)

#### Temadatas struktur

Nyckeln till arrayen är fullständig temats sökväg: `area` + `theme path`

Exempel, `frontend/Magento/luma`.
`frontend` är area och `Magento/luma` är [tema](https://glossary.magento.com/theme) bana.

Värdet för arrayen är data om temat: kod, titel, sökväg, överordnat id

Fullständigt exempel:

```php?start_inline=1
'frontend/Magento/luma' =>
   array (
      'parent_id' => 'Magento/blank',
      'theme_path' => 'Magento/luma',
      'theme_title' => 'Magento Luma',
      'is_featured' => '0',
      'area' => 'frontend',
      'type' => '0',
      'code' => 'Magento/luma',
),
```

>[!INFO]
>
>- _Registrering av tema_. Om ett temadata definieras i `config.php` men temats källkod inte finns i filsystemet, ignoreras temat (d.v.s. inte registrerat).
>- _Ta bort teman_. Om ett tema inte finns i `config.php` men källkoden finns i filsystemet, tas inte temat bort.

