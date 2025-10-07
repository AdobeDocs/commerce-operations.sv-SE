---
title: Distribuera statiska vyfiler
description: Lär dig hur du distribuerar statiska vyfiler till Adobe Commerce filsystem i produktionsläge. Upptäck driftsättningskommandon och optimeringstekniker.
exl-id: 51954738-b999-4982-954b-70f7a70c5a17
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 0%

---

# Distribuera statiska vyfiler

{{file-system-owner}}

Med distributionskommandot för statiska visningsfiler kan du skriva statiska filer till filsystemet i Commerce när Commerce-programmet är inställt för [produktionsläge](../bootstrap/application-modes.md#production-mode).

Termen _statisk vyfil_ refererar till följande:

- &quot;Statisk&quot; betyder att den kan cachas för en plats (det vill säga att filen inte genereras dynamiskt). Exempel är bilder och CSS som genererats från LESS.
- &quot;Visa&quot; avser presentationsskikt (från MVC).

Statiska vyfiler finns i katalogen `<magento_root>/pub/static` och vissa cachelagras även i katalogen `<magento_root>/var/view_preprocessed`.

Distributionen av statiska visningsfiler påverkas av programlägena enligt följande:

- Lägen [Standard](../bootstrap/application-modes.md#default-mode) och [utvecklare](../bootstrap/application-modes.md#developer-mode): Commerce genererar dem vid behov, men resten cachas i en fil för att få snabb åtkomst.
- [Produktion](../bootstrap/application-modes.md#production-mode): Statiska filer genereras eller cachelagras _inte_.

Du måste skriva statiska vyfiler till filsystemet i Commerce manuellt med det kommando som beskrivs i det här avsnittet. Därefter kan du begränsa behörigheter för att begränsa dina säkerhetsluckor och förhindra oavsiktlig eller skadlig överskrivning av filer.

>[!WARNING]
>
>_Endast i utvecklarläget_: När du installerar eller aktiverar en ny modul kan den läsa in nya JavaScript, CSS, layouter och så vidare. För att undvika problem med statiska filer måste du rensa de gamla filerna så att du ser till att du får alla ändringar för den nya modulen. Du kan rensa genererade statiska vyfiler på flera sätt. Mer information finns i [Rensa cache-avsnittet för statiska filer](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache).

**Så här distribuerar du statiska vyfiler**:

1. Logga in på Commerce-servern som eller [växla till filsystemets ägare](../../installation/prerequisites/file-system/overview.md).
1. Ta bort innehållet i `<magento_root>/pub/static`, förutom i filen `.htaccess`. Ta inte bort filen.
1. Kör distributionsverktyget `<magento_root>/bin/magento setup:static-content:deploy` för statiska vyfiler.

   >[!INFO]
   >
   >Om du aktiverar filsammanfogning i statisk vy i Admin måste katalogsystemet `pub/static` vara skrivbart.

   Kommandoalternativ:

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

I följande tabell förklaras det här kommandots parametrar och värden.

| Alternativ | Beskrivning | Obligatoriskt? |
| ------ | ----------- | --------- |
| `<languages>` | Blankstegsavgränsad lista med [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php)-språkkoder som statiska vyfiler ska skrivas ut för. (Standard är `en_US`.)<br>Hitta listan genom att köra: `bin/magento info:language:list` | Nej |
| `--language (-l)` | Generera filer endast för de angivna språken. Standardinställningen, utan att något alternativ har angetts, är att generera filer för alla ISO-639-språkkoder. Du kan ange namnet på en språkkod i taget. Standardvärdet är **all**.<br>Till exempel: `--language en_US --language es_ES` | Nej |
| `--exclude-language` | Generera filer för angivna språkkoder. Standardinställningen, utan något alternativ angivet, är att ingenting ska uteslutas. Du kan ange namnet på en språkkod eller en kommaavgränsad lista med språkkoder. Standardvärdet är **ingen**. | Nej |
| `--theme <theme>` | Teman där statiskt innehåll ska distribueras. Standardvärdet är **all**.<br>Till exempel: `--theme Magento/blank --theme Magento/luma` | Nej |
| `--exclude-theme <theme>` | Teman som ska uteslutas vid distribution av statiskt innehåll. Standardvärdet är **ingen**.<br>Exempel: `--exclude-theme Magento/blank` | Nej |
| `--area (-a)` | Generera filer endast för de angivna områdena. Standardinställningen, utan att något alternativ har angetts, är att generera filer för alla områden. Giltiga värden är `adminhtml` och `frontend`. Standardvärdet är **all**.<br>Till exempel: `--area adminhtml` | Nej |
| `--exclude-area` | Generera inga filer för de angivna områdena. Standardinställningen, utan något alternativ angivet, är att ingenting ska uteslutas. Standardvärdet är **ingen**. | Nej |
| `--jobs (-j)` | Aktivera [parallell bearbetning](manage-indexers.md#reindexing-in-parallel-mode) med angivet antal jobb. Standardvärdet är 0 (kör inte i parallella processer). Standardvärdet är **0**. | Nej |
| `--symlink-locale` | Skapa länkar för filerna för de språkinställningarna som skickas för distribution, men som inte har några anpassningar. | Nej |
| `--content-version=CONTENT-VERSION` | Anpassad version av statiskt innehåll kan användas om distributionen körs på flera noder för att säkerställa att den statiska innehållsversionen är identisk och att cachelagring fungerar som den ska. | Nej |
| `--no-javascript` | Installera inte JavaScript-filer | Nej |
| `--no-css` | Distribuera inte CSS-filer. | Nej |
| `--no-less` | Distribuera inte LESS-filer. | Nej |
| `--no-images` | Distribuera inte bilder. | Nej |
| `--no-fonts` | Distribuera inte teckensnittsfiler. | Nej |
| `--no-html` | Installera inte HTML-filer. | Nej |
| `--no-misc` | Distribuera inte andra typer av filer: MD, JBF, CSV, JSON, TXT, HTC, SWF | Nej |
| `--no-html-minify` | Minimera inte HTML-filer. | Nej |
| `-s <quick\|standard\|compact>` | Definiera distributionsstrategin. Använd endast dessa alternativ om du har fler än en lokal plats.<ul><li>Använd [snabbstrategin](static-view-file-strategy.md#quick-strategy) för att minimera distributionstiden. Detta är standardkommandoalternativet om det inte anges.</li><li>Använd [standardstrategin](static-view-file-strategy.md#standard-strategy) för att distribuera alla statiska vyfiler för alla paket.</li><li>Använd [kompakt strategi](static-view-file-strategy.md#compact-strategy) för att spara diskutrymme på servern.</li></ul> | Nej |
| `--no-parent` | Generera inga filer för det aktuella temats överordnade teman. Vi rekommenderar starkt att du använder den här flaggan om du inte uttryckligen använder det överordnade temat för det aktuella temat som du försöker distribuera. Detta gör processen betydligt snabbare. Den här flaggan finns i Commerce 2.4.2 | Nej |
| `--force (-f)` | Distribuera filer i valfritt läge. (som standard kan verktyget för distribution av statiskt innehåll endast köras i produktionsläge. Använd det här alternativet om du vill köra det i standardläge eller utvecklarläge). | Nej |

>[!INFO]
>
>Om du anger värden för både `<languages>` och `--language` har `<languages>` företräde.

## Exempel

Här följer några exempelkommandon.

### Exkludera ett tema och HTML-miniatyr

Följande kommando distribuerar statiskt innehåll för amerikansk engelska (`en_US`), exkluderar Luma-temat som ingår i Commerce och minierar inte HTML-filer.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

Exempel:

```
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

Följande kommando genererar statiska visningsfiler för alla språk, endast för frontend-området och Commerce Luma-temat, utan att generera teckensnitt:

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

Exempel:

```
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

1. Kör [`bin/magento app:config:dump`](../cli/export-configuration.md) om du vill exportera konfigurationen från produktionssystemet.
1. Kopiera de exporterade filerna till kodbasen för icke-produktion.
1. Distribuera statiska vyfiler: `bin/magento setup:static-content:deploy`

## Felsöka distributionsverktyget för statiska vyfiler

[Installera Commerce först](../../installation/overview.md), annars kan du inte köra distributionsverktyget för statiska vyfiler.

**Symptom**: Följande fel visas när du kör distributionsverktyget för statiska vyfiler:

```
ERROR: You need to install the Commerce application before running this utility.
```

**Lösning**:

Gör så här:

1. Installera Commerce-programmet med kommandoraden [](../../installation/composer.md).
1. Logga in på programservern som, eller [växla till](../../installation/prerequisites/file-system/overview.md), ägare av filsystemet.
1. Ta bort innehållet i katalogen `<app_root>/pub/static`, förutom i filen `.htaccess`. Ta inte bort filen.
1. Distribuera statiska vyfiler: `bin/magento setup:static-content:deploy`

## Tips för utvecklare som anpassar verktyget för statisk innehållsdistribution

När du skapar en anpassad implementering av det statiska innehållsdistributionsverktyget ska du endast använda atomiska filskrivningar för filer som ska vara tillgängliga på klienten. Om du använder icke-atomisk filskrivning kan dessa filer läsas in på klienten med delvis innehåll.

Ett av alternativen för att göra det atomiskt är att skriva till filer som lagras i en tillfällig katalog och kopiera eller flytta dem till målkatalogen (varifrån de läses in till klienten) när skrivningen är klar. Mer information om hur du skriver till filer finns i [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
