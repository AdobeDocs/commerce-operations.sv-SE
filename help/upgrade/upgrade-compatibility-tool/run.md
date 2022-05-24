---
title: Kör [!DNL Upgrade Compatibility Tool]
description: Följ de här stegen för att köra [!DNL Upgrade Compatibility Tool] i ditt Adobe Commerce-projekt.
source-git-commit: 64b061f3b2f93827bfdb904a6faddbd21f4da5e6
workflow-type: tm+mt
source-wordcount: '2057'
ht-degree: 0%

---


# Kör [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

The [!DNL Upgrade Compatibility Tool] är ett kommandoradsverktyg som kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla installerade moduler. Den returnerar en lista med allvarliga problem, fel och varningar som måste åtgärdas innan du uppgraderar till den senaste versionen av Adobe Commerce.

The [!DNL Upgrade Compatibility Tool] identifierar möjliga problem som måste åtgärdas i koden innan du försöker uppgradera till en nyare version av Adobe Commerce.

## Använd `upgrade:check` kommando

The `upgrade:check` är det huvudsakliga kommandot som kör verktyget:

```bash
bin/uct upgrade:check <dir>
```

>[!TIP]
>
>The `<dir>` värde är den katalog där din Adobe Commerce-instans finns.

The `upgrade:check` kommandot kör [!DNL Upgrade Compatibility Tool] och kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla moduler som är installerade i den. Den returnerar en lista med viktiga problem, fel och varningar som måste åtgärdas innan du uppgraderar till den senaste versionen av din Adobe Commerce.

>[!WARNING]
>
>Kör bara när projektets rotkatalog (eller huvudkatalogen) anges.

Det här kommandot kontrollerar om det finns några kodändringar för den specifika Adobe Commerce-instansen och om alla anpassade kodändringar har installerats i den.

Du kan köra `core:code:changes` om du bara vill analysera kodändringar för den specifika Adobe Commerce-instansen. Se [Huvudkodändringar](../upgrade-compatibility-tool/run.md#use-the-core:code:changes-command) -avsnitt.

Du kan använda `graphql:compare` om du vill jämföra två GraphQL-scheman för att kontrollera om det finns några ändringar mellan dem. Se [Verifiering av GraphQL-schemakompatibilitet](../upgrade-compatibility-tool/run.md#graphql-schema-compatibility-verification) -avsnitt.

### Recommendations använder `upgrade:check` kommando

- The [!DNL Upgrade Compatibility Tool] kräver minst 2 GB RAM-minne för att köras. Den här inställningen rekommenderas för att undvika problem på grund av en låg minnesbegränsning. The [!DNL Upgrade Compatibility Tool] visar en fråga om du kör `upgrade:check` kommando med låg `memory_limit` inställning.
- Ange `-m` för att köra verktyget mot en specifik modul:

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

Där argumenten är följande:

- `<dir>`: Adobe Commerce installationskatalog.
- `[=MODULE-PATH]`: En specifik modulsökvägskatalog.

### Använd `--help` option

Om du vill se [!DNL Upgrade Compatibility Tool] allmänna kommandoalternativ och hjälp, kör:

```bash
bin/uct --help
```

Det går dock att köra `--help` som ett alternativ när du kör ett specifikt kommando, som `bin/uct upgrade:check`. Detta returnerar specifika `--help` alternativ för det kommandot:

```bash
bin/uct upgrade:check --help
```

Tillgänglig `--help` för `upgrade:check` kommando:

- `-m, --module-path[=MODULE-PATH]`: Sökväg till de moduler som ska analyseras
- `-a, --current-version[=CURRENT-VERSION]`: Aktuell Adobe Commerce-version, version av Adobe Commerce-installationen, används om den utelämnas.
- `-c, --coming-version[=COMING-VERSION]`: Adobe Commerce-målversion, den senaste versionen av Adobe Commerce kommer att användas om den utelämnas. Innehåller en lista över alla tillgängliga Adobe Commerce-versioner.
- `--json-output-path[=JSON-OUTPUT-PATH]`: Sökväg till filen där utdata ska exporteras i json-format.
- `--html-output-path[=HTML-OUTPUT-PATH]`: Sökväg till filen där utdata ska exporteras i HTML-format.
- `--min-issue-level`: Minsta utgivningsnivå som ska visas i rapporten. Standardnivån är [VARNING].
- `-i, --ignore-current-version-compatibility-issues`: Använd det här alternativet om du inte vill inkludera kända allvarliga problem, fel och varningar i [!DNL Upgrade Compatibility Tool] rapport.
- `--context=CONTEXT`: Körningskontext. Det här alternativet är avsett för integrering och påverkar inte körningsresultatet.
- `-h, --help`: Visa hjälp för det specifika kommandot. Om inget kommando anges `list` är standardresultatet.
- `-q, --quiet`: Skriv inga meddelanden när kommandot körs.
- `-v, --version`: Visa programversion.
- `--ansi, --no-ansi`: Aktivera ANSI-utdata.
- `-n, --no-interaction`: Ställ inga interaktiva frågor när du kör kommandot.
- `-v, --vv, --vvv, --verbose`: Öka detaljrikedomen i utdatakommunikationen. 1 för normal utskrift, 2 för utförlig utskrift och 3 för DEBUG-utdata.

### Utdata

Som ett resultat av den analys som gjorts [!DNL Upgrade Compatibility Tool] exporterar en rapport som innehåller en lista med problem för varje fil och anger hur allvarlig den är, felkoden och felbeskrivningen.

Se exemplet nedan:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

Kontrollera [Felmeddelandereferens](error-messages.md) för mer information.

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

#### JSON

JSON-filen innehåller exakt samma information som visas för utdata:

- Lista över identifierade problem.
- Sammanfattning av analysen.

För varje påträffat fel innehåller rapporten detaljerad information som problemets svårighetsgrad och beskrivning.

>[!NOTE]
>
>Standardsökvägen för utdatamappen är `var/output/[TIME]-results.json`.

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

#### HTML

HTML-filen innehåller också analyssammanfattningen och en lista över identifierade problem.

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

Du kommer att kunna filtrera de problem som visas i rapporten efter den minsta utgåvnivån (som standard, [VARNING]).

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
>Standardsökvägen för utdatamappen är `var/output/[TIME]-results.html`.

### Använd `--ignore-current-version-compatibility-issues` option

The [!DNL Upgrade Compatibility Tool] låter dig köra `upgrade:check` kommando med `--ignore-current-version-compatibility-issues` så att endast nya eller okända allvarliga problem, fel och varningar visas. Använd det här alternativet om du inte vill inkludera kända allvarliga problem, fel och varningar i [!DNL Upgrade Compatibility Tool] rapport.

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
>Detta gäller endast för PHP API-valideringar.

### Vanilla-installation

A _vanilj_ installation är en ren installation av en angiven versionstagg eller gren för en specifik version.

The `bin/uct core:code:changes` -kommandot kontrollerar om det finns en vanilj-instans i systemet. Om det här är första gången du använder en vanilj-installation uppmanas du av en interaktiv kommandoradsfråga att hämta vanilj-projektet från Adobe Commerce-databasen (`https://repo.magento.com/`).

Du kan köra en [!DNL Upgrade Compatibility Tool] med `--vanilla-dir` om du vill ange installationskatalogen för Adobe Commerce vanilla.

Se [Distribuera vanilj-instans](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) för mer information.

## Använd `list` kommando

Returnera en lista med [!DNL Upgrade Compatibility Tool] tillgängliga kommandon, kör:

```bash
bin/uct list
```

The `list` returnerar följande:

- `-h, --help`: Visa hjälp för det specifika kommandot. Om inget kommando anges `list` är standardresultatet.
- `-q, --quiet`: Skriv inga meddelanden när kommandot körs.
- `-v, --version`: Visa appversion.
- `--ansi, --no-ansi`: Aktivera ANSI-utdata.
- `-n, --no-interaction`: Ställ inga interaktiva frågor när du kör kommandot.
- `-v, --vv, --vvv, --verbose`: Öka detaljrikedomen i utdatakommunikationen. 1 för normal utskrift, 2 för utförlig utskrift och 3 för DEBUG-utdata.

## Använd `core:code:changes` kommando

Du kan jämföra din nuvarande Adobe Commerce-installation med en ren vanilj-installation för att se om kärnkoden innehåller några ändringar som gjorts för att implementera en ny funktion eller anpassning. Valideringen hjälper till att uppskatta den insats som uppgraderingen kräver baserat på dessa ändringar.

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Där argumenten är följande:

- `<dir>`: Adobe Commerce installationskatalog.
- `<vanilla dir>`: Installationskatalogen för Adobe Commerce vanilla.

Det finns vissa begränsningar när du kör det här kommandot:

- Kör bara när projektets rotkatalog (eller huvudkatalogen) anges.
- Visar endast en lista med kärnändringar.

### Använd `core:code:changes` med `--help` option

Tillgänglig `--help` för `core:code:changes` kommando:

- `-h, --help`: Visa hjälp för det specifika kommandot. Om inget kommando anges `list` är standardresultatet.
- `-q, --quiet`: Skriv inga meddelanden när kommandot körs.
- `-v, --version`: Visa appversion.
- `--ansi, --no-ansi`: Aktivera ANSI-utdata.
- `-n, --no-interaction`: Ställ inga interaktiva frågor när du kör kommandot.
- `-v, --vv, --vvv, --verbose`: Öka detaljrikedomen i utdatakommunikationen. 1 för normal utskrift, 2 för utförlig utskrift och 3 för DEBUG-utdata.

## Version

Du kan jämföra din nuvarande Adobe Commerce-installation med Adobe Commerce-versioner `>=2.3`.

Du måste ange versionen som en parameter när du kör kommandot:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

>[!NOTE]
>
>Den här parametern innehåller en lista med alla tillgängliga Adobe Commerce-versioner.

Var:

- `-c, --coming-version[=COMING-VERSION]`: Målversionen för Adobe Commerce.

Det finns vissa begränsningar när du kör föregående kommando:

- Den här parametern refererar till taggar som identifierar en viss version av Adobe Commerce.
- Det är ett krav att uttryckligen ange detta. om bara värdet inte fungerar.
- Ange taggversionen utan citattecken (varken enkla eller dubbla): ~~&quot;2.4.1-develop&quot;~~.
- Du bör INTE tillhandahålla äldre versioner än den som du har installerat, eller äldre än 2.3, som för närvarande är den äldsta som stöds.

### Använd `refactor` kommando

The [!DNL Upgrade Compatibility Tool] har möjlighet att automatiskt åtgärda en reducerad uppsättning problem:

- Funktioner som var tillåtna att användas utan att ett argument skickades, men med sådan användning har nu tagits bort.
- Användning av `$this` i Magento-mallar.
- Användning av PHP-nyckelord `final` i privata metoder.

Kör:

```bash
bin/uct refactor <dir>
```

Där argumenten är följande:

- `<dir>`: Adobe Commerce installationskatalog.

## Verifiering av GraphQL-schemakompatibilitet

The [!DNL Upgrade Compatibility Tool] ger även möjlighet att granska två GraphQL-slutpunkter och jämföra deras scheman för att hitta brytningar och farliga förändringar mellan dem:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Där argumenten är följande:

- `<schema1>`: Slutpunkts-URL för den befintliga installationen.
- `<schema2>`: Slutpunkts-URL för vanilj-installationen.

Du måste köra `instance before` och `instance after` uppgraderingen.

### Jämförelsekommando för GraphQL `--help` alternativ

Tillgänglig `--help` för `graphql:compare` kommando:

- `-h, --help`: Visa hjälp för det specifika kommandot. Om inget kommando anges `list` är standardresultatet.
- `-q, --quiet`: Skriv inga meddelanden när kommandot körs.
- `-v, --version`: Visa appversion.
- `--ansi, --no-ansi`: Aktivera ANSI-utdata.
- `-n, --no-interaction`: Ställ inga interaktiva frågor när du kör kommandot.
- `-v, --vv, --vvv, --verbose`: Öka detaljrikedomen i utdatakommunikationen. 1 för normal utskrift, 2 för utförlig utskrift och 3 för DEBUG-utdata.

### Exempel med en lista med kritiska problem, fel och varningar för GraphQL

```terminal
 *   [WARNING] FIELD_CHANGED_KIND: ConfigurableProduct.gender changed type from Int to String.
 *   [WARNING] OPTIONAL_INPUT_FIELD_ADDED: An optional field sku on input type ProductAttributeSortInput was added.
```

Du kan köra [!DNL Upgrade Compatibility Tool] med en körningskonfiguration via plugin-programmet PhpStorm. Se [[!DNL Upgrade Compatibility Tool] Kör konfiguration](https://devdocs.magento.com/guides/v2.3/ext-best-practices/phpstorm/uct-run-configuration.html) för mer information.

Se det här [videosjälvstudiekurs](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/uct-phpstorm.html?lang=en) (06:30) för att lära dig hur du använder [!DNL Upgrade Compatibility Tool] med Magento PHPStorm-pluginen.


## Rekommenderade åtgärder

### Optimera resultatet

The [!DNL Upgrade Compatibility Tool] innehåller en rapport med resultat med alla problem som identifieras i ditt projekt som standard. Du kan optimera resultaten för att fokusera på de problem som du måste åtgärda för att slutföra uppgraderingen:

- Använd alternativet `--ignore-current-version-compatibility-issues`, som inte åtgärdar alla kända allvarliga problem, fel och varningar i den aktuella Adobe Commerce-versionen. Den innehåller bara fel mot den version du försöker uppgradera till.
- Lägg till `--min-issue-level` den här inställningen gör att du kan ange en miniminivå för utgåvor, så att du bara kan prioritera de viktigaste problemen med din uppgradering.
- Om du bara vill analysera en viss leverantör, modul eller katalog kan du även ange sökvägen som ett alternativ. Kör `bin` kommando med tillagt alternativ `-m`. Detta gör att [!DNL Upgrade Compatibility Tool] för att analysera en specifik modul oberoende av varandra och hjälper till med minnesproblem som kan uppstå när du kör [!DNL Upgrade Compatibility Tool].

### Följ Adobe Commerce metodtips

- Undvik att ha två moduler med samma namn.
- Följ Adobe Commerce [kodstandarder](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).

## Felsökning

### Segmenteringsfel

När två moduler har samma namn [!DNL Upgrade Compatibility Tool] visar ett segmenteringsfel.

För att undvika det här felet bör du köra `bin` kommando med tillagt alternativ `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>The `<dir>` värde är den katalog där din Adobe Commerce-instans finns.

The `-m` kan [!DNL Upgrade Compatibility Tool] om du vill analysera varje specifik modul oberoende av varandra för att undvika att stöta på två moduler med samma namn i din Adobe Commerce-instans.

Med det här kommandoalternativet kan [!DNL Upgrade Compatibility Tool] om du vill analysera en mapp som innehåller flera moduler:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Den här rekommendationen hjälper dig även med minnesproblem som kan uppstå när du kör [!DNL Upgrade Compatibility Tool].

### Tomma utdata

>[!NOTE]
>
>The `M2_VERSION` är den målversion av Adobe Commerce som du vill jämföra med din Adobe Commerce-instans.

Om du har kört det här kommandot:

```bash
bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

Det enda resultatet är `Upgrade compatibility tool`:

```terminal
bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
Upgrade compatibility tool
```

Den troliga orsaken är en minnesbegränsning för PHP.
Åsidosätt minnesbegränsningen genom att ange `memory_limit` till `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```
