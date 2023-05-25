---
source-git-commit: ad7f05eaa5f144b5a8616307d65be635a0c499eb
workflow-type: tm+mt
source-wordcount: '29786'
ht-degree: 0%

---
# magento-cloud (Adobe Commerce on cloud infrastructure)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Version**: 1.42.0

Referensen innehåller 134 kommandon som är tillgängliga via `magento-cloud` kommandoradsverktyg.
Den inledande listan genereras automatiskt med `magento-cloud list` på Adobe Commerce om molninfrastruktur.

>[!NOTE]
>
>Den här referensen genereras från programmets kodbas. Om du vill ändra innehållet kan du uppdatera källkoden för motsvarande kommandoimplementering i [kodbas](https://github.com/magento) arkivera och skicka in dina ändringar för granskning. Ett annat sätt är att _Ge oss feedback_ (hitta länken i det övre högra hörnet). Information om riktlinjer för bidrag finns i [Kodavgifter](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

BAS-slutförandekrok.

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

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

- Accepterar ett värde


## `bot`

Magento Cloud Bot

```bash
magento-cloud bot [--party] [--parrot]
```

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `clear-cache`

Rensa CLI-cachen

```bash
magento-cloud clear-cache
```


```bash
clearcache
```


```bash
cc
```

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `decode`

Avkoda en kodad sträng som MAGENTO_CLOUD_VARIABLES

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```


### `value`

Variabelvärdet som ska avkodas

- Obligatoriskt

### `--property`, `-P`

Den egenskap som ska visas i variabeln

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `docs`

Öppna onlinedokumentationen

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```


### `search`

Sökord

- Standard: `[]`

- Array

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `help`

Visar hjälp för ett kommando

```bash
magento-cloud help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

Kommandonamnet

- Standard: `help`


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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `legacy-migrate`

Migrera från den äldre filstrukturen

```bash
magento-cloud legacy-migrate [--no-backup]
```

### `--no-backup`

Skapa ingen säkerhetskopia av projektet.

- Standard: `false`
- Accepterar inte ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `list`

Visar kommandon

```bash
magento-cloud list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```


### `command`

Kommandot som ska köras

- Obligatoriskt

### `namespace`

Namnutrymmets namn


### `--raw`

Utdata för kommandolista

- Standard: `false`
- Accepterar inte ett värde

### `--format`

Utdataformatet (txt, xml, json eller md)

- Standard: `txt`
- Kräver ett värde

### `--all`

Visa alla kommandon, även dolda

- Standard: `false`
- Accepterar inte ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `multi`

Kör ett kommando i flera projekt

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd> (<cmd>)...
```


### `cmd`

Kommandot som ska köras

- Standard: `[]`

- Obligatoriskt
- Array

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `web`

Öppna webbgränssnittet

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `welcome`

Välkommen till Magento Cloud

```bash
magento-cloud welcome
```

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `winky`



```bash
magento-cloud winky
```

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `activity:cancel`

Avbryt en aktivitet

```bash
magento-cloud activity:cancel [--type TYPE] [--exclude-type EXCLUDE-TYPE] [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

Aktivitets-ID. Standardvärdet är den senaste avbrutna aktiviteten.


### `--type`

Filtrera efter typ (när du väljer en standardaktivitet). Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg. Tecknet % kan användas som jokertecken för typen, t.ex. %var% för att välja variabelrelaterade aktiviteter.

- Standard: `[]`
- Kräver ett värde

### `--exclude-type`

Exkludera efter typ (när du väljer en standardaktivitet). Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg. Tecknet % kan användas som jokertecken för att utesluta typer.

- Standard: `[]`
- Kräver ett värde

### `--all`, `-a`

Kontrollera senaste aktiviteter i alla miljöer (när du väljer en standardaktivitet)

- Standard: `false`
- Accepterar inte ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `activity:get`

Visa detaljerad information om en enskild aktivitet

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```


### `id`

Aktivitets-ID. Standardvärdet är den senaste aktiviteten.


### `--property`, `-P`

Egenskapen som ska visas

- Kräver ett värde

### `--type`

Filtrera efter typ (när du väljer en standardaktivitet). Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg. Tecknet % kan användas som jokertecken för typen, t.ex. %var% för att välja variabelrelaterade aktiviteter.

- Standard: `[]`
- Kräver ett värde

### `--exclude-type`

Exkludera efter typ (när du väljer en standardaktivitet). Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg. Tecknet % kan användas som jokertecken för att utesluta typer.

- Standard: `[]`
- Kräver ett värde

### `--state`

Filtrera efter läge (när du väljer en standardaktivitet): in_progress, pending, complete eller canceled. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `activity:list`

Hämta en lista över aktiviteter för en miljö eller ett projekt

```bash
magento-cloud activity:list [-t|--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
activities
```


```bash
act
```

### `--type`, `-t`

Filtrera aktiviteter efter typ Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg. Tecknet % kan användas som jokertecken för typen, t.ex. %var% för att välja variabelrelaterade aktiviteter.

- Standard: `[]`
- Kräver ett värde

### `--exclude-type`, `-x`

Uteslut aktiviteter efter typ. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg. Tecknet % kan användas som jokertecken för att utesluta typer.

- Standard: `[]`
- Kräver ett värde

### `--limit`

Begränsa antalet resultat som visas

- Standard: `10`
- Kräver ett värde

### `--start`

Endast aktiviteter som skapats före detta datum listas

- Kräver ett värde

### `--state`

Filtrera aktiviteter efter tillstånd: in_progress, pending, complete eller canceled. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: id*, created*, description*, progress*, state*, result*, complete, environment, type (* = default columns). Tecknet&quot;+&quot; kan användas som platshållare för standardkolumnerna. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `activity:log`

Visa loggen för en aktivitet

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

Aktivitets-ID. Standardvärdet är den senaste aktiviteten.


### `--refresh`

Intervall för aktivitetsuppdatering (sekunder). Ange 0 om du vill inaktivera uppdatering.

- Standard: `3`
- Kräver ett värde

### `--timestamps`, `-t`

Visa en tidsstämpel bredvid varje meddelande

- Standard: `false`
- Accepterar inte ett värde

### `--type`

Filtrera efter typ (när du väljer en standardaktivitet). Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg. Tecknet % kan användas som jokertecken för typen, t.ex. %var% för att välja variabelrelaterade aktiviteter.

- Standard: `[]`
- Kräver ett värde

### `--exclude-type`

Exkludera efter typ (när du väljer en standardaktivitet). Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg. Tecknet % kan användas som jokertecken för att utesluta typer.

- Standard: `[]`
- Kräver ett värde

### `--state`

Filtrera efter läge (när du väljer en standardaktivitet): in_progress, pending, complete eller canceled. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `api:curl`

Kör en autentiserad cURL-begäran på Magento Cloud API

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [--] [<path>]
```


### `path`

API-sökvägen


### `--request`, `-X`

Begärandemetoden som ska användas

- Kräver ett värde

### `--data`, `-d`

Data som ska skickas

- Kräver ett värde

### `--json`

JSON-data att skicka

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

### `--fail`, `-f`

Misslyckades utan utdata på ett felsvar

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `app:config-get`

Visa konfigurationen för ett program

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `app:list`

Visa program i projektet

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
apps
```

### `--refresh`

Om cachen ska uppdateras

- Standard: `false`
- Accepterar inte ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: namn*, typ*, disk, sökväg, storlek (* = standardkolumner). Tecknet&quot;+&quot; kan användas som platshållare för standardkolumnerna. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `auth:api-token-login`

Logga in på Magento Cloud med en API-token

```bash
magento-cloud auth:api-token-login
```

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `auth:browser-login`

Logga in på Magento Cloud via en webbläsare

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```


```bash
login
```

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `auth:info`

Visa din kontoinformation

```bash
magento-cloud auth:info [--no-auto-login] [-P|--property PROPERTY] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--] [<property>]
```


### `property`

Kontoegenskapen som ska visas


### `--no-auto-login`

Hoppar över automatisk inloggning. Inget skrivs ut om det inte loggas in och avslutningskoden blir 0, förutsatt att inga andra fel inträffar.

- Standard: `false`
- Accepterar inte ett värde

### `--property`, `-P`

Den kontoegenskap som ska visas (alternativ syntax)

- Kräver ett värde

### `--refresh`

Om cachen ska uppdateras

- Standard: `false`
- Accepterar inte ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `auth:logout`

Logga ut från Magento Cloud

```bash
magento-cloud logout [-a|--all] [--other]
```


```bash
logout
```

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Logga in på Magento Cloud med ett användarnamn och lösenord

```bash
magento-cloud auth:password-login
```


```bash
auth:login
```

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `auth:token`

Hämta en OAuth 2-åtkomsttoken för begäranden till Magento Cloud-API:er

```bash
magento-cloud auth:token [-H|--header] [-W|--no-warn]
```

### `--header`, `-H`

Lägg till token som &quot;Authorization: Bearer om du vill skapa en RFC 6750-rubrik

- Standard: `false`
- Accepterar inte ett värde

### `--no-warn`, `-W`

Utelämna den varning som är utskriven som standard till avsändare. Det här alternativet är att föredra framför omdirigering av avsändare, eftersom det skulle dölja andra potentiellt användbara meddelanden.

- Standard: `false`
- Accepterar inte ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `blackfire:setup`

Konfigurera Blackfire.io-integrering för projektet

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `blue-green:conclude`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALFA ]&lt;/> Slutför en blå/grön distribution

```bash
magento-cloud blue-green:conclude [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `blue-green:deploy`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALFA ]&lt;/> Utför en blå/grön distribution

```bash
magento-cloud blue-green:deploy [--routing-percentage ROUTING-PERCENTAGE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--routing-percentage`

Ange den senaste versionens routningsprocent

- Standard: `100`
- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `blue-green:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALFA ]&lt;/> Aktivera blå/gröna distributioner

```bash
magento-cloud blue-green:enable [-%|--routing-percentage ROUTING-PERCENTAGE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--routing-percentage`, `-%`

Ange den senaste versionens routningsprocent

- Standard: `100`
- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `certificate:add`

Lägg till ett SSL-certifikat i projektet

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `certificate:delete`

Ta bort ett certifikat från projektet

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <id>
```


### `id`

Certifikat-ID (eller början av det)

- Obligatoriskt

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `certificate:get`

Visa ett certifikat

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--] <id>
```


### `id`

Certifikat-ID (eller början av det)

- Obligatoriskt

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `certificate:list`

Visa projektcertifikat

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
certificates
```


```bash
certs
```

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

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: skapad, domäner, förfaller, id, utfärdare. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `commit:get`

Visa implementeringsinformation

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--] [<commit>]
```


### `commit`

Verkställ SHA. Detta kan även acceptera suffixen &quot;HEAD&quot; och cirkumflex (^) eller tilde (~) för överordnade implementeringar.

- Standard: `HEAD`


### `--property`, `-P`

Den implementeringsegenskap som ska visas.

- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `commit:list`

Listimplementeringar

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```


```bash
commits
```


### `commit`

Git-starten verkställer SHA. Detta kan även acceptera suffixen &quot;HEAD&quot; och cirkumflex (^) eller tilde (~) för överordnade implementeringar.


### `--limit`

Antalet implementeringar som ska visas.

- Standard: `10`
- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: författare, datum, sha, sammanfattning. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `db:dump`

Skapa en lokal dump av fjärrdatabasen

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```


```bash
sql-dump
```


```bash
environment:sql-dump
```

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `db:size`

Beräkna diskanvändningen för en databas

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

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

Inaktuellt alternativ, används inte längre

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

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: max, percent_used, used. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `db:sql`

Kör SQL på fjärrdatabasen

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```


```bash
sql
```


```bash
environment:sql
```


### `query`

En SQL-sats som ska köras


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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `domain:add`

Lägg till en ny domän i projektet

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Domännamnet

- Obligatoriskt

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `domain:delete`

Ta bort en domän från projektet

```bash
magento-cloud domain:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Domännamnet

- Obligatoriskt

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `domain:get`

Visa detaljerad information om en domän

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--] [<name>]
```


### `name`

Domännamnet


### `--property`, `-P`

Domänegenskapen som ska visas

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `domain:list`

Hämta en lista över alla domäner

```bash
magento-cloud domains [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
domains
```

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: name*, ssl*, created_at*, updated_at (* = standardkolumner). Tecknet&quot;+&quot; kan användas som platshållare för standardkolumnerna. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `domain:update`

Uppdatera en domän

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Domännamnet

- Obligatoriskt

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:activate`

Aktivera en miljö

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


### `environment`

Den eller de miljöer som ska aktiveras

- Standard: `[]`

- Array

### `--parent`

Ange en ny överordnad miljö innan du aktiverar

- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:branch`

Gren och miljön

```bash
magento-cloud branch [--title TITLE] [--type TYPE] [--force] [--no-clone-parent] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```


```bash
branch
```


### `id`

Den nya miljöns ID (filialnamn)


### `parent`

Den nya miljöns överordnade


### `--title`

Den nya miljöns titel

- Kräver ett värde

### `--type`

Den nya miljöns typ

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:checkout`

Kolla in en miljö

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```


```bash
checkout
```


### `id`

ID för miljön som ska checkas ut. Till exempel: &quot;sprint2&quot;


### `--identity-file`, `-i`

En SSH-identitet (privat nyckel) som ska användas

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:curl`

Kör en autentiserad cURL-begäran på en miljös API

```bash
magento-cloud environment:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

API-sökvägen


### `--request`, `-X`

Begärandemetoden som ska användas

- Kräver ett värde

### `--data`, `-d`

Data som ska skickas

- Kräver ett värde

### `--json`

JSON-data att skicka

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

### `--fail`, `-f`

Misslyckades utan utdata på ett felsvar

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:delete`

Ta bort en eller flera miljöer

```bash
magento-cloud environment:delete [--delete-branch] [--no-delete-branch] [--type TYPE] [-t|--only-type ONLY-TYPE] [--exclude EXCLUDE] [--exclude-type EXCLUDE-TYPE] [--inactive] [--merged] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


```bash
environment:deactivate
```


### `environment`

Den eller de miljöer som ska tas bort. Tecknet % kan användas som jokertecken. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

- Standard: `[]`

- Array

### `--delete-branch`

Ta bort Git-gren(er) (inaktiva miljöer)

- Standard: `false`
- Accepterar inte ett värde

### `--no-delete-branch`

Ta inte bort Git-grenar (inaktiva miljöer)

- Standard: `false`
- Accepterar inte ett värde

### `--type`

Ta bort alla miljöer av en typ (som läggs till andra markerade) Om en lista anges som ett värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

- Standard: `[]`
- Kräver ett värde

### `--only-type`, `-t`

Ta endast bort miljö(er) av en viss typ Om en lista anges som ett enskilt värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

- Standard: `[]`
- Kräver ett värde

### `--exclude`

Miljö(er) som inte ska tas bort. Tecknet % kan användas som jokertecken. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

- Standard: `[]`
- Kräver ett värde

### `--exclude-type`

Miljötyper som inte ska tas bort Om en lista anges som ett enskilt värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

- Standard: `[]`
- Kräver ett värde

### `--inactive`

Ta bort alla inaktiva miljöer (lägga till andra markerade)

- Standard: `false`
- Accepterar inte ett värde

### `--merged`

Ta bort alla sammanfogade miljöer (lägga till andra markerade)

- Standard: `false`
- Accepterar inte ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:http-access`

Uppdatera HTTP-åtkomstinställningar för en miljö

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
httpaccess
```

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:info`

Läs eller ange egenskaper för en miljö

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


```bash
environment:metadata
```


### `property`

Egenskapens namn


### `value`

Ange ett nytt värde för egenskapen


### `--refresh`

Om cachen ska uppdateras

- Standard: `false`
- Accepterar inte ett värde

### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)

- Standard: `c`
- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:init`

Initiera en miljö från en offentlig Git-databas

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```


### `url`

En URL till en Git-databas

- Obligatoriskt

### `--profile`

Profilens namn

- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:list`

Få en lista över miljöer

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--type TYPE] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
environments
```


```bash
env
```

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

### `--type`

Filtrera listan efter miljötyp(er). Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

- Standard: `[]`
- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: id*, title*, status*, type*, created, machine_name, updated (* = standardkolumner). Tecknet&quot;+&quot; kan användas som platshållare för standardkolumnerna. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:logs`

Läs en miljös loggar

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [--] [<type>]
```


```bash
log
```


```bash
logs
```


### `type`

Loggtypen, t.ex. &quot;access&quot; eller &quot;error&quot;


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

Inaktuellt alternativ, används inte längre

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

### `--instance`, `-I`

Ett instans-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:merge`

Sammanfoga en miljö

```bash
magento-cloud merge [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


```bash
merge
```


### `environment`

Den miljö som ska sammanfogas


### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:push`

Kodning i en miljö

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--parent PARENT] [--type TYPE] [--no-clone-parent] [-W|--no-wait] [--wait] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```


```bash
push
```


### `source`

Källreferens: ett filialnamn eller spara hash

- Standard: `HEAD`


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

Ange den nya miljön som överordnad (används endast med —activate)

- Kräver ett värde

### `--type`

Ange miljötypen (används endast med —activate )

- Kräver ett värde

### `--no-clone-parent`

Klona inte den överordnade grenens data (används endast med —activate)

- Standard: `false`
- Accepterar inte ett värde

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:redeploy`

Distribuera om en miljö

```bash
magento-cloud redeploy [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
redeploy
```

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:relationships`

Visa en miljös relationer

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```


```bash
relationships
```


### `environment`

Miljön


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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:scp`

Kopiera filer till och från den aktuella miljön med scp

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```


```bash
scp
```


### `files`

Filer som ska kopieras. Använd fjärrkontrollen: för att definiera fjärrplatser.

- Standard: `[]`

- Array

### `--recursive`, `-r`

Kopiera hela kataloger rekursivt

- Standard: `false`
- Accepterar inte ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--instance`, `-I`

Ett instans-ID

- Kräver ett värde

### `--identity-file`, `-i`

En SSH-identitet (privat nyckel) som ska användas

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:set-remote`

Ange att fjärrmiljön ska mappa till en gren

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```


### `environment`

Miljödatorns namn. Ange 0 för att ta bort mappningen för en gren

- Obligatoriskt

### `branch`

Git-grenen som ska mappas (används som standard för den aktuella grenen)


### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:ssh`

SSH till den aktuella miljön

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```


```bash
ssh
```


### `cmd`

Ett kommando som körs i miljön.

- Standard: `[]`

- Array

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

Inaktuellt alternativ, används inte längre

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

### `--instance`, `-I`

Ett instans-ID

- Kräver ett värde

### `--identity-file`, `-i`

En SSH-identitet (privat nyckel) som ska användas

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:synchronize`

Synkronisera en miljös kod och/eller data från dess överordnade

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```


```bash
sync
```


### `synchronize`

Synkronisera: &quot;code&quot;, &quot;data&quot; eller båda

- Standard: `[]`

- Array

### `--rebase`

Synkronisera kod genom att basera om i stället för att sammanfoga

- Standard: `false`
- Accepterar inte ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:url`

Hämta offentliga URL:er för en miljö

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
url
```

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `environment:xdebug`

Öppna en tunnel för Xdebug i miljön

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```


```bash
xdebug
```

### `--port`

Den lokala porten

- Standard: `9000`
- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--instance`, `-I`

Ett instans-ID

- Kräver ett värde

### `--identity-file`, `-i`

En SSH-identitet (privat nyckel) som ska användas

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `integration:activity:get`

Visa detaljerad information om en enskild integreringsaktivitet

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```


### `integration`

Ett integrerings-ID. Lämna tomt om du vill välja från en lista.


### `activity`

Aktivitets-ID. Som standard används den senaste integreringsaktiviteten.


### `--property`, `-P`

Egenskapen som ska visas

- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

[Inaktuellt alternativ, används inte]

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `integration:activity:list`

Få en lista över aktiviteter för en integrering

```bash
magento-cloud i:act [--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


```bash
i:act
```


```bash
integration:activities
```


### `id`

Ett integrerings-ID. Lämna tomt om du vill välja från en lista.


### `--type`

Filtrera aktiviteter efter typ. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

- Standard: `[]`
- Kräver ett värde

### `--exclude-type`, `-x`

Uteslut aktiviteter efter typ. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg. Tecknet % kan användas som jokertecken för att utesluta typer.

- Standard: `[]`
- Kräver ett värde

### `--limit`

Begränsa antalet resultat som visas

- Standard: `10`
- Kräver ett värde

### `--start`

Endast aktiviteter som skapats före detta datum listas

- Kräver ett värde

### `--state`

Filtrera aktiviteter efter stat. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

- Standard: `[]`
- Kräver ett värde

### `--result`

Filtrera aktiviteter efter resultat

- Kräver ett värde

### `--incomplete`, `-i`

Endast lista ofullständiga aktiviteter

- Standard: `false`
- Accepterar inte ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: id*, created*, description*, type*, state*, result*, complete (* = standardkolumner). Tecknet&quot;+&quot; kan användas som platshållare för standardkolumnerna. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

[Inaktuellt alternativ, används inte]

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `integration:activity:log`

Visa loggen för en integreringsaktivitet

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```


### `integration`

Ett integrerings-ID. Lämna tomt om du vill välja från en lista.


### `activity`

Aktivitets-ID. Som standard används den senaste integreringsaktiviteten.


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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

[Inaktuellt alternativ, används inte]

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `integration:add`

Lägg till en integrering i projektet

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--license-key LICENSE-KEY] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [--category CATEGORY] [--index INDEX] [--sourcetype SOURCETYPE] [--protocol PROTOCOL] [--syslog-host SYSLOG-HOST] [--syslog-port SYSLOG-PORT] [--facility FACILITY] [--message-format MESSAGE-FORMAT] [--auth-mode AUTH-MODE] [--auth-token AUTH-TOKEN] [--verify-tls VERIFY-TLS] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--type`

Integrationstypen (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;webkroch&#39;, &#39;health.email&#39;, &#39;health.pageruty&#39;, &#39;health.slack&#39;, &#39;health.webkrok&#39;, &#39;script&#39;, &#39;newrelic&#39;, &#39;splunk&#39;, &#39;sumologic&#39;, &#39;syslog&#39;)

- Kräver ett värde

### `--base-url`

Bas-URL:en för serverinstallationen

- Kräver ett värde

### `--username`

Användarnamnet för Bitbucket Server

- Kräver ett värde

### `--token`

En autentiserings- eller åtkomsttoken för integreringen

- Kräver ett värde

### `--key`

En Bitbucket OAuth-konsumentnyckel

- Kräver ett värde

### `--secret`

En Bitbucket OAuth-hemlighet

- Kräver ett värde

### `--license-key`

Licensnyckeln för New Relic Logs

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

### `--url`

Integreringens URL- eller API-slutpunkt

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

### `--category`

Kategorin Sumo Logic, som används för filtrering

- Kräver ett värde

### `--index`

Splunk-indexvärdet

- Kräver ett värde

### `--sourcetype`

Källtypen för Splunk-händelsen

- Kräver ett värde

### `--protocol`

Syslog-transportprotokoll (&#39;tcp&#39;, &#39;udp&#39;, &#39;tls&#39;)

- Standard: `tls`
- Kräver ett värde

### `--syslog-host`

Syslog relay/collector host

- Kräver ett värde

### `--syslog-port`

Syslog-relä/insamlarport

- Kräver ett värde

### `--facility`

Syslog-funktion

- Standard: `1`
- Kräver ett värde

### `--message-format`

Syslog-meddelandeformat (&#39;rfc3164&#39; eller &#39;rfc5424&#39;)

- Standard: `rfc5424`
- Kräver ett värde

### `--auth-mode`

Autentiseringsläge (prefix eller Structure_data)

- Standard: `prefix`
- Kräver ett värde

### `--auth-token`

Autentiseringstoken

- Kräver ett värde

### `--verify-tls`

Om HTTPS-certifikatverifiering ska vara aktiverat (rekommenderas)

- Standard: `true`
- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `integration:delete`

Ta bort en integrering från ett projekt

```bash
magento-cloud integration:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

Integrations-ID. Lämna tomt om du vill välja från en lista.


### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `integration:get`

Visa information om en integrering

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<id>]
```


### `id`

Ett integrerings-ID. Lämna tomt om du vill välja från en lista.


### `--property`, `-P`

Den integrationsegenskap som ska visas

- Accepterar ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `integration:list`

Visa en lista över projektintegrering(ar)

```bash
magento-cloud integrations [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
integrations
```

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: id, summary, type. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `integration:update`

Uppdatera en integrering

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--license-key LICENSE-KEY] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [--category CATEGORY] [--index INDEX] [--sourcetype SOURCETYPE] [--protocol PROTOCOL] [--syslog-host SYSLOG-HOST] [--syslog-port SYSLOG-PORT] [--facility FACILITY] [--message-format MESSAGE-FORMAT] [--auth-mode AUTH-MODE] [--auth-token AUTH-TOKEN] [--verify-tls VERIFY-TLS] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

ID för den integrering som ska uppdateras


### `--type`

Integrationstypen (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;webkroch&#39;, &#39;health.email&#39;, &#39;health.pageruty&#39;, &#39;health.slack&#39;, &#39;health.webkrok&#39;, &#39;script&#39;, &#39;newrelic&#39;, &#39;splunk&#39;, &#39;sumologic&#39;, &#39;syslog&#39;)

- Kräver ett värde

### `--base-url`

Bas-URL:en för serverinstallationen

- Kräver ett värde

### `--username`

Användarnamnet för Bitbucket Server

- Kräver ett värde

### `--token`

En autentiserings- eller åtkomsttoken för integreringen

- Kräver ett värde

### `--key`

En Bitbucket OAuth-konsumentnyckel

- Kräver ett värde

### `--secret`

En Bitbucket OAuth-hemlighet

- Kräver ett värde

### `--license-key`

Licensnyckeln för New Relic Logs

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

### `--url`

Integreringens URL- eller API-slutpunkt

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

### `--category`

Kategorin Sumo Logic, som används för filtrering

- Kräver ett värde

### `--index`

Splunk-indexvärdet

- Kräver ett värde

### `--sourcetype`

Källtypen för Splunk-händelsen

- Kräver ett värde

### `--protocol`

Syslog-transportprotokoll (&#39;tcp&#39;, &#39;udp&#39;, &#39;tls&#39;)

- Standard: `tls`
- Kräver ett värde

### `--syslog-host`

Syslog relay/collector host

- Kräver ett värde

### `--syslog-port`

Syslog-relä/insamlarport

- Kräver ett värde

### `--facility`

Syslog-funktion

- Standard: `1`
- Kräver ett värde

### `--message-format`

Syslog-meddelandeformat (&#39;rfc3164&#39; eller &#39;rfc5424&#39;)

- Standard: `rfc5424`
- Kräver ett värde

### `--auth-mode`

Autentiseringsläge (prefix eller Structure_data)

- Standard: `prefix`
- Kräver ett värde

### `--auth-token`

Autentiseringstoken

- Kräver ett värde

### `--verify-tls`

Om HTTPS-certifikatverifiering ska vara aktiverat (rekommenderas)

- Standard: `true`
- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `integration:validate`

Validera en befintlig integrering

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--] [<id>]
```


### `id`

Ett integrerings-ID. Lämna tomt om du vill välja från en lista.


### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `local:build`

Bygg det aktuella projektet lokalt

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```


```bash
build
```


### `app`

Ange vilka program som ska byggas

- Standard: `[]`

- Array

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `local:clean`

Ta bort gamla projektbyggen

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```


```bash
clean
```

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `local:dir`

Hitta den lokala projektroten

```bash
magento-cloud dir [<subdir>]
```


```bash
dir
```


### `subdir`

Den underkatalog som ska hittas (&#39;local&#39;, &#39;web&#39; eller &#39;shared&#39;)


### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `metrics:disk-usage`

Visa diskanvändning för en tjänst

```bash
magento-cloud disk [-s|--service SERVICE] [--type TYPE] [-r|--range RANGE] [-i|--interval INTERVAL] [--to TO] [-B|--bytes] [-1|--latest] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```


```bash
disk
```

### `--service`, `-s`

Tjänstnamnet

- Kräver ett värde

### `--type`

Servicetyp (om tjänstens namn inte anges), t.ex. mysql, pgsql, mongodb osv. Typversionen är inte obligatorisk.

- Kräver ett värde

### `--range`, `-r`

Tidsintervall. Mätvärden läses in för den här varaktigheten till sluttiden (—to). Du kan ange enheter: timmar (h), minuter (m) eller sekunder (s). Minimum &lt;comment>5 m&lt;/comment>, max &lt;comment>8 tim&lt;/comment> eller mer (beroende på projektet), standard &lt;comment>10 m&lt;/comment>.

- Kräver ett värde

### `--interval`, `-i`

Tidsintervallet. Standardvärdet är en division av intervallet. Du kan ange enheter: timmar (h), minuter (m) eller sekunder (s). Minimum &lt;comment>1 m&lt;/comment>, max &lt;comment>1h&lt;/comment>.

- Kräver ett värde

### `--to`

Sluttiden. Standardvärdet är nu.

- Kräver ett värde

### `--bytes`, `-B`

Visa storlekar i byte

- Standard: `false`
- Accepterar inte ett värde

### `--latest`, `-1`

Visa endast den senaste enskilda datapunkten

- Standard: `false`
- Accepterar inte ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: timestamp*, used*, limit*, percent*, ipercent*, ilimit, interval, is used (* = default columns). Tecknet&quot;+&quot; kan användas som platshållare för standardkolumnerna. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `mount:download`

Hämta filer från en montering med hjälp av synkronisering

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```

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

Inaktuellt alternativ, används inte längre

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

### `--instance`, `-I`

Ett instans-ID

- Kräver ett värde

### `--identity-file`, `-i`

En SSH-identitet (privat nyckel) som ska användas

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `mount:list`

Få en lista över monteringar

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE]
```


```bash
mounts
```

### `--paths`

Utdata endast för monteringsbanor (en per rad)

- Standard: `false`
- Accepterar inte ett värde

### `--refresh`

Om cachen ska uppdateras

- Standard: `false`
- Accepterar inte ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: definition, sökväg. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

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

### `--instance`, `-I`

Ett instans-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `mount:size`

Kontrollera diskanvändning av monteringar

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE]
```

### `--bytes`, `-B`

Visa storlekar i byte

- Standard: `false`
- Accepterar inte ett värde

### `--refresh`

Uppdatera cacheminnet

- Standard: `false`
- Accepterar inte ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: available, max, monts, percent_used, sizes, used. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

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

### `--instance`, `-I`

Ett instans-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `mount:upload`

Överför filer till en plats med hjälp av synkronisering

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```

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

Inaktuellt alternativ, används inte längre

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

### `--instance`, `-I`

Ett instans-ID

- Kräver ett värde

### `--identity-file`, `-i`

En SSH-identitet (privat nyckel) som ska användas

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `project:clear-build-cache`

Rensa ett projekts byggcache

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT]
```

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `project:curl`

Köra en autentiserad cURL-begäran på ett projekts API

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [--] [<path>]
```


### `path`

API-sökvägen


### `--request`, `-X`

Begärandemetoden som ska användas

- Kräver ett värde

### `--data`, `-d`

Data som ska skickas

- Kräver ett värde

### `--json`

JSON-data att skicka

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

### `--fail`, `-f`

Misslyckades utan utdata på ett felsvar

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `project:get`

Klona ett projekt lokalt

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```


```bash
get
```


### `project`

Projekt-ID


### `directory`

Katalogen som ska klonas. Standardvärdet är projekttiteln


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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--identity-file`, `-i`

En SSH-identitet (privat nyckel) som ska användas

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `project:info`

Läsa eller ange egenskaper för ett projekt

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


```bash
project:metadata
```


### `property`

Egenskapens namn


### `value`

Ange ett nytt värde för egenskapen


### `--refresh`

Om cachen ska uppdateras

- Standard: `false`
- Accepterar inte ett värde

### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)

- Standard: `c`
- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `project:list`

Hämta en lista över alla aktiva projekt

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```


```bash
projects
```


```bash
pro
```

### `--pipe`

Skriv ut en enkel lista med projekt-ID:n. Inaktiverar sidnumrering.

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

### `--page`

Sidnummer. Detta aktiverar sidnumrering, trots konfiguration eller —count. Ignoreras om —pipe har angetts.

- Kräver ett värde

### `--count`, `-c`

Antalet projekt som ska visas per sida. Använd 0 för att inaktivera sidnumrering. Ignoreras om —page har angetts.

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`

Kolumner att visa. Tillgängliga kolumner: id*, title*, region*, created_at, endpoint, organization_id, organization_label, organization_name, region_label, status, ui_url (* = standardkolumner). Tecknet&quot;+&quot; kan användas som platshållare för standardkolumnerna. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `project:set-remote`

Ange fjärrprojektet för den aktuella Git-databasen

```bash
magento-cloud project:set-remote [<project>]
```


### `project`

Projekt-ID


### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Ta bort en variabel från ett projekt

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Variabelnamnet

- Obligatoriskt

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Visa variabler för ett projekt

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<name>]
```


```bash
project-variables
```


```bash
pvget
```


```bash
project:variable:list
```


### `name`

Variabelns namn


### `--pipe`

Utdata för endast det fullständiga variabelvärdet (ett &quot;name&quot; måste anges)

- Standard: `false`
- Accepterar inte ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Ange en variabel för ett projekt

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
pvset
```


### `name`

Variabelnamnet

- Obligatoriskt

### `value`

Variabelvärdet

- Obligatoriskt

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `repo:cat`

Läsa en fil i projektdatabasen

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] <path>
```


### `path`

Sökvägen till filen

- Obligatoriskt

### `--commit`, `-c`

Verkställ SHA. Detta kan även acceptera suffixen &quot;HEAD&quot; och cirkumflex (^) eller tilde (~) för överordnade implementeringar.

- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `repo:ls`

Visa filer i projektdatabasen

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

Sökvägen till en underkatalog


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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `repo:read`

Läsa en katalog eller fil i projektdatabasen

```bash
magento-cloud read [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


```bash
read
```


### `path`

Sökvägen till katalogen eller filen


### `--commit`, `-c`

Verkställ SHA. Detta kan även acceptera suffixen &quot;HEAD&quot; och cirkumflex (^) eller tilde (~) för överordnade implementeringar.

- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `route:get`

Visa detaljerad information om ett flöde

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```


### `route`

Vägets ursprungliga URL


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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `route:list`

Visa alla vägar för en miljö

```bash
magento-cloud routes [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<environment>]
```


```bash
routes
```


```bash
environment:routes
```


### `environment`

Miljö-ID


### `--refresh`

Kringgå cacheminnet för vägar

- Standard: `false`
- Accepterar inte ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: route*, type*, to*, url (* = standardkolumner). Tecknet&quot;+&quot; kan användas som platshållare för standardkolumnerna. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `self:install`

Installera eller uppdatera CLI-konfigurationsfiler

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```


```bash
local:install
```

### `--shell-type`

Gränssnittstypen för automatisk komplettering (bash eller zsh)

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `self:stats`

Visa statistik för hämtningar av GitHub-paket

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

### `--page`, `-p`

Sidnummer

- Standard: `1`
- Kräver ett värde

### `--count`, `-c`

Resultat per sida (max: 100)

- Standard: `20`
- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`

Kolumner att visa. Tillgängliga kolumner: resurs, datum, nedladdningar, release. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `self:update`

Uppdatera CLI till den senaste versionen

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```


```bash
self-update
```


```bash
update
```

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `service:list`

Visa tjänster i projektet

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
services
```

### `--refresh`

Om cachen ska uppdateras

- Standard: `false`
- Accepterar inte ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: disk, namn, storlek, typ. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `service:mongo:dump`

Skapa en binär arkivdump av data från MongoDB

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongodump
```

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `service:mongo:export`

Exportera data från MongoDB

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongoexport
```

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `service:mongo:restore`

Återställa en binär arkivdump av data till MongoDB

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongorestore
```

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `service:mongo:shell`

Använd MongoDB-skalet

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongo
```

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `service:redis-cli`

Åtkomst till Redis CLI

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```


```bash
redis
```


### `args`

Argument som ska läggas till i Redis-kommandot


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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Växla mellan sessioner

```bash
magento-cloud session:switch [<id>]
```


### `id`

Nytt sessions-ID


### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `snapshot:create`

Ta en ögonblicksbild av en miljö

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


```bash
backup
```


```bash
backup:create
```


```bash
environment:backup
```


### `environment`

Miljön


### `--live`

Live-säkerhetskopiering: stoppa inte miljön. Om detta anges kommer miljön att vara igång och öppen för anslutningar under säkerhetskopieringen. Detta minskar driftstoppen och riskerar att data säkerhetskopieras i ett inkonsekvent tillstånd.

- Standard: `false`
- Accepterar inte ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--unsafe`

Föråldrat alternativ: use —live i stället

- Standard: `false`
- Accepterar inte ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `snapshot:list`

Visa tillgängliga ögonblicksbilder av en miljö

```bash
magento-cloud snapshots [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
snapshots
```


```bash
backups
```


```bash
backup:list
```

### `--limit`

[Föråldrat] - det här alternativet används inte

- Kräver ett värde

### `--start`

[Föråldrat] - det här alternativet används inte

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `snapshot:restore`

Återställ en ögonblicksbild av miljön

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```


```bash
environment:restore
```


```bash
backup:restore
```


### `snapshot`

Namnet på ögonblicksbilden. Standardvärdet är den senaste


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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Kör en källåtgärd

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```


### `operation`

Åtgärdsnamnet

- Obligatoriskt

### `--variable`

En variabel som ska anges under åtgärden, i formatet &lt;info>type:name=value&lt;/info>

- Standard: `[]`
- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `ssh-cert:info`

Visa information om det aktuella SSH-certifikatet

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `ssh-cert:load`

Generera ett SSH-certifikat

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `ssh-key:add`

Lägg till en ny SSH-nyckel

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```


### `path`

Sökvägen till en befintlig offentlig SSH-nyckel


### `--name`

Ett namn som identifierar nyckeln

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `ssh-key:delete`

Ta bort en SSH-nyckel

```bash
magento-cloud ssh-key:delete [<id>]
```


### `id`

ID för SSH-nyckeln som ska tas bort


### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `ssh-key:list`

Hämta en lista med SSH-nycklar i ditt konto

```bash
magento-cloud ssh-keys [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
ssh-keys
```

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: id*, title*, path*, fingeravtryck (* = standardkolumner). Tecknet&quot;+&quot; kan användas som platshållare för standardkolumnerna. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `subscription:info`

Läs eller ändra prenumerationsegenskaper

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<property>] [<value>]
```


### `property`

Egenskapens namn


### `value`

Ange ett nytt värde för egenskapen


### `--id`, `-s`

Prenumerations-ID

- Kräver ett värde

### `--date-fmt`

Datumformatet (som en PHP-datumformatsträng)

- Standard: `c`
- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `tunnel:close`

Stäng SSH-tunnlar

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

### `--all`, `-a`

Stäng alla tunnlar

- Standard: `false`
- Accepterar inte ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `tunnel:info`

Visa relationsinformation för SSH-tunnlar

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--app`, `-A`

Namnet på fjärrprogrammet

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `tunnel:list`

Lista SSH-tunnlar

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
tunnels
```

### `--all`, `-a`

Visa alla tunnlar

- Standard: `false`
- Accepterar inte ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--app`, `-A`

Namnet på fjärrprogrammet

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `tunnel:open`

Öppna SSH-tunnlar i en apps relationer

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

### `--gateway-ports`, `-g`

Tillåt att fjärrvärdar ansluter till lokala vidarebefordrade portar

- Standard: `false`
- Accepterar inte ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `tunnel:single`

Öppna en SSH-tunnel till en apprelation

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `user:add`

Lägg till en användare i projektet

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

Användarens e-postadress


### `--role`, `-r`

Användarens projektroll (admin eller viewer) eller miljötypsroll (t.ex. &#39;staging:contributor&#39; or &#39;production:viewer&#39;). Om du vill ta bort en användare från en miljötyp anger du rollen som none. Tecknet % kan användas som jokertecken för miljötypen, t.ex. %:viewer för att ge användaren rollen &#39;viewer&#39; för alla typer. Rollen kan förkortas, t.ex. &#39;production:v&#39;.

- Standard: `[]`
- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `user:delete`

Ta bort en användare från projektet

```bash
magento-cloud user:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <email>
```


### `email`

Användarens e-postadress

- Obligatoriskt

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `user:get`

Visa en användares roll

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```


```bash
user:role
```


### `email`

Användarens e-postadress


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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `user:list`

Visa projektanvändare

```bash
magento-cloud users [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
users
```

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: e-post, id, namn, roll. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `user:update`

Uppdatera användarroller i ett projekt

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

Användarens e-postadress


### `--role`, `-r`

Användarens projektroll (admin eller viewer) eller miljötypsroll (t.ex. &#39;staging:contributor&#39; or &#39;production:viewer&#39;). Om du vill ta bort en användare från en miljötyp anger du rollen som none. Tecknet % kan användas som jokertecken för miljötypen, t.ex. %:viewer för att ge användaren rollen &#39;viewer&#39; för alla typer. Rollen kan förkortas, t.ex. &#39;production:v&#39;.

- Standard: `[]`
- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `variable:create`

Skapa en variabel

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```


### `name`

Variabelnamnet


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

- Kräver ett värde

### `--visible-runtime`

Om variabeln ska vara synlig vid körning

- Standard: `true`
- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `variable:delete`

Ta bort en variabel

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Variabelnamnet

- Obligatoriskt

### `--level`, `-l`

Variabelnivån (&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; eller &#39;e&#39;)

- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Inaktivera en aktiverad miljönivåvariabel

```bash
magento-cloud variable:disable [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Variabelns namn

- Obligatoriskt

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Aktivera en inaktiverad miljönivåvariabel

```bash
magento-cloud variable:enable [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Variabelns namn

- Obligatoriskt

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `variable:get`

Visa en variabel

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```


```bash
vget
```


### `name`

Variabelns namn


### `--property`, `-P`

Visa en enskild variabelegenskap

- Kräver ett värde

### `--level`, `-l`

Variabelnivån (&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; eller &#39;e&#39;)

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `variable:list`

Listvariabler

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
variables
```


```bash
var
```

### `--level`, `-l`

Variabelnivån (&#39;project&#39;, &#39;environment&#39;, &#39;p&#39; eller &#39;e&#39;)

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: is_enabled, level, name, value. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--help`, `-h`

Visa det här hjälpmeddelandet

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

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ INAKTUELL ]&lt;/> Ange en variabel för en miljö

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
vset
```


### `name`

Variabelnamnet

- Obligatoriskt

### `value`

Variabelvärdet

- Obligatoriskt

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

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `variable:update`

Uppdatera en variabel

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Variabelnamnet

- Obligatoriskt

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

- Kräver ett värde

### `--visible-runtime`

Om variabeln ska vara synlig vid körning

- Standard: `true`
- Kräver ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `version:list`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALFA ]&lt;/> Listmiljöversioner

```bash
magento-cloud versions [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
versions
```

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde


## `worker:list`

Hämta en lista över alla distribuerade arbetare

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
workers
```

### `--refresh`

Om cachen ska uppdateras

- Standard: `false`
- Accepterar inte ett värde

### `--project`, `-p`

Projekt-ID eller URL

- Kräver ett värde

### `--host`

Inaktuellt alternativ, används inte längre

- Kräver ett värde

### `--environment`, `-e`

Miljö-ID

- Kräver ett värde

### `--format`

Utdataformatet: table, csv, tsv eller plain

- Standard: `table`
- Kräver ett värde

### `--columns`, `-c`

Kolumner att visa. Tillgängliga kolumner: kommandon, namn, typ. Om en lista anges som ett enda värde (t.ex. &quot;a,b,c&quot;) delas den med kommatecken och/eller blanksteg.

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

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas exakthet

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--yes`, `-y`

svara ja på bekräftelsefrågor, godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`

Ställ inga interaktiva frågor. acceptera standardvärden. Motsvarar användning av miljövariabeln: &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Framtvinga ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no-ansi`

Inaktivera ANSI-utdata

- Standard: `false`
- Accepterar inte ett värde

### `--no`, `-n`

Svara&quot;nej&quot; på bekräftelsefrågor. godkänna standardvärdet för andra frågor, inaktivera interaktion

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde
