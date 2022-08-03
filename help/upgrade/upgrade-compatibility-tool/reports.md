---
title: '"[!DNL Upgrade Compatibility Tool] rapporter"'
description: Följ de här stegen för att köra [!DNL Upgrade Compatibility Tool] i ditt Adobe Commerce-projekt.
source-git-commit: 1ce02c3215b01f64e86383938a257514f0e4257c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Rapporter

{{commerce-only}}

Som ett resultat av analysen [!DNL Upgrade Compatibility Tool] kan exportera en rapport som innehåller en lista med problem för varje fil och ange hur allvarlig den är, felkoden och felbeskrivningen. The [!DNL Upgrade Compatibility Tool] exporterar rapporten i två olika format:

- A [JSON-fil](reports.md#json-file).
- An [HTML rapport](reports.md#html-report).

Se följande exempel på kommandoradsgränssnitt för en rapport:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

Kontrollera [Felmeddelandereferens](../upgrade-compatibility-tool/error-messages.md) för mer information om de olika fel som rapporten kan ge.

Den här rapporten innehåller även en detaljerad sammanfattning av

- *Aktuell version*: den version som är installerad.
- *Målversion*: den version du vill uppgradera till.
- *Körningstid*: hur lång tid det tog att sammanställa rapporten (mm:ss).
- *Moduler som behöver uppdateras*: procentandelen moduler som innehåller kompatibilitetsproblem och som behöver uppdateras.
- *Filer som behöver uppdateras*: procentandelen filer som innehåller kompatibilitetsproblem och som behöver uppdateras.
- *Totalt antal kritiska fel*: antalet kritiska fel som påträffats.
- *Totalt antal fel*: antalet fel som hittats.
- *Totalt antal varningar*: antalet varningar som hittats.
- *Maximal minnesanvändning*: den maximala mängden minne i [!DNL Upgrade Compatibility Tool] har nåtts under körningen.

Se följande exempel på kommandoradsgränssnitt:

```terminal
 ----------------------------- ----------------- 
  Current version               2.4.1            
  Target version                2.4.4            
  Execution time                1m:8s            
  Modules that require update   71.67% (43/60)   
  Files that require update     18.05% (96/532)  
  Total critical issues         24               
  Total errors                  159              
  Total warnings                53               
  Memory peak usage             902.00 MB        
 ----------------------------- ----------------- 
```

## JSON-fil

Du kan hämta JSON-filens utdata medan du kör [!DNL Upgrade Compatibility Tool] i kommandoradsgränssnitt. The `JSON` filen innehåller exakt samma information som visas på [!DNL Upgrade Compatibility Tool] utdata:

- En lista med identifierade problem.
- En sammanfattning av analysen.

För varje påträffat fel innehåller rapporten detaljerad information som problemets svårighetsgrad och beskrivning.

Exportera detta `JSON` till en annan utdatamapp:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Där argumenten är följande:

- `<dir>`: Adobe Commerce installationskatalog.
- `[=JSON-OUTPUT-PATH]`: Sökvägskatalog som ska exporteras `JSON` utdatafil.

>[!NOTE]
>
> Standardsökvägen för utdatamappen är `var/output/[TIME]-results.json`.

## HTML rapport

Du kan hämta HTML-rapporten när du kör verktyget i ett kommandoradsgränssnitt eller via [!DNL Site-Wide Analysis Tool]. Rapporten från HTML innehåller också följande:

- En lista med identifierade problem.
- En sammanfattning av analysen.

![HTML-rapport - sammanfattning](../../assets/upgrade-guide/uct-html-summary.png)

Du kan enkelt navigera bland de identifierade problemen under [!DNL Upgrade Compatibility Tool] analys.

Du kan filtrera utgåvor som visas i rapporten efter den minsta utgåvnivån (standardvärdet är `WARNING`).

Det finns en listruta i det övre högra hörnet där du kan välja en annan nivå. Listan med identifierade problem filtreras därefter.

![HTML-rapport - listruteanvändning](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> Problemen med lägre problemnivå har tagits bort, men du får ett meddelande så att du alltid är medveten om de identifierade problemen per modul.

HTML-betänkandet innehåller även fyra olika diagram:

- **Moduler efter allvarlighetsgrad för problem**: Visar allvarlighetsgrad fördelad efter moduler.
- **Filer efter allvarlighetsgrad för problem**: Visar allvarlighetsgrad för fildistribution.
- **Moduler ordnade efter totalt antal utgåvor**: Visar de 10 mest komprometterade modulerna med hänsyn till varningar, fel och kritiska fel.
- **Moduler med relativa storlekar och problem**: Ju fler filer en modul innehåller, desto större blir cirkeln. Ju fler problem en modul har, desto mer röd blir cirkeln.

Med dessa diagram kan du identifiera de moduler som är mest komprometterade och de som kräver mer arbete för att kunna utföra en uppgradering.

![HTML-rapport - diagram](../../assets/upgrade-guide/uct-html-diagrams.png)

Diagrammen i HTML-rapporten uppdateras också i enlighet med detta, med det enda undantaget `Modules with relative sizes and issues`, som genereras med `min-issue-level` som ursprungligen var konfigurerad.

Om du vill se olika resultat för `Modules with relative sizes and issues` måste du köra kommandot igen och ange ett annat värde för `--min-issue-level` alternativ.

![HTML-rapport - Bubbeldiagram](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Så här exporterar du den här HTML-rapporten till en annan utdatamapp:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Där argumenten är följande:

- `<dir>`: {{site.data.var.ee}} installationskatalog.
- `[=HTML-OUTPUT-PATH]`: Sökvägskatalog som ska exporteras `.html` utdatafil.

>[!NOTE]
>
> Standardsökvägen för utdatamappen är `var/output/[TIME]-results.html`.
