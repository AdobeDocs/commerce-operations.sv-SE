---
title: Distribuera statiska vyfiler
description: Lär dig skriva statiska filer i Commerce-filsystemet i produktionsläge.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 0%

---


# Distribuera statiska vyfiler

{{file-system-owner}}

Distributionskommandot för statiska visningsfiler gör att du kan skriva [statiska filer](https://glossary.magento.com/static-files) till Commerce-filsystemet när Commerce-programvaran är inställd för [produktionsläge](../bootstrap/application-modes.md#production-mode).

Termen _statisk vyfil_ avser följande:

- &quot;Statisk&quot; betyder att den kan cachas för en plats (det vill säga att filen inte genereras dynamiskt). Exempel är bilder och CSS som genererats från LESS.
- &quot;Visa&quot; avser presentationsskikt (från MVC).

Filerna i den statiska vyn finns i `<magento_root>/pub/static` och vissa cachelagras i `<magento_root>/var/view_preprocessed` även katalogen.

Distributionen av statiska visningsfiler påverkas av programlägena enligt följande:

- [Standard](../bootstrap/application-modes.md#default-mode) och [utvecklare](../bootstrap/application-modes.md#developer-mode) lägen: Commerce genererar dem på begäran, men resten cachelagras i en fil för att få snabbare åtkomst.
- [Produktion](../bootstrap/application-modes.md#production-mode) läge: Statiska filer _not_ genereras eller cachelagras.

Du måste skriva statiska vyfiler till Commerce-filsystemet manuellt med det kommando som beskrivs i det här avsnittet; Därefter kan du begränsa behörigheter för att begränsa säkerhetsluckorna och för att förhindra oavsiktlig eller skadlig överskrivning av filer.

>[!WARNING]
>
>_Endast i utvecklarläget_: När du installerar eller aktiverar en ny modul kan ny JavaScript, CSS, layouter och så vidare läsas in. För att undvika problem med statiska filer måste du rensa de gamla filerna så att du ser till att du får alla ändringar för den nya modulen. Du kan rensa genererade statiska vyfiler på flera sätt. Se [Rensa cacheämne för statiska filer för detaljer](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/cache_for_frontdevs.html#clean_static_cache) för mer information.

**Distribuera statiska vyfiler**:

1. Logga in på Commerce Server som, eller [växla till filsystemets ägare](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Ta bort innehållet i `<magento_root>/pub/static`, förutom `.htaccess` -fil. Ta inte bort den här filen.
1. Köra distributionsverktyget för statiska vyfiler `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >Om du aktiverar filsammanfogning i statisk vy i Admin `pub/static` katalogsystemet måste vara skrivbart.

   Kommandoalternativ:

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

I följande tabell förklaras det här kommandots parametrar och värden.

| Alternativ | Beskrivning | Obligatoriskt? |
| ------ | ----------- | --------- |
| `<languages>` | Blankstegsavgränsad lista med [ISO-639](http://www.loc.gov/standards/iso639-2/php/code_list.php) språkkoder som statiska vyfiler ska skrivas ut för. (Standard är `en_US`.)<br>Hitta listan genom att köra: `bin/magento info:language:list` | Nej |
| `--language (-l)` | Generera filer endast för de angivna språken. Standardinställningen, utan att något alternativ har angetts, är att generera filer för alla ISO-639-språkkoder. Du kan ange namnet på en språkkod i taget. Standardvärdet är **alla**.<br>Exempel: `--language en_US --language es_ES` | Nej |
| `--exclude-language` | Generera filer för de angivna språkkoderna. Standardinställningen, utan något alternativ angivet, är att ingenting ska uteslutas. Du kan ange namnet på en språkkod eller en kommaavgränsad lista med språkkoder. Standardvärdet är **ingen**. | Nej |
| `--theme <theme>` | teman som statiskt innehåll ska distribueras för. Standardvärdet är **alla**.<br>Exempel: `--theme Magento/blank --theme Magento/luma` | Nej |
| `--exclude-theme <theme>` | Teman som ska uteslutas vid distribution av statiskt innehåll. Standardvärdet är **ingen**.<br>Exempel, `--exclude-theme Magento/blank` | Nej |
| `--area (-a)` | Generera filer endast för de angivna områdena. Standardinställningen, utan att något alternativ har angetts, är att generera filer för alla områden. Giltiga värden är `adminhtml` och `frontend`. Standardvärdet är **alla**.<br>Exempel: `--area adminhtml` | Nej |
| `--exclude-area` | Generera inga filer för de angivna områdena. Standardinställningen, utan något alternativ angivet, är att ingenting ska uteslutas. Standardvärdet är **ingen**. | Nej |
| `--jobs (-j)` | Aktivera parallell bearbetning med angivet antal jobb. Standardvärdet är 0 (kör inte i parallella processer). Standardvärdet är **0**. | Nej |
| `--symlink-locale` | Skapa länkar för filerna för de språkinställningarna som skickas för distribution, men som inte har några anpassningar. | Nej |
| `--content-version=CONTENT-VERSION` | Anpassad version av statiskt innehåll kan användas om distributionen körs på flera noder för att säkerställa att den statiska innehållsversionen är identisk och att cachelagring fungerar som den ska. | Nej |
| `--no-javascript` | Distribuera inte JavaScript-filer | Nej |
| `--no-css` | Distribuera inte CSS-filer. | Nej |
| `--no-less` | Distribuera inte LESS-filer. | Nej |
| `--no-images` | Distribuera inte bilder. | Nej |
| `--no-fonts` | Distribuera inte teckensnittsfiler. | Nej |
| `--no-html` | Distribuera inte HTML-filer. | Nej |
| `--no-misc` | Distribuera inte andra typer av filer: MD, JBF, CSV, JSON, TXT, HTC, SWF | Nej |
| `--no-html-minify` | Minimera inte HTML-filer. | Nej |
| `-s <quick\|standard\|compact>` | Definiera distributionsstrategin. Använd endast dessa alternativ om du har fler än en lokal plats.<ul><li>Använd [snabb strategi](static-view-file-strategy.md#quick-strategy) för att minimera driftsättningstiden. Detta är standardkommandoalternativet om det inte anges.</li><li>Använd [standardstrategi](static-view-file-strategy.md#standard-strategy) för att distribuera alla statiska vyfiler för alla paket.</li><li>Använd [kompakt strategi](static-view-file-strategy.md#compact-strategy) för att spara diskutrymme på servern.</li></ul> | Nej |
| `--no-parent` | Generera inga filer för det aktuella temats överordnade teman. Vi rekommenderar starkt att du använder den här flaggan om du inte uttryckligen använder det överordnade temat för det aktuella temat som du försöker distribuera. Detta gör processen betydligt snabbare. Den här flaggan är tillgänglig i Commerce 2.4.2 | Nej |
| `--force (-f)` | Distribuera filer i valfritt läge. (som standard kan verktyget för distribution av statiskt innehåll endast köras i produktionsläge. Använd det här alternativet om du vill köra det i standardläge eller utvecklarläge). | Nej |

>[!INFO]
>
>Om du anger värden för båda `<languages>` och `--language`, `<languages>` har företräde.

## Exempel

Här följer några exempelkommandon.

### Utesluta ett tema och HTML-miniatyr

Följande kommando distribuerar statiskt innehåll för amerikansk engelska (`en_US`), utelämnar Luma-temat som finns i Commerce och minierar inte HTML-filer.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

Exempelutdata:

```terminal
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/backend
=== frontend -> Magento/blank -> en_US ===
=== adminhtml -> Magento/backend -> en_US ===
...........................................................
... more ...
Successful: 2055 files; errors: 0
---

New version of deployed files: 1466710645
............
Successful: 1993 files; errors: 0
---
```

Följande kommando distribuerar endast JavaScript, med fyra jobb, med en standarddistributionsstrategi:

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

Följande kommando distribuerar endast CSS och LESS med 3 jobb och en snabb distributionsstrategi:

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### Generera statiska vyfiler för ett tema och ett område

Följande kommando genererar statiska vyfiler för alla språk, endast för klientdelen, temat för Commerce Luma, utan att generera teckensnitt:

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

Exempelutdata:

```terminal
Requested languages: en_US
Requested areas: frontend
Requested themes: Magento/luma
=== frontend -> Magento/luma -> en_US ===
...........................................................
... more ...
........................................................................
Successful: 2092 files; errors: 0
---

New version of deployed files: 1466711110
```

## Distribuera statiska vyfiler utan att installera Commerce

Du kanske vill köra distributionsprocessen i en separat, icke-produktionsmiljö för att undvika eventuella byggprocesser på känsliga produktionsdatorer.

Gör så här:

1. Kör [`bin/magento app:config:dump`](../cli/export-configuration.md) för att exportera konfigurationen från produktionssystemet.
1. Kopiera de exporterade filerna till kodbasen för icke-produktion.
1. Distribuera statiska vyfiler: `bin/magento setup:static-content:deploy`

## Felsöka distributionsverktyget för statiska vyfiler

[Installera Commerce-programvaran först](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html); Annars kan du inte köra distributionsverktyget för statiska vyfiler.

**Symptom**: Följande fel visas när du kör distributionsverktyget för statiska vyfiler:

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**Lösning**:

Gör så här:

1. Installera Commerce-programvaran med [kommandorad](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli.html).
1. Logga in på Commerce Server som, eller [växla till](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html), filsystemets ägare.
1. Ta bort innehållet i `<magento_root>/pub/static` katalog, förutom `.htaccess` -fil. Ta inte bort den här filen.
1. Distribuera statiska vyfiler: `bin/magento setup:static-content:deploy`

## Tips för utvecklare som anpassar verktyget för statisk innehållsdistribution

När du skapar en anpassad implementering av det statiska innehållsdistributionsverktyget ska du endast använda atomiska filskrivningar för filer som ska vara tillgängliga på klienten. Om du använder icke-atomisk filskrivning kan dessa filer läsas in på klienten med delvis innehåll.

Ett av alternativen för att göra det atomiskt är att skriva till filer som lagras i en tillfällig katalog och kopiera eller flytta dem till målkatalogen (varifrån de läses in till klienten) när skrivningen är klar. Mer information om hur du skriver till filer finns i [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
