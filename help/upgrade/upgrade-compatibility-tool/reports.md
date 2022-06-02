---
title: '"[!DNL Upgrade Compatibility Tool] rapporter"'
description: Följ de här stegen för att köra [!DNL Upgrade Compatibility Tool] i ditt Adobe Commerce-projekt.
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Rapporter

{{commerce-only}}

Som ett resultat av analysen [!DNL Upgrade Compatibility Tool] exporterar en rapport som innehåller en lista med problem för varje fil och anger hur allvarlig den är, felkoden och felbeskrivningen.

Se exemplet nedan:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

Kontrollera [Felmeddelandereferens](../upgrade-compatibility-tool/error-messages.md) för mer information.

Rapporten innehåller även en detaljerad sammanfattning som visar:

- *Aktuell version*: den version som är installerad.
- *Målversion*: den version du vill uppgradera till.
- *Körningstid*: hur lång tid det tog att sammanställa rapporten (mm:ss).
- *Moduler som behöver uppdateras*: procentandelen moduler som innehåller kompatibilitetsproblem och som behöver uppdateras.
- *Filer som behöver uppdateras*: procentandelen filer som innehåller kompatibilitetsproblem och som behöver uppdateras.
- *Totalt antal kritiska fel*: antalet kritiska fel som påträffats.
- *Totalt antal fel*: antalet fel som hittats.
- *Totalt antal varningar*: antalet varningar som hittats.

Se exemplet nedan:

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>Som standard är [!DNL Upgrade Compatibility Tool] exporterar rapporten till två olika format: `json` och `html`.

## JSON-fil

JSON-filen innehåller exakt samma information som visas för utdata:

- Lista över identifierade problem.
- Sammanfattning av analysen.

För varje påträffat fel innehåller rapporten detaljerad information som problemets svårighetsgrad och beskrivning.

Om du vill exportera den här rapporten till en annan utdatamapp kör du:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Där argumenten är följande:

- `<dir>`: Adobe Commerce installationskatalog.
- `[=JSON-OUTPUT-PATH]`: Sökvägskatalog som ska exporteras `.json` utdatafil.

>[!NOTE]
>
>Standardsökvägen för utdatamappen är `var/output/[TIME]-results.json`.

## HTML rapport

HTML-filen innehåller också analyssammanfattningen och en lista över identifierade problem. Du kan hämta HTML-rapporten när du kör verktyget i ett kommandoradsgränssnitt eller via [!DNL Site-Wide Analysis Tool].

![HTML-rapport - sammanfattning](../../assets/upgrade-guide/uct-html-summary.png)

Du kan enkelt navigera bland de identifierade problemen under [!DNL Upgrade Compatibility Tool] analys:

![HTML - rapport](../../assets/upgrade-guide/uct-html-details.png)

HTML-betänkandet innehåller även fyra olika diagram:

- **Moduler efter allvarlighetsgrad för problem**: Visar allvarlighetsgrad fördelad efter moduler.
- **Filer efter allvarlighetsgrad för problem**: Visar allvarlighetsgrad för fildistribution.
- **Moduler ordnade efter totalt antal utgåvor**: Visar de 10 mest komprometterade modulerna med hänsyn till varningar, fel och kritiska fel.
- **Moduler med relativa storlekar och problem**: Ju fler filer en modul innehåller, desto större blir cirkeln. Ju fler problem en modul har, desto mer röd blir cirkeln.

Med hjälp av dessa diagram kan du snabbt identifiera de delar som är mest komprometterade och de som kräver mer arbete för en uppgradering.

![HTML-rapport - diagram](../../assets/upgrade-guide/uct-html-diagrams.png)

Du kan filtrera utgåvor som visas i rapporten efter den minsta utgåvnivån. Standardvärdet är `WARNING`.

Det finns en listruta i det övre högra hörnet där du kan välja en annan beroende på dina behov. Listan över identifierade problem kommer att filtreras i enlighet med detta.

![HTML-rapport - listruteanvändning](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

Observera att problemen med lägre problemnivå har tagits bort, men du får ett meddelande så att du alltid är medveten om de identifierade problemen per modul.

Diagrammen uppdateras också i enlighet med detta, med det enda undantaget `Modules with relative sizes and issues`, som genereras med `min-issue-level` ursprungligen konfigurerad.

Om du vill se olika resultat måste du köra kommandot igen och ange ett annat värde för `--min-issue-level` alternativ.

![HTML-rapport - Bubbeldiagram](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Om du vill exportera den här rapporten till en annan utdatamapp kör du:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Där argumenten är följande:

- `<dir>`: Installationskatalogen för {{site.data.var.ee}}.
- `[=HTML-OUTPUT-PATH]`: Sökvägskatalog som ska exporteras `.html` utdatafil.

>[!NOTE]
>
> Standardsökvägen för utdatamappen är `var/output/[TIME]-results.html`.
