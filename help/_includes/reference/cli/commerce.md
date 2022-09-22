---
source-git-commit: ebd32f3fac571efa729122d0e84471b6de540630
workflow-type: tm+mt
source-wordcount: '19002'
ht-degree: 0%

---
# magento-cloud (Adobe Commerce on cloud infrastructure)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Version**: 1.38.1 <!-- app.version -->

Referensen innehåller 127 kommandon som är tillgängliga via `magento-cloud` kommandoradsverktyg.
Den inledande listan genereras automatiskt med `magento-cloud list` i utgåvan.

>[!NOTE]
>
>Den här referensen genereras från programmets kodbas. Om du vill ändra innehållet kan du uppdatera källkoden för motsvarande kommandoimplementering i [kodbas](https://github.com/magento) arkivera och skicka in dina ändringar för granskning. Ett annat sätt är att _Ge oss feedback_ (hitta länken i det övre högra hörnet). Information om riktlinjer för bidrag finns i [Kodavgifter](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

BAS-slutförandekrok.

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--generate-hook`, `-g`



Generera BASH-kod som anger slutförande för det här programmet.
- Standard: `false`
- Accepterar inte ett värde



### `--program`, `-p`



Programnamn som ska utlösa slutförande &lt;comment>(standard är den absoluta programsökvägen)&lt;/comment>.
- Kräver ett värde



### `--multiple`, `-m`



Genererad krok kan användas för flera program.
- Standard: `false`
- Accepterar inte ett värde


### `--shell-type`

Ange gränssnittstypen (zsh eller bash). I annat fall bestäms detta automatiskt.
- Accepterar ett värde <!-- options --> <!-- options.size -->

## `bot`

Magento Cloud Bot

```bash
magento-cloud bot [--party] [--parrot]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--party`


- Standard: `false`
- Accepterar inte ett värde


### `--parrot`


- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `clear-cache`

Rensa CLI-cachen

```bash
magento-cloud clear-cache
```

<!-- app.name -->

```bash
clearcache
```

<!-- app.name -->

```bash
cc
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `decode`

Avkoda en kodad sträng som MAGENTO_CLOUD_VARIABLES

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```

<!-- app.name --> <!-- command.usage -->

### `value`

Variabelvärdet som ska avkodas
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Den egenskap som ska visas i variabeln
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `docs`

Öppna onlinedokumentationen

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```

<!-- app.name --> <!-- command.usage -->

### `search`

Sökord

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--browser`

Webbläsaren som ska användas för att öppna URL-adressen. Ange 0 som ingen.
- Kräver ett värde


### `--pipe`

Skriv ut URL-adressen som ska stoppas.
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `help`

Visar hjälp för ett kommando

```bash
help [--format FORMAT] [--raw] [--] [<command_name>]
```

<!-- app.name --> <!-- command.usage -->

### `command_name`

Kommandonamnet
- Standard: `help`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--format`

Utdataformatet (txt, xml, json eller md)
- Standard: `txt`
- Kräver ett värde


### `--raw`

Hjälp för att skriva ut råformat
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `legacy-migrate`

Migrera från den äldre filstrukturen

```bash
magento-cloud legacy-migrate [--no-backup]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-backup`

Skapa ingen säkerhetskopia av projektet.
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `list`

Visar kommandon

```bash
list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```

<!-- app.name --> <!-- command.usage -->

### `namespace`

Namnutrymmets namn
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

Utdata för kommandolista
- Standard: `false`
- Accepterar inte ett värde


### `--format`

Utdataformatet (txt, xml, json eller md)
- Standard: `txt`
- Kräver ett värde <!-- options --> <!-- options.size -->

## `multi`

Kör ett kommando i flera projekt

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd>
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

Kommandot som ska köras
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--projects`, `-p`



En lista med projekt-ID:n, avgränsade med kommatecken och/eller blanksteg
- Kräver ett värde


### `--continue`

Fortsätt köra kommandon även om ett undantag påträffas
- Standard: `false`
- Accepterar inte ett värde


### `--sort`

En egenskap som listan med projektalternativ ska sorteras efter
- Standard: `title`
- Kräver ett värde


### `--reverse`

Invertera ordningen för projektalternativ
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `web`

Öppna webbgränssnittet

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--browser`

Webbläsaren som ska användas för att öppna URL-adressen. Ange 0 som ingen.
- Kräver ett värde


### `--pipe`

Skriv ut URL-adressen som ska stoppas.
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `welcome`

Välkommen till Magento Cloud

```bash
magento-cloud welcome
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `winky`



```bash
magento-cloud winky
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `activity:cancel`

Avbryt en aktivitet

```bash
magento-cloud activity:cancel [--type TYPE] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Aktivitets-ID. Standardvärdet är den senaste avbrutna aktiviteten.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Filtrera efter typ (när du väljer en standardaktivitet)
- Kräver ett värde



### `--all`, `-a`



Kontrollera senaste aktiviteter i alla miljöer (när du väljer en standardaktivitet)
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `activity:get`

Visa detaljerad information om en enskild aktivitet

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Aktivitets-ID. Standardvärdet är den senaste aktiviteten.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Egenskapen som ska visas
- Kräver ett värde


### `--type`

Filtrera efter typ (när du väljer en standardaktivitet)
- Kräver ett värde


### `--state`

Filtrera efter läge (när du väljer en standardaktivitet): in_progress, pending, complete eller canceled
- Standard: `[]`
- Kräver ett värde


### `--result`

Filtrera efter resultat (när du väljer en standardaktivitet): framgång eller misslyckande
- Kräver ett värde



### `--incomplete`, `-i`



Inkludera endast ofullständiga aktiviteter (när du väljer en standardaktivitet). Det här är en förkortning för &lt;info>—state=in_progress,pending&lt;/info>
- Standard: `false`
- Accepterar inte ett värde



### `--all`, `-a`



Kontrollera senaste aktiviteter i alla miljöer (när du väljer en standardaktivitet)
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `activity:list`

Hämta en lista över aktiviteter för en miljö eller ett projekt

```bash
magento-cloud activity:list [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
activities
```

<!-- app.name -->

```bash
act
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

Filtrera aktiviteter efter typ
- Kräver ett värde


### `--limit`

Begränsa antalet resultat som visas
- Standard: `10`
- Kräver ett värde


### `--start`

Endast aktiviteter som skapats före detta datum listas
- Kräver ett värde


### `--state`

Filtrera aktiviteter efter tillstånd: in_progress, pending, complete eller canceled
- Standard: `[]`
- Kräver ett värde


### `--result`

Filtrera aktiviteter efter resultat: framgång eller misslyckande
- Kräver ett värde



### `--incomplete`, `-i`



Endast lista ofullständiga aktiviteter
- Standard: `false`
- Accepterar inte ett värde



### `--all`, `-a`



Visa aktiviteter i alla miljöer
- Standard: `false`
- Accepterar inte ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `activity:log`

Visa loggen för en aktivitet

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Aktivitets-ID. Standardvärdet är den senaste aktiviteten.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Intervall för aktivitetsuppdatering (sekunder). Ange 0 om du vill inaktivera uppdatering.
- Standard: `3`
- Kräver ett värde



### `--timestamps`, `-t`



Visa en tidsstämpel bredvid varje meddelande
- Standard: `false`
- Accepterar inte ett värde


### `--type`

Filtrera efter typ (när du väljer en standardaktivitet)
- Kräver ett värde


### `--state`

Filtrera efter läge (när du väljer en standardaktivitet): in_progress, pending, complete eller canceled
- Standard: `[]`
- Kräver ett värde


### `--result`

Filtrera efter resultat (när du väljer en standardaktivitet): framgång eller misslyckande
- Kräver ett värde



### `--incomplete`, `-i`



Inkludera endast ofullständiga aktiviteter (när du väljer en standardaktivitet). Det här är en förkortning för &lt;info>—state=in_progress,pending&lt;/info>
- Standard: `false`
- Accepterar inte ett värde



### `--all`, `-a`



Kontrollera senaste aktiviteter i alla miljöer (när du väljer en standardaktivitet)
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `api:curl`

Kör en autentiserad cURL-begäran på Magento Cloud API

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

API-sökvägen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



Begärandemetoden som ska användas
- Kräver ett värde



### `--data`, `-d`



Data som ska skickas
- Kräver ett värde



### `--include`, `-i`



Inkludera sidhuvuden i utdata
- Standard: `false`
- Accepterar inte ett värde



### `--head`, `-I`



Hämta endast rubriker
- Standard: `false`
- Accepterar inte ett värde


### `--disable-compression`

Använd inte flaggan curl —compressed
- Standard: `false`
- Accepterar inte ett värde


### `--enable-glob`

Aktivera bläddring (ta bort flaggan —globoff)
- Standard: `false`
- Accepterar inte ett värde



### `--header`, `-H`



Extra rubrik(er)
- Standard: `[]`
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `app:config-get`

Visa konfigurationen för ett program

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



Den konfigurationsegenskap som ska visas
- Kräver ett värde


### `--refresh`

Om cachen ska uppdateras
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde



### `--identity-file`, `-i`



[Inaktuellt alternativ, används inte längre]
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `app:list`

Visa program i projektet

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
apps
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Om cachen ska uppdateras
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `auth:api-token-login`

Logga in på Magento Cloud med en API-token

```bash
magento-cloud auth:api-token-login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `auth:browser-login`

Logga in på Magento Cloud via en webbläsare

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```

<!-- app.name -->

```bash
login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



Logga in igen, även om du redan är inloggad
- Standard: `false`
- Accepterar inte ett värde


### `--browser`

Webbläsaren som ska användas för att öppna URL-adressen. Ange 0 som ingen.
- Kräver ett värde


### `--pipe`

Skriv ut URL-adressen som ska stoppas.
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `auth:info`

Visa din kontoinformation

```bash
magento-cloud auth:info [-P|--property PROPERTY] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<property>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

Kontoegenskapen som ska visas
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Den kontoegenskap som ska visas (alternativ syntax)
- Kräver ett värde


### `--refresh`

Om cachen ska uppdateras
- Standard: `false`
- Accepterar inte ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `auth:logout`

Logga ut från Magento Cloud

```bash
magento-cloud logout [-a|--all] [--other]
```

<!-- app.name -->

```bash
logout
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Logga ut från alla lokala sessioner
- Standard: `false`
- Accepterar inte ett värde


### `--other`

Logga ut från andra lokala sessioner
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Logga in på Magento Cloud med ett användarnamn och lösenord

```bash
magento-cloud auth:password-login
```

<!-- app.name -->

```bash
auth:login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `auth:token`

Hämta en OAuth 2-åtkomsttoken för begäranden till Magento Cloud-API:er

```bash
magento-cloud auth:token
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `blackfire:setup`

Konfigurera Blackfire.io-integrering för projektet

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--server_id`

Server-ID
- Kräver ett värde


### `--server_token`

Servertoken
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `certificate:add`

Lägg till ett SSL-certifikat i projektet

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--cert`

Sökvägen till certifikatfilen
- Kräver ett värde


### `--key`

Sökvägen till certifikatets privata nyckelfil
- Kräver ett värde


### `--chain`

Sökvägen till certifikatkedjefilen
- Standard: `[]`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `certificate:delete`

Ta bort ett certifikat från projektet

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

Certifikat-ID (eller början av det)
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `certificate:get`

Visa ett certifikat

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

Certifikat-ID (eller början av det)
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Certifikategenskapen som ska visas
- Kräver ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `certificate:list`

Visa projektcertifikat

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
certificates
```

<!-- app.name -->

```bash
certs
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--domain`

Filtrera efter domännamn (skiftlägesokänslig sökning)
- Kräver ett värde


### `--exclude-domain`

Uteslut certifikat, matcha efter domännamn (skiftlägesokänslig sökning)
- Kräver ett värde


### `--issuer`

Filtrera efter utfärdare
- Kräver ett värde


### `--only-auto`

Visa endast automatiskt tilldelade certifikat
- Standard: `false`
- Accepterar inte ett värde


### `--no-auto`

Visa endast manuellt tillagda certifikat
- Standard: `false`
- Accepterar inte ett värde


### `--ignore-expiry`

Visa både utgångna och ej utgångna certifikat
- Standard: `false`
- Accepterar inte ett värde


### `--only-expired`

Visa endast utgångna certifikat
- Standard: `false`
- Accepterar inte ett värde


### `--no-expired`

Visa endast certifikat som inte har upphört att gälla (standard)
- Standard: `false`
- Accepterar inte ett värde


### `--pipe-domains`

Returnera endast en lista med domännamn som omfattas av certifikaten
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `commit:get`

Visa implementeringsinformation

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<commit>]
```

<!-- app.name --> <!-- command.usage -->

### `commit`

Verkställ SHA. Detta kan även acceptera suffixen &quot;HEAD&quot; och cirkumflex (^) eller tilde (~) för överordnade implementeringar.
- Standard: `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Den implementeringsegenskap som ska visas.
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde


### `--format`

INAKTUELL
- Kräver ett värde


### `--columns`

INAKTUELL
- Standard: `[]`
- Kräver ett värde


### `--no-header`

INAKTUELL
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `commit:list`

Listimplementeringar

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```

<!-- app.name -->

```bash
commits
```

<!-- app.name --> <!-- command.usage -->

### `commit`

Git-starten verkställer SHA. Detta kan även acceptera suffixen &quot;HEAD&quot; och cirkumflex (^) eller tilde (~) för överordnade implementeringar.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--limit`

Antalet implementeringar som ska visas.
- Standard: `10`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `db:dump`

Skapa en lokal dump av fjärrdatabasen

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
sql-dump
```

<!-- app.name -->

```bash
environment:sql-dump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--schema`

Schemat som ska dumpas. Uteslut att använda standardschemat (vanligen&quot;main&quot;).
- Kräver ett värde



### `--file`, `-f`



Ett anpassat filnamn för dumpen
- Kräver ett värde



### `--directory`, `-d`



En anpassad katalog för dumpen
- Kräver ett värde



### `--gzip`, `-z`



Komprimera dumpen med gzip
- Standard: `false`
- Accepterar inte ett värde



### `--timestamp`, `-t`



Lägg till en tidsstämpel i dumpfilnamnet
- Standard: `false`
- Accepterar inte ett värde



### `--stdout`, `-o`



Utdata till STDOUT i stället för en fil
- Standard: `false`
- Accepterar inte ett värde


### `--table`

Tabell som ska inkluderas
- Standard: `[]`
- Kräver ett värde


### `--exclude-table`

Tabell(er) som ska uteslutas
- Standard: `[]`
- Kräver ett värde


### `--schema-only`

Dumpa endast scheman, inga data
- Standard: `false`
- Accepterar inte ett värde


### `--charset`

Teckenuppsättningens kodning för dumpen
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde



### `--relationship`, `-r`



Den tjänstrelation som ska användas
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `db:size`

Beräkna diskanvändningen för en databas

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



Visa storlekar i byte.
- Standard: `false`
- Accepterar inte ett värde



### `--cleanup`, `-C`



Kontrollera om tabeller kan rensas och visa rekommendationer (endast InnoDb).
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde



### `--relationship`, `-r`



Den tjänstrelation som ska användas
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `db:sql`

Kör SQL på fjärrdatabasen

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```

<!-- app.name -->

```bash
sql
```

<!-- app.name -->

```bash
environment:sql
```

<!-- app.name --> <!-- command.usage -->

### `query`

En SQL-sats som ska köras
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

Producera råa, icke-tabulära utdata
- Standard: `false`
- Accepterar inte ett värde


### `--schema`

Schemat som ska användas. Uteslut att använda standardschemat (vanligen&quot;main&quot;). Skicka en tom sträng för att inte använda något schema.
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde



### `--relationship`, `-r`



Den tjänstrelation som ska användas
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `domain:add`

Lägg till en ny domän i projektet

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Domännamnet
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

Sökvägen till certifikatfilen för den här domänen
- Kräver ett värde


### `--key`

Sökvägen till den privata nyckelfilen för det angivna certifikatet.
- Kräver ett värde


### `--chain`

Sökvägen till certifikatkedjefilen eller -filerna för det angivna certifikatet
- Standard: `[]`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `domain:delete`

Ta bort en domän från projektet

```bash
magento-cloud domain:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Domännamnet
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `domain:get`

Visa detaljerad information om en domän

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

Domännamnet
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Domänegenskapen som ska visas
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `domain:list`

Hämta en lista över alla domäner

```bash
magento-cloud domains [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
domains
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `domain:update`

Uppdatera en domän

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Domännamnet
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

Sökvägen till certifikatfilen för den här domänen
- Kräver ett värde


### `--key`

Sökvägen till den privata nyckelfilen för det angivna certifikatet.
- Kräver ett värde


### `--chain`

Sökvägen till certifikatkedjefilen eller -filerna för det angivna certifikatet
- Standard: `[]`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:activate`

Aktivera en miljö

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Den eller de miljöer som ska aktiveras

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--parent`

Ange en ny överordnad miljö innan du aktiverar
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:branch`

Gren och miljön

```bash
magento-cloud branch [--title TITLE] [--force] [--no-clone-parent] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```

<!-- app.name -->

```bash
branch
```

<!-- app.name --> <!-- command.usage -->

### `id`

Den nya miljöns ID (filialnamn)
<!-- argument -->

### `parent`

Den nya miljöns överordnade
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--title`

Den nya miljöns titel
- Kräver ett värde


### `--force`

Skapa den nya miljön även om grenen inte kan checkas ut lokalt
- Standard: `false`
- Accepterar inte ett värde


### `--no-clone-parent`

Klona inte den överordnade grenens data
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:checkout`

Kolla in en miljö

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```

<!-- app.name -->

```bash
checkout
```

<!-- app.name --> <!-- command.usage -->

### `id`

ID för miljön som ska checkas ut. Till exempel: &quot;sprint2&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:delete`

Ta bort en miljö

```bash
magento-cloud environment:deactivate [--delete-branch] [--no-delete-branch] [--inactive] [--merged] [--exclude EXCLUDE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name -->

```bash
environment:deactivate
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Den eller de miljöer som ska tas bort

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--delete-branch`

Ta bort Git-fjärrgrenen
- Standard: `false`
- Accepterar inte ett värde


### `--no-delete-branch`

Ta inte bort Git-fjärrgrenar
- Standard: `false`
- Accepterar inte ett värde


### `--inactive`

Ta bort alla inaktiva miljöer
- Standard: `false`
- Accepterar inte ett värde


### `--merged`

Ta bort alla sammanfogade miljöer
- Standard: `false`
- Accepterar inte ett värde


### `--exclude`

Miljöer som inte ska tas bort
- Standard: `[]`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:http-access`

Uppdatera HTTP-åtkomstinställningar för en miljö

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
httpaccess
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--access`

Åtkomstbegränsning i formatet &quot;permission:address&quot;. Använd 0 för att rensa alla adresser.
- Standard: `[]`
- Kräver ett värde


### `--auth`

HTTP Basic-autentiseringsuppgifter i formatet &quot;username:password&quot;. Använd 0 för att rensa alla autentiseringsuppgifter.
- Standard: `[]`
- Kräver ett värde


### `--enabled`

Anger om åtkomstkontroll ska aktiveras: 1 att aktivera, 0 att inaktivera
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:info`

Läs eller ange egenskaper för en miljö

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
environment:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

Egenskapens namn
<!-- argument -->

### `value`

Ange ett nytt värde för egenskapen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Om cachen ska uppdateras
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:init`

Initiera en miljö från en offentlig Git-databas

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```

<!-- app.name --> <!-- command.usage -->

### `url`

En URL till en Git-databas
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--profile`

Profilens namn
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:list`

Få en lista över miljöer

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
environments
```

<!-- app.name -->

```bash
env
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--no-inactive`, `-I`



Visa inte inaktiva miljöer
- Standard: `false`
- Accepterar inte ett värde


### `--pipe`

Skriv ut en enkel lista över miljö-ID:n.
- Standard: `false`
- Accepterar inte ett värde


### `--refresh`

Anger om listan ska uppdateras.
- Standard: `1`
- Kräver ett värde


### `--sort`

En egenskap som ska sorteras efter
- Standard: `title`
- Kräver ett värde


### `--reverse`

Sortera i omvänd ordning (fallande)
- Standard: `false`
- Accepterar inte ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:logs`

Läs en miljös loggar

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [--] [<type>]
```

<!-- app.name -->

```bash
log
```

<!-- app.name -->

```bash
logs
```

<!-- app.name --> <!-- command.usage -->

### `type`

Loggtypen, t.ex. &quot;access&quot; eller &quot;error&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--lines`

Antalet rader som ska visas
- Standard: `100`
- Kräver ett värde


### `--tail`

Avsluta loggen kontinuerligt
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde


### `--worker`

Ett arbetarnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:merge`

Sammanfoga en miljö

```bash
magento-cloud merge [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
merge
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Den miljö som ska sammanfogas
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:push`

Kodning i en miljö

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--branch] [--parent PARENT] [-W|--no-wait] [--wait] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```

<!-- app.name -->

```bash
push
```

<!-- app.name --> <!-- command.usage -->

### `source`

Källreferens: ett filialnamn eller spara hash
- Standard: `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

Målgrenens namn
- Kräver ett värde



### `--force`, `-f`



Tillåt icke-snabba framåtriktade uppdateringar
- Standard: `false`
- Accepterar inte ett värde


### `--force-with-lease`

Tillåt icke-snabba framåtriktade uppdateringar om fjärrspårningsgrenen är uppdaterad
- Standard: `false`
- Accepterar inte ett värde



### `--set-upstream`, `-u`



Ange målmiljön som den överordnade för källgrenen
- Standard: `false`
- Accepterar inte ett värde


### `--activate`

Aktivera miljön innan du trycker
- Standard: `false`
- Accepterar inte ett värde


### `--branch`

INAKTUELL: alias för —activate
- Standard: `false`
- Accepterar inte ett värde


### `--parent`

Ange en ny överordnad miljö (används endast med —activate eller —branch)
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:redeploy`

Distribuera om en miljö

```bash
magento-cloud redeploy [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
redeploy
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:relationships`

Visa en miljös relationer

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```

<!-- app.name -->

```bash
relationships
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Miljön
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Den relationsegenskap som ska visas
- Kräver ett värde


### `--refresh`

Om relationerna ska uppdateras
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:scp`

Kopiera filer till och från den aktuella miljön med scp

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```

<!-- app.name -->

```bash
scp
```

<!-- app.name --> <!-- command.usage -->

### `files`

Filer som ska kopieras. Använd fjärrkontrollen: för att definiera fjärrplatser.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--recursive`, `-r`



Kopiera hela kataloger rekursivt
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde


### `--worker`

Ett arbetarnamn
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:set-remote`

Ange att fjärrmiljön ska mappa till en gren

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Miljödatorns namn. Ange 0 för att ta bort mappningen för en gren
- Obligatoriskt

   <!-- argument -->

### `branch`

Git-grenen som ska mappas (används som standard för den aktuella grenen)
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:ssh`

SSH till den aktuella miljön

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```

<!-- app.name -->

```bash
ssh
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

Ett kommando som körs i miljön.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

Skriv bara ut SSH-URL:en.
- Standard: `false`
- Accepterar inte ett värde


### `--all`

Skriv ut alla SSH-URL:er (för alla program).
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde


### `--worker`

Ett arbetarnamn
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:synchronize`

Synkronisera en miljös kod och/eller data från dess överordnade

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```

<!-- app.name -->

```bash
sync
```

<!-- app.name --> <!-- command.usage -->

### `synchronize`

Synkronisera: &quot;code&quot;, &quot;data&quot; eller båda

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--rebase`

Synkronisera kod genom att basera om i stället för att sammanfoga
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:url`

Hämta offentliga URL:er för en miljö

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
url
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--primary`, `-1`



Returnera bara URL:en för den primära vägen
- Standard: `false`
- Accepterar inte ett värde


### `--browser`

Webbläsaren som ska användas för att öppna URL-adressen. Ange 0 som ingen.
- Kräver ett värde


### `--pipe`

Skriv ut URL-adressen som ska stoppas.
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `environment:xdebug`

Öppna en tunnel för Xdebug i miljön

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
xdebug
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

Den lokala porten
- Standard: `9000`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde


### `--worker`

Ett arbetarnamn
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `integration:activity:get`

Visa detaljerad information om en enskild integreringsaktivitet

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

Ett integrerings-ID. Lämna tomt om du vill välja från en lista.
<!-- argument -->

### `activity`

Aktivitets-ID. Som standard används den senaste integreringsaktiviteten.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Egenskapen som ska visas
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



[Inaktuellt alternativ, används inte]
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `integration:activity:list`

Få en lista över aktiviteter för en integrering

```bash
magento-cloud i:act [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name -->

```bash
i:act
```

<!-- app.name -->

```bash
integration:activities
```

<!-- app.name --> <!-- command.usage -->

### `id`

Ett integrerings-ID. Lämna tomt om du vill välja från en lista.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Filtrera aktiviteter efter typ
- Kräver ett värde


### `--limit`

Begränsa antalet resultat som visas
- Standard: `10`
- Kräver ett värde


### `--start`

Endast aktiviteter som skapats före detta datum listas
- Kräver ett värde


### `--state`

Filtrera aktiviteter efter delstat
- Standard: `[]`
- Kräver ett värde


### `--result`

Filtrera aktiviteter efter resultat
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



[Inaktuellt alternativ, används inte]
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `integration:activity:log`

Visa loggen för en integreringsaktivitet

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

Ett integrerings-ID. Lämna tomt om du vill välja från en lista.
<!-- argument -->

### `activity`

Aktivitets-ID. Som standard används den senaste integreringsaktiviteten.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--timestamps`, `-t`



Visa en tidsstämpel bredvid varje meddelande
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



[Inaktuellt alternativ, används inte]
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `integration:add`

Lägg till en integrering i projektet

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

Integrationstypen (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;hipchat&#39;, &#39;webkroch&#39;, &#39;health.email&#39;, &#39;health.pageruty&#39;, &#39;health.slack&#39;, &#39;health.webkroch&#39;, &#39;script&#39;)
- Kräver ett värde


### `--base-url`

Bas-URL:en för serverinstallationen
- Kräver ett värde


### `--username`

Användarnamnet för Bitbucket Server
- Kräver ett värde


### `--token`

En åtkomsttoken för integreringen
- Kräver ett värde


### `--key`

En Bitbucket OAuth-konsumentnyckel
- Kräver ett värde


### `--secret`

En Bitbucket OAuth-hemlighet
- Kräver ett värde


### `--server-project`

Projektet (t.ex. &#39;namespace/repo&#39;)
- Kräver ett värde


### `--repository`

Den databas som ska spåras (t.ex. &#39;ägare/databas&#39;)
- Kräver ett värde


### `--build-merge-requests`

GitLab: bygga sammanfogningsbegäranden som miljöer
- Standard: `true`
- Kräver ett värde


### `--build-pull-requests`

Bygg upp alla förfrågningar som en miljö
- Standard: `true`
- Kräver ett värde


### `--build-draft-pull-requests`

Bygg släppbegäranden
- Standard: `true`
- Kräver ett värde


### `--build-pull-requests-post-merge`

Skapa pull-begäranden baserat på deras status efter sammanfogning
- Standard: `false`
- Kräver ett värde


### `--build-wip-merge-requests`

GitLab: skapa begäran om sammanfogning av PIA
- Standard: `true`
- Kräver ett värde


### `--merge-requests-clone-parent-data`

GitLab: klona data för sammanfogningsbegäranden
- Standard: `true`
- Kräver ett värde


### `--pull-requests-clone-parent-data`

Klona den överordnade miljöns data för pull-begäranden
- Standard: `true`
- Kräver ett värde


### `--resync-pull-requests`

Synkronisera miljödata för pull-begäran på nytt vid varje bygge
- Standard: `false`
- Kräver ett värde


### `--fetch-branches`

Hämta alla grenar från fjärrkontrollen (som inaktiva miljöer)
- Standard: `true`
- Kräver ett värde


### `--prune-branches`

Ta bort grenar som inte finns på fjärrkontrollen
- Standard: `true`
- Kräver ett värde


### `--room`

HipChat-rums-ID
- Kräver ett värde


### `--url`

Webkrok: en URL som tar emot JSON-data
- Kräver ett värde


### `--shared-key`

Webkrok: den delade hemliga nyckeln för JWS
- Kräver ett värde


### `--file`

Namnet på en lokal fil som innehåller skriptet som ska överföras
- Kräver ett värde


### `--events`

En lista över händelser som ska hanteras, t.ex. environment.push
- Standard: `*`
- Kräver ett värde


### `--states`

En lista över lägen att agera på, t.ex. väntande, in_progress, slutfört
- Standard: `complete`
- Kräver ett värde


### `--environments`

De miljö-ID som ska inkluderas
- Standard: `*`
- Kräver ett värde


### `--excluded-environments`

De miljö-ID som ska uteslutas
- Standard: `[]`
- Kräver ett värde


### `--from-address`

[Valfritt] Anpassad avsändaradress för varningsmeddelanden
- Kräver ett värde


### `--recipients`

Mottagarens e-postadress(er)
- Standard: `[]`
- Kräver ett värde


### `--channel`

Kanalen Slack
- Kräver ett värde


### `--routing-key`

PagerDuty-routningsnyckeln
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `integration:delete`

Ta bort en integrering från ett projekt

```bash
magento-cloud integration:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Integrations-ID. Lämna tomt om du vill välja från en lista.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `integration:get`

Visa information om en integrering

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Ett integrerings-ID. Lämna tomt om du vill välja från en lista.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Den integrationsegenskap som ska visas
- Accepterar ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `integration:list`

Visa en lista över projektintegrering(ar)

```bash
magento-cloud integrations [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
integrations
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `integration:update`

Uppdatera en integrering

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

ID för den integrering som ska uppdateras
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Integrationstypen (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;hipchat&#39;, &#39;webkroch&#39;, &#39;health.email&#39;, &#39;health.pageruty&#39;, &#39;health.slack&#39;, &#39;health.webkroch&#39;, &#39;script&#39;)
- Kräver ett värde


### `--base-url`

Bas-URL:en för serverinstallationen
- Kräver ett värde


### `--username`

Användarnamnet för Bitbucket Server
- Kräver ett värde


### `--token`

En åtkomsttoken för integreringen
- Kräver ett värde


### `--key`

En Bitbucket OAuth-konsumentnyckel
- Kräver ett värde


### `--secret`

En Bitbucket OAuth-hemlighet
- Kräver ett värde


### `--server-project`

Projektet (t.ex. &#39;namespace/repo&#39;)
- Kräver ett värde


### `--repository`

Den databas som ska spåras (t.ex. &#39;ägare/databas&#39;)
- Kräver ett värde


### `--build-merge-requests`

GitLab: bygga sammanfogningsbegäranden som miljöer
- Standard: `true`
- Kräver ett värde


### `--build-pull-requests`

Bygg upp alla förfrågningar som en miljö
- Standard: `true`
- Kräver ett värde


### `--build-draft-pull-requests`

Bygg släppbegäranden
- Standard: `true`
- Kräver ett värde


### `--build-pull-requests-post-merge`

Skapa pull-begäranden baserat på deras status efter sammanfogning
- Standard: `false`
- Kräver ett värde


### `--build-wip-merge-requests`

GitLab: skapa begäran om sammanfogning av PIA
- Standard: `true`
- Kräver ett värde


### `--merge-requests-clone-parent-data`

GitLab: klona data för sammanfogningsbegäranden
- Standard: `true`
- Kräver ett värde


### `--pull-requests-clone-parent-data`

Klona den överordnade miljöns data för pull-begäranden
- Standard: `true`
- Kräver ett värde


### `--resync-pull-requests`

Synkronisera miljödata för pull-begäran på nytt vid varje bygge
- Standard: `false`
- Kräver ett värde


### `--fetch-branches`

Hämta alla grenar från fjärrkontrollen (som inaktiva miljöer)
- Standard: `true`
- Kräver ett värde


### `--prune-branches`

Ta bort grenar som inte finns på fjärrkontrollen
- Standard: `true`
- Kräver ett värde


### `--room`

HipChat-rums-ID
- Kräver ett värde


### `--url`

Webkrok: en URL som tar emot JSON-data
- Kräver ett värde


### `--shared-key`

Webkrok: den delade hemliga nyckeln för JWS
- Kräver ett värde


### `--file`

Namnet på en lokal fil som innehåller skriptet som ska överföras
- Kräver ett värde


### `--events`

En lista över händelser som ska hanteras, t.ex. environment.push
- Standard: `*`
- Kräver ett värde


### `--states`

En lista över lägen att agera på, t.ex. väntande, in_progress, slutfört
- Standard: `complete`
- Kräver ett värde


### `--environments`

De miljö-ID som ska inkluderas
- Standard: `*`
- Kräver ett värde


### `--excluded-environments`

De miljö-ID som ska uteslutas
- Standard: `[]`
- Kräver ett värde


### `--from-address`

[Valfritt] Anpassad avsändaradress för varningsmeddelanden
- Kräver ett värde


### `--recipients`

Mottagarens e-postadress(er)
- Standard: `[]`
- Kräver ett värde


### `--channel`

Kanalen Slack
- Kräver ett värde


### `--routing-key`

PagerDuty-routningsnyckeln
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `integration:validate`

Validera en befintlig integrering

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Ett integrerings-ID. Lämna tomt om du vill välja från en lista.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `local:build`

Bygg det aktuella projektet lokalt

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```

<!-- app.name -->

```bash
build
```

<!-- app.name --> <!-- command.usage -->

### `app`

Ange vilka program som ska byggas

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--abslinks`, `-a`



Använd absoluta länkar
- Standard: `false`
- Accepterar inte ett värde



### `--source`, `-s`



Källkatalogen. Standardvärdet är den aktuella projektroten.
- Kräver ett värde



### `--destination`, `-d`



Det mål som webbroten för varje program ska länkas till. Standard: _www
- Kräver ett värde



### `--copy`, `-c`



Kopiera till en byggkatalog i stället för att länka från källan
- Standard: `false`
- Accepterar inte ett värde


### `--clone`

Använd Git för att klona HEAD till byggkatalogen
- Standard: `false`
- Accepterar inte ett värde


### `--run-deploy-hooks`

Kör hookar för driftsättning och/eller post_deploy
- Standard: `false`
- Accepterar inte ett värde


### `--no-clean`

Ta inte bort gamla byggen
- Standard: `false`
- Accepterar inte ett värde


### `--no-archive`

Skapa eller använd inte ett byggarkiv
- Standard: `false`
- Accepterar inte ett värde


### `--no-backup`

Säkerhetskopiera inte föregående version
- Standard: `false`
- Accepterar inte ett värde


### `--no-cache`

Inaktivera cachelagring
- Standard: `false`
- Accepterar inte ett värde


### `--no-build-hooks`

Kör inte kopplingar efter bygget
- Standard: `false`
- Accepterar inte ett värde


### `--no-deps`

Installera inte byggberoenden lokalt
- Standard: `false`
- Accepterar inte ett värde


### `--working-copy`

Dra: använda git för att klona en databas för varje Drupal-modul i stället för att bara ladda ned en version
- Standard: `false`
- Accepterar inte ett värde


### `--concurrency`

Dra: ange antalet samtidiga projekt som ska bearbetas samtidigt
- Standard: `4`
- Kräver ett värde


### `--lock`

Dra: skapa eller uppdatera en låsfil (endast tillgänglig med Drush version 7+)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `local:clean`

Ta bort gamla projektbyggen

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```

<!-- app.name -->

```bash
clean
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--keep`

Maximalt antal byggen som ska behållas
- Standard: `5`
- Kräver ett värde


### `--max-age`

Högsta byggålder i sekunder. Ignoreras om den inte har angetts.
- Kräver ett värde


### `--include-active`

Ta bort aktiva byggen
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `local:dir`

Hitta den lokala projektroten

```bash
magento-cloud dir [<subdir>]
```

<!-- app.name -->

```bash
dir
```

<!-- app.name --> <!-- command.usage -->

### `subdir`

Den underkatalog som ska hittas (&#39;local&#39;, &#39;web&#39; eller &#39;shared&#39;)
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `mount:download`

Hämta filer från en montering med hjälp av synkronisering

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Ladda ned från alla monteringar
- Standard: `false`
- Accepterar inte ett värde



### `--mount`, `-m`



Monteringen (som en apprelativ sökväg)
- Kräver ett värde


### `--target`

Katalogen som filerna ska hämtas till. Om —all används läggs monteringssökvägen till
- Kräver ett värde


### `--source-path`

Använd monteringens källsökväg (i stället för monteringssökvägen) som en underkatalog till målet, när —all används
- Standard: `false`
- Accepterar inte ett värde


### `--delete`

Om överflödiga filer ska tas bort i målkatalogen
- Standard: `false`
- Accepterar inte ett värde


### `--exclude`

Fil(er) som ska uteslutas från nedladdningen (mönster)
- Standard: `[]`
- Kräver ett värde


### `--include`

Fil(er) som ska inkluderas i hämtningen (mönster)
- Standard: `[]`
- Kräver ett värde


### `--refresh`

Om cachen ska uppdateras
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde


### `--worker`

Ett arbetarnamn
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `mount:list`

Få en lista över monteringar

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name -->

```bash
mounts
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--paths`

Utdata endast för monteringsbanor (en per rad)
- Standard: `false`
- Accepterar inte ett värde


### `--refresh`

Om cachen ska uppdateras
- Standard: `false`
- Accepterar inte ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde


### `--worker`

Ett arbetarnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `mount:size`

Kontrollera diskanvändning av monteringar

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



Visa storlekar i byte
- Standard: `false`
- Accepterar inte ett värde


### `--refresh`

Uppdatera cacheminnet
- Standard: `false`
- Accepterar inte ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde


### `--worker`

Ett arbetarnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `mount:upload`

Överför filer till en plats med hjälp av synkronisering

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--source`

En katalog som innehåller filer som ska överföras
- Kräver ett värde



### `--mount`, `-m`



Monteringen (som en apprelativ sökväg)
- Kräver ett värde


### `--delete`

Om överflödiga filer ska tas bort i monteringen
- Standard: `false`
- Accepterar inte ett värde


### `--exclude`

Fil(er) som ska uteslutas från överföringen (mönster)
- Standard: `[]`
- Kräver ett värde


### `--include`

Fil(er) som ska inkluderas i överföringen (mönster)
- Standard: `[]`
- Kräver ett värde


### `--refresh`

Om cachen ska uppdateras
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde


### `--worker`

Ett arbetarnamn
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `project:clear-build-cache`

Rensa ett projekts byggcache

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT] [--host HOST]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `project:curl`

Köra en autentiserad cURL-begäran på ett projekts API

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [-p|--project PROJECT] [--host HOST] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

API-sökvägen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



Begärandemetoden som ska användas
- Kräver ett värde



### `--data`, `-d`



Data som ska skickas
- Kräver ett värde



### `--include`, `-i`



Inkludera sidhuvuden i utdata
- Standard: `false`
- Accepterar inte ett värde



### `--head`, `-I`



Hämta endast rubriker
- Standard: `false`
- Accepterar inte ett värde


### `--disable-compression`

Använd inte flaggan curl —compressed
- Standard: `false`
- Accepterar inte ett värde


### `--enable-glob`

Aktivera bläddring (ta bort flaggan —globoff)
- Standard: `false`
- Accepterar inte ett värde



### `--header`, `-H`



Extra rubrik(er)
- Standard: `[]`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `project:get`

Klona ett projekt lokalt

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [--host HOST] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```

<!-- app.name -->

```bash
get
```

<!-- app.name --> <!-- command.usage -->

### `project`

Projekt-ID
<!-- argument -->

### `directory`

Katalogen som ska klonas. Standardvärdet är projekttiteln
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--environment`, `-e`



Det miljö-ID som ska klonas. Standardvärdet är projektets standardinställning eller den första tillgängliga miljön
- Kräver ett värde


### `--depth`

Skapa en grund klon: begränsa antalet implementeringar i historiken
- Kräver ett värde


### `--build`

Bygg projektet efter kloning
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `project:info`

Läsa eller ange egenskaper för ett projekt

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
project:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

Egenskapens namn
<!-- argument -->

### `value`

Ange ett nytt värde för egenskapen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Om cachen ska uppdateras
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `project:list`

Hämta en lista över alla aktiva projekt

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
projects
```

<!-- app.name -->

```bash
pro
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--pipe`

Skapa en enkel lista med projekt-ID:n
- Standard: `false`
- Accepterar inte ett värde


### `--host`

Filtrera efter regionens värdnamn (exakt matchning)
- Kräver ett värde


### `--title`

Filtrera efter titel (skiftlägesokänslig sökning)
- Kräver ett värde


### `--my`

Visa endast de projekt du äger
- Standard: `false`
- Accepterar inte ett värde


### `--refresh`

Om listan ska uppdateras
- Standard: `1`
- Kräver ett värde


### `--sort`

En egenskap som ska sorteras efter
- Standard: `title`
- Kräver ett värde


### `--reverse`

Sortera i omvänd ordning (fallande)
- Standard: `false`
- Accepterar inte ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `project:set-remote`

Ange fjärrprojektet för den aktuella Git-databasen

```bash
magento-cloud project:set-remote [<project>]
```

<!-- app.name --> <!-- command.usage -->

### `project`

Projekt-ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Ta bort en variabel från ett projekt

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Variabelnamnet
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Visa variabler för ett projekt

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name -->

```bash
project-variables
```

<!-- app.name -->

```bash
pvget
```

<!-- app.name -->

```bash
project:variable:list
```

<!-- app.name --> <!-- command.usage -->

### `name`

Variabelns namn
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

Utdata för endast det fullständiga variabelvärdet (ett &quot;name&quot; måste anges)
- Standard: `false`
- Accepterar inte ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Ange en variabel för ett projekt

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
pvset
```

<!-- app.name --> <!-- command.usage -->

### `name`

Variabelnamnet
- Obligatoriskt

   <!-- argument -->

### `value`

Variabelvärdet
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

Markera värdet som JSON
- Standard: `false`
- Accepterar inte ett värde


### `--no-visible-build`

Visa inte den här variabeln vid byggtillfället
- Standard: `false`
- Accepterar inte ett värde


### `--no-visible-runtime`

Visa inte den här variabeln vid körning
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `repo:cat`

Läsa en fil i projektdatabasen

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

Sökvägen till filen
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--commit`, `-c`



Verkställ SHA. Detta kan även acceptera suffixen &quot;HEAD&quot; och cirkumflex (^) eller tilde (~) för överordnade implementeringar.
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `repo:ls`

Visa filer i projektdatabasen

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Sökvägen till en underkatalog
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--directories`, `-d`



Visa endast kataloger
- Standard: `false`
- Accepterar inte ett värde



### `--files`, `-f`



Visa endast filer
- Standard: `false`
- Accepterar inte ett värde


### `--git-style`

Formatutdata som liknar &quot;git ls-tree&quot;
- Standard: `false`
- Accepterar inte ett värde



### `--commit`, `-c`



Verkställ SHA. Detta kan även acceptera suffixen &quot;HEAD&quot; och cirkumflex (^) eller tilde (~) för överordnade implementeringar.
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `route:get`

Visa detaljerad information om ett flöde

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```

<!-- app.name --> <!-- command.usage -->

### `route`

Vägets ursprungliga URL
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--id`

Ett rutt-ID att välja
- Kräver ett värde



### `--primary`, `-1`



Välj primärt flöde
- Standard: `false`
- Accepterar inte ett värde



### `--property`, `-P`



Egenskapen som ska visas
- Kräver ett värde


### `--refresh`

Kringgå cacheminnet för vägar
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



[Inaktuellt alternativ, används inte längre]
- Kräver ett värde



### `--identity-file`, `-i`



[Inaktuellt alternativ, används inte längre]
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `route:list`

Visa alla vägar för en miljö

```bash
magento-cloud routes [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<environment>]
```

<!-- app.name -->

```bash
routes
```

<!-- app.name -->

```bash
environment:routes
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Miljö-ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Kringgå cacheminnet för vägar
- Standard: `false`
- Accepterar inte ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `self:install`

Installera eller uppdatera CLI-konfigurationsfiler

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```

<!-- app.name -->

```bash
local:install
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--shell-type`

Gränssnittstypen för automatisk komplettering (bash eller zsh)
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `self:stats`

Visa statistik för hämtningar av GitHub-paket

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--page`, `-p`



Sidnummer
- Standard: `1`
- Kräver ett värde



### `--count`, `-c`



Resultat per sida (max: 100)
- Standard: `20`
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `self:update`

Uppdatera CLI till den senaste versionen

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```

<!-- app.name -->

```bash
self-update
```

<!-- app.name -->

```bash
update
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-major`

Uppdatera endast mellan mindre versioner eller korrigeringsversioner
- Standard: `false`
- Accepterar inte ett värde


### `--unstable`

Uppdatera till en ny instabil version, om en sådan finns
- Standard: `false`
- Accepterar inte ett värde


### `--manifest`

Åsidosätt manifestfilens plats
- Kräver ett värde


### `--current-version`

Åsidosätt den aktuella versionen
- Kräver ett värde


### `--timeout`

En timeout för versionskontrollen
- Standard: `30`
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `service:list`

Visa tjänster i projektet

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
services
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Om cachen ska uppdateras
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `service:mongo:dump`

Skapa en binär arkivdump av data från MongoDB

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongodump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



Samlingen som ska dumpas
- Kräver ett värde



### `--gzip`, `-z`



Komprimera dumpen med gzip
- Standard: `false`
- Accepterar inte ett värde



### `--stdout`, `-o`



Utdata till STDOUT i stället för en fil
- Standard: `false`
- Accepterar inte ett värde



### `--relationship`, `-r`



Den tjänstrelation som ska användas
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `service:mongo:export`

Exportera data från MongoDB

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongoexport
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



Samlingen som ska exporteras
- Kräver ett värde


### `--jsonArray`

Exportera data som en enda JSON-array
- Standard: `false`
- Accepterar inte ett värde


### `--type`

Exporttyp, t.ex. &quot;csv&quot;
- Kräver ett värde



### `--fields`, `-f`



De fält som ska exporteras
- Standard: `[]`
- Kräver ett värde



### `--relationship`, `-r`



Den tjänstrelation som ska användas
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `service:mongo:restore`

Återställa en binär arkivdump av data till MongoDB

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongorestore
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



Samlingen som ska återställas
- Kräver ett värde



### `--relationship`, `-r`



Den tjänstrelation som ska användas
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `service:mongo:shell`

Använd MongoDB-skalet

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongo
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--eval`

Skicka ett JavaScript-fragment till skalet
- Kräver ett värde



### `--relationship`, `-r`



Den tjänstrelation som ska användas
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `service:redis-cli`

Åtkomst till Redis CLI

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```

<!-- app.name -->

```bash
redis
```

<!-- app.name --> <!-- command.usage -->

### `args`

Argument som ska läggas till i Redis-kommandot
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--relationship`, `-r`



Den tjänstrelation som ska användas
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Växla mellan sessioner

```bash
magento-cloud session:switch [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Nytt sessions-ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `snapshot:create`

Ta en ögonblicksbild av en miljö

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
backup
```

<!-- app.name -->

```bash
backup:create
```

<!-- app.name -->

```bash
environment:backup
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Miljön
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--live`

Live-säkerhetskopiering: stoppa inte miljön. Om detta anges kommer miljön att vara igång och öppen för anslutningar under säkerhetskopieringen. Detta minskar driftstoppen och riskerar att data säkerhetskopieras i ett inkonsekvent tillstånd.
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `snapshot:list`

Visa tillgängliga ögonblicksbilder av en miljö

```bash
magento-cloud snapshots [--limit LIMIT] [--start START] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
snapshots
```

<!-- app.name -->

```bash
backups
```

<!-- app.name -->

```bash
backup:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--limit`

Begränsa antalet ögonblicksbilder till listan
- Standard: `10`
- Kräver ett värde


### `--start`

Endast ögonblicksbilder som skapats före detta datum visas
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `snapshot:restore`

Återställ en ögonblicksbild av miljön

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```

<!-- app.name -->

```bash
environment:restore
```

<!-- app.name -->

```bash
snapshot:restore
```

<!-- app.name --> <!-- command.usage -->

### `snapshot`

Namnet på ögonblicksbilden. Standardvärdet är den senaste
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

Den miljö som ska återställas till. Standardvärdet är ögonblicksbildens aktuella miljö
- Kräver ett värde


### `--branch-from`

Om —target inte finns än, anger detta den överordnade för den nya miljön
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Kör en källåtgärd

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```

<!-- app.name --> <!-- command.usage -->

### `operation`

Åtgärdsnamnet
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--variable`

En variabel som ska anges under åtgärden, i formatet &lt;info>type:name=value&lt;/info>
- Standard: `[]`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `ssh-cert:info`

Visa information om det aktuella SSH-certifikatet

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-refresh`

Uppdatera inte certifikatet om det är ogiltigt
- Standard: `false`
- Accepterar inte ett värde



### `--property`, `-P`



Certifikategenskapen som ska visas
- Kräver ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `ssh-cert:load`

Generera ett SSH-certifikat

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh-only`

Uppdatera bara certifikatet om det behövs (skriv inte SSH-konfigurationen)
- Standard: `false`
- Accepterar inte ett värde


### `--new`

Tvinga certifikatet att uppdateras
- Standard: `false`
- Accepterar inte ett värde


### `--new-key`

[Föråldrat] Använd —new i stället
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `ssh-key:add`

Lägg till en ny SSH-nyckel

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Sökvägen till en befintlig offentlig SSH-nyckel
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--name`

Ett namn som identifierar nyckeln
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `ssh-key:delete`

Ta bort en SSH-nyckel

```bash
magento-cloud ssh-key:delete [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

ID för SSH-nyckeln som ska tas bort
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `ssh-key:list`

Hämta en lista med SSH-nycklar i ditt konto

```bash
magento-cloud ssh-keys [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
ssh-keys
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `subscription:info`

Läs eller ändra prenumerationsegenskaper

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<property>] [<value>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

Egenskapens namn
<!-- argument -->

### `value`

Ange ett nytt värde för egenskapen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--id`, `-s`



Prenumerations-ID
- Kräver ett värde


### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)
- Standard: `c`
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `tunnel:close`

Stäng SSH-tunnlar

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Stäng alla tunnlar
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `tunnel:info`

Visa relationsinformation för SSH-tunnlar

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



Den relationsegenskap som ska visas
- Kräver ett värde



### `--encode`, `-c`



Utdata som base64-kodad JSON
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `tunnel:list`

Lista SSH-tunnlar

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
tunnels
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Visa alla tunnlar
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `tunnel:open`

Öppna SSH-tunnlar i en apps relationer

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--gateway-ports`, `-g`



Tillåt att fjärrvärdar ansluter till lokala vidarebefordrade portar
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `tunnel:single`

Öppna en SSH-tunnel till en apprelation

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

Den lokala porten
- Kräver ett värde



### `--gateway-ports`, `-g`



Tillåt att fjärrvärdar ansluter till lokala vidarebefordrade portar
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--app`, `-A`



Namnet på fjärrprogrammet
- Kräver ett värde



### `--relationship`, `-r`



Den tjänstrelation som ska användas
- Kräver ett värde



### `--identity-file`, `-i`



En SSH-identitet (privat nyckel) som ska användas
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `user:add`

Lägg till en användare i projektet

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

Användarens e-postadress
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



Användarens projektroll (admin eller viewer) eller miljöspecifik roll (t.ex. &#39;överordnad:contributor&#39; or &#39;stage:viewer&#39;). Tecknet % kan användas som jokertecken i miljö-ID:t, t.ex. %:viewer. Rollen kan förkortas, t.ex. &#39;överordnad:c&#39;.
- Standard: `[]`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `user:delete`

Ta bort en användare från projektet

```bash
magento-cloud user:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <email>
```

<!-- app.name --> <!-- command.usage -->

### `email`

Användarens e-postadress
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `user:get`

Visa en användares roll

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```

<!-- app.name -->

```bash
user:role
```

<!-- app.name --> <!-- command.usage -->

### `email`

Användarens e-postadress
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Rollnivån (&#39;project&#39; eller &#39;environment&#39;)
- Kräver ett värde


### `--pipe`

Utdata för rollen till stdout (efter att du har gjort några ändringar)
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--role`, `-r`



[Föråldrat: använda användare:uppdatera för att ändra en användares roll(er)]
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `user:list`

Visa projektanvändare

```bash
magento-cloud users [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
users
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `user:update`

Uppdatera användarroller i ett projekt

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

Användarens e-postadress
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



Användarens projektroll (admin eller viewer) eller miljöspecifik roll (t.ex. &#39;överordnad:contributor&#39; or &#39;stage:viewer&#39;). Tecknet % kan användas som jokertecken i miljö-ID:t, t.ex. %:viewer. Rollen kan förkortas, t.ex. &#39;överordnad:c&#39;.
- Standard: `[]`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `variable:create`

Skapa en variabel

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

Variabelnamnet
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Den nivå som variabeln (&#39;project&#39; eller &#39;environment&#39;) ska anges på
- Kräver ett värde


### `--name`

Variabelnamnet
- Kräver ett värde


### `--value`

Variabelns värde
- Kräver ett värde


### `--json`

Om variabeln är JSON-formaterad
- Standard: `false`
- Kräver ett värde


### `--sensitive`

Om variabeln är känslig
- Standard: `false`
- Kräver ett värde


### `--prefix`

Variabelns prefix (t.ex. &#39;none&#39; eller &#39;env:&#39;)
- Standard: `none`
- Kräver ett värde


### `--enabled`

Om variabeln ska aktiveras
- Standard: `true`
- Kräver ett värde


### `--inheritable`

Om variabeln kan ärvas av underordnade miljöer
- Standard: `true`
- Kräver ett värde


### `--visible-build`

Om variabeln ska vara synlig vid byggtillfället
- Standard: `true`
- Kräver ett värde


### `--visible-runtime`

Om variabeln ska vara synlig vid körning
- Standard: `true`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `variable:delete`

Ta bort en variabel

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Variabelnamnet
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Variabelnivån (&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; eller &#39;e&#39;)
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Inaktivera en aktiverad miljönivåvariabel

```bash
magento-cloud variable:disable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Variabelns namn
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Aktivera en inaktiverad miljönivåvariabel

```bash
magento-cloud variable:enable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Variabelns namn
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `variable:get`

Visa en variabel

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```

<!-- app.name -->

```bash
vget
```

<!-- app.name --> <!-- command.usage -->

### `name`

Variabelns namn
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Visa en enskild variabelegenskap
- Kräver ett värde



### `--level`, `-l`



Variabelnivån (&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; eller &#39;e&#39;)
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde


### `--pipe`

[Inaktuellt alternativ] Skriv ut endast variabelvärdet
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `variable:list`

Listvariabler

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
variables
```

<!-- app.name -->

```bash
var
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--level`, `-l`



Variabelnivån (&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; eller &#39;e&#39;)
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Ange en variabel för en miljö

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
vset
```

<!-- app.name --> <!-- command.usage -->

### `name`

Variabelnamnet
- Obligatoriskt

   <!-- argument -->

### `value`

Variabelvärdet
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

Markera värdet som JSON
- Standard: `false`
- Accepterar inte ett värde


### `--disabled`

Markera variabeln som inaktiverad
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `variable:update`

Uppdatera en variabel

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Variabelnamnet
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Variabelnivån (&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; eller &#39;e&#39;)
- Kräver ett värde


### `--value`

Variabelns värde
- Kräver ett värde


### `--json`

Om variabeln är JSON-formaterad
- Standard: `false`
- Kräver ett värde


### `--sensitive`

Om variabeln är känslig
- Standard: `false`
- Kräver ett värde


### `--enabled`

Om variabeln ska aktiveras
- Standard: `true`
- Kräver ett värde


### `--inheritable`

Om variabeln kan ärvas av underordnade miljöer
- Standard: `true`
- Kräver ett värde


### `--visible-build`

Om variabeln ska vara synlig vid byggtillfället
- Standard: `true`
- Kräver ett värde


### `--visible-runtime`

Om variabeln ska vara synlig vid körning
- Standard: `true`
- Kräver ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde



### `--no-wait`, `-W`



Vänta inte på att åtgärden ska slutföras
- Standard: `false`
- Accepterar inte ett värde


### `--wait`

Vänta tills åtgärden har slutförts (standard)
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `worker:list`

Hämta en lista över alla distribuerade arbetare

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
workers
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Om cachen ska uppdateras
- Standard: `false`
- Accepterar inte ett värde



### `--project`, `-p`



Projekt-ID eller URL
- Kräver ett värde


### `--host`

Projektets API-värdnamn
- Kräver ett värde



### `--environment`, `-e`



Miljö-ID
- Kräver ett värde


### `--format`

Utdataformatet (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; eller &quot;plain&quot;)
- Standard: `table`
- Kräver ett värde


### `--columns`

Kolumner att visa (kommaavgränsad lista eller flera värden)
- Standard: `[]`
- Kräver ett värde


### `--no-header`

Skriv inte ut tabellrubriken
- Standard: `false`
- Accepterar inte ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
- Standard: `false`
- Accepterar inte ett värde



### `--yes`, `-y`



Svara ja på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde



### `--no`, `-n`



Besvara&quot;nej&quot; på eventuella ja/nej-frågor. inaktivera interaktion
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->