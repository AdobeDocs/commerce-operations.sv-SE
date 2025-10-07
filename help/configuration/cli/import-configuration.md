---
title: Importera data från konfigurationsfiler
description: Lär dig hur du importerar konfigurationsinställningar för Adobe Commerce från konfigurationsfiler. Identifiera driftsättning av pipeline och databasimportprocesser.
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Importera konfigurationsinställningar

{{file-system-owner}}

När du konfigurerar ett produktionssystem med Commerce 2.2 [pipeline-distributionsmodellen](../deployment/technical-details.md) måste du _importera_ konfigurationsinställningar från `config.php` och `env.php` till databasen.
Dessa inställningar omfattar konfigurationssökvägar och -värden, webbplatser, butiker, butiksvyer och teman.

När du har importerat webbplatser, butiker, vyer och teman kan du skapa produktattribut och tillämpa dem på webbplatser, butiker och butiksvyer i produktionssystemet.

>[!INFO]
>
>Kommandot `bin/magento app:config:import` bearbetar inte konfigurationen som lagras i miljövariabler.

## Importera, kommando

Kör följande kommando på produktionssystemet för att importera data från konfigurationsfilerna (`config.php` och `env.php`) till databasen:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Använd den valfria flaggan `[-n, --no-interaction]` för att importera data utan interaktion.

Om du anger `bin/magento app:config:import` utan den valfria flaggan måste du bekräfta ändringarna.

Om konfigurationsfilen till exempel innehåller en ny webbplats och en ny butik visas följande meddelande:

```
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Ange `yes` om du vill fortsätta med importen.

Om distributionskonfigurationsfilerna innehåller data som ska importeras visas ett meddelande som liknar följande:

```
Start import:
Some information about importing
```

Om distributionskonfigurationsfilerna inte innehåller några data att importera visas ett meddelande som liknar följande:

```
Start import:
Nothing to import
```

## Vad vi importerar

I följande avsnitt beskrivs i detalj vilka data vi importerar.

### Systemkonfiguration

Commerce använder värden direkt i `system`-arrayen i `config.php` - eller `env.php`-filerna i stället för att importera dem till databasen eftersom de kräver vissa för- och efterbearbetningsåtgärder.

Värdet för konfigurationssökvägen `web/secure/base_url` måste till exempel valideras med serverdelsmodeller.

#### Backend-modeller

Servermodeller är en mekanism för bearbetning av ändringar i systemkonfigurationen.
Du definierar serverdelsmoduler i `<module_name>/adminhtml/system.xml`.

Alla backend-modeller måste utöka klassen [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php).

När vi importerar backend-modeller sparas inte konfigurationsvärdena.

### Konfiguration av webbplatser, butiker och butiksgrupper

Vi importerar följande typer av konfigurationer.
(Dessa konfigurationer finns under arrayen `scopes` i `config.php`.)

- `websites`: webbplatsrelaterad konfiguration
- `groups`: lagrar relaterad konfiguration
- `stores`: butiksvyer visar relaterad konfiguration

De föregående konfigurationerna kan importeras i följande lägen:

- `create`: `config.php` innehåller nya entiteter (`websites`, `groups`, `stores`) som inte finns i produktionsmiljön
- `update`: `config.php` innehåller entiteter (`websites`, `groups`, `stores`) som skiljer sig från produktionsmiljön
- `delete`: `config.php` innehåller _inte_ entiteter (`websites`, `groups`, `stores`) som finns i produktionsmiljön

>[!INFO]
>
>Vi importerar inte den rotkategori som är associerad med butiker. Du måste associera en rotkategori med en butik med hjälp av Commerce Admin.

### Temakonfiguration

Temakonfigurationen innehåller alla teman som är registrerade i ditt Commerce-system. Data kommer direkt från databastabellen `theme`. (Temakonfigurationen finns i arrayen `themes` i `config.php`.)

#### Temadatas struktur

Nyckeln i matrisen är fullständig temats sökväg: `area` + `theme path`

Exempel: `frontend/Magento/luma`.
`frontend` är ett område och `Magento/luma` är en temaväge.

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
>- _Temaregistrering_. Om ett temadata definieras i `config.php` men temats källkod inte finns i filsystemet, ignoreras temat (d.v.s. inte registrerat).
>- _Ta bort teman_. Om det inte finns något tema i `config.php` men källkoden finns i filsystemet tas temat inte bort.
