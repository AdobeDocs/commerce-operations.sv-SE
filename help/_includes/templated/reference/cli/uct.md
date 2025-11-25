---
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->
**Version**: 3.0.25

Referensen innehåller nio kommandon som är tillgängliga via kommandoradsverktyget `bin/uct`.
Den inledande listan genereras automatiskt med kommandot `bin/uct list` på Adobe Commerce.

## Allmänt

Läs mer om verktyget i [Översikt](/help/upgrade/upgrade-compatibility-tool/overview.md).

>[!NOTE]
>
>Kommandot `composer update` fungerar inte för att uppgradera det här verktyget. Du måste [hämta och installera den senaste versionen](/help/upgrade/upgrade-compatibility-tool/run.md).

Den här referensdokumentationen genereras från programmets källkod. Om du vill ändra dokumentationen bör du öppna en pull-begäran för motsvarande kommando i den relevanta [koddatabasen](https://github.com/magento). Mer information finns i [Kodbidrag](https://developer.adobe.com/commerce/contributor/guides/code-contributions).

### Globala alternativ

#### `--help`, `-h`

Visa hjälp för det angivna kommandot. När inget kommando anges visas hjälpen för listkommandot

- Standard: `false`
- Accepterar inte ett värde

#### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde

#### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas utförlighet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning

- Standard: `false`
- Accepterar inte ett värde

#### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

#### `--ansi`

Tvinga (eller inaktivera) ANSI-utdata

- Accepterar inte ett värde

#### `--no-ansi`

Ignorera alternativet &quot;—ansi&quot;

- Standard: `false`
- Accepterar inte ett värde

#### `--no-interaction`, `-n`

Ställ inga interaktiva frågor

- Standard: `false`
- Accepterar inte ett värde


## `_complete`

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Internt kommando för att ge förslag på komplettering av skalet

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--shell`, `-s`

Skaltypen (&quot;bash&quot;, &quot;fish&quot;, &quot;zsh&quot;)

- Kräver ett värde

#### `--input`, `-i`

En array med indatatoken (t.ex. COMP_WORDS eller argv)

- Standard: `[]`
- Kräver ett värde

#### `--current`, `-c`

Indexvärdet för den inmatningsarray där markören finns (t.ex. COMP_CWORD)

- Kräver ett värde

#### `--api-version`, `-a`

API-versionen av det slutförda skriptet

- Kräver ett värde

#### `--symfony`, `-S`

inaktuell

- Kräver ett värde


## `completion`

```bash
bin/uct completion [--debug] [--] [<shell>]
```

Dumpa skriptet för gränssnittets slutförande

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    uct/bin/uct completion  | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    uct/bin/uct completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/jenkins/workspace/gendocs-uct-cli/uct/bin/uct completion )"
```

### Argument

#### `shell`

Gränssnittstypen (t.ex. &quot;bash&quot;), värdet för &quot;$SHELL&quot; env var, används om detta inte anges

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--debug`

Avsluta felsökningsloggen

- Standard: `false`
- Accepterar inte ett värde


## `help`

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```

Visa hjälp för ett kommando

```
The help command displays help for a given command:

  uct/bin/uct help list

You can also output the help in other formats by using the --format option:

  uct/bin/uct help --format=xml list

To display the list of available commands, please use the list command.
```

### Argument

#### `command_name`

Kommandonamnet

- Standard: `help`

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--format`

Utdataformatet (txt, xml, json eller md)

- Standard: `txt`
- Kräver ett värde

#### `--raw`

Hjälp för att skriva ut råformat

- Standard: `false`
- Accepterar inte ett värde


## `list`

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Listkommandon

```
The list command lists all commands:

  uct/bin/uct list

You can also display the commands for a specific namespace:

  uct/bin/uct list test

You can also output the information in other formats by using the --format option:

  uct/bin/uct list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  uct/bin/uct list --raw
```

### Argument

#### `namespace`

Namnutrymmets namn

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--raw`

Utdata för kommandolista

- Standard: `false`
- Accepterar inte ett värde

#### `--format`

Utdataformatet (txt, xml, json eller md)

- Standard: `txt`
- Kräver ett värde

#### `--short`

Så här beskriver du inte kommandots argument

- Standard: `false`
- Accepterar inte ett värde


## `refactor`

```bash
bin/uct refactor <path>
```

Åtgärdar problem som kan korrigeras automatiskt. Koden i sökvägen uppdateras.

### Argument

#### `path`

Sökväg för att lösa problem i.

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `core:code:changes`

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

Kompatibilitetsverktyget för uppgradering är ett kommandoradsverktyg som kontrollerar en Adobe Commerce-instans mot en viss version genom att analysera alla andra moduler än Adobe Commerce som är installerade i den. Returnerar en lista med fel och varningar som du måste åtgärda innan du uppgraderar till en ny version av Adobe Commerce-koden.

### Argument

#### `dir`

Adobe Commerce installationskatalog.

- Obligatoriskt


#### `vanilla-dir`

Installationskatalogen för Adobe Commerce vanilla.

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--output`, `-o`

Sökväg till filen som ska exporteras (Json-format)

- Accepterar ett värde


## `dbschema:diff`

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Tillåt att lista skillnader i Adobe Commerce DB-scheman mellan två valda versioner. Tillgängliga versioner: 2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4-p1 | 2.3.4-p2 | 2.3.5 | 2.3.5-p1 | 2.3.5-p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0 | 2.4.0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4-p2 | 2.4.5-p1 | 2.4.4-p3 | 2.4.4-p4 | 2.4.4-p5 | 2.4.5-p2 | 2.4.5-p3 | 2.4.5-p4 | 2.4.6 | 2.4.6-p1 | 2.4.6-p2 | 2.4.7-beta1 | 2.4.4-p6 | 2.4.5-p5 | 2.4.6-p3 | 2.4.7-beta2 | 2.4.4-p7 | 2.4.5-p6 | 2.4.6-p4 | 2.4.7-beta3 | 2.4.7 | 2.4.6-p5 | 2.4.5-p7 | 2.4.4-p8 | 2.4.4-p9 | 2.4.5-p8 | 2.4.6-p6 | 2.4.7-p1 | 2.4.4-p10 | 2.4.5-p9 | 2.4.6-p7 | 2.4.7-p2 | 2.4.4-p11 | 2.4.5-p10 | 2.4.6-p8 | 2.4.7-p3 | 2.4.8-beta1 | 2.4.4-p12 | 2.4.5-p11 | 2.4.6-p9 | 2.4.7-p4 | 2.4.8-beta2 | 2.4.4-p13 | 2.4.5-p12 | 2.4.6-p10 | 2.4.7-p5 | 2.4.8 | 2.4.9-alfa2 | 2.4.8-p2 | 2.4.7-p7 | 2.4.6-p12 | 2.4.5-p14 | 2.4.4-p15 | 2.4.9-alpha1 | 2.4.8-p1 | 2.4.7-p6 | 2.4.6-p11 | 2.4.5-p13 | 2.4.4-p14 | 2.4.9-alpha3 | 2.4.8-p3 | 2.4.7-p8 | 2.4.6-p13 | 2.4.5-p15 | 2.4.4-p16

### Argument

#### `current-version`

aktuell version (t.ex. 2.3.2).

- Obligatoriskt


#### `target-version`

målversion (t.ex. 2.4.5).

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `graphql:compare`

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

Verifiering av schemakompatibilitet med GraphQL

### Argument

#### `schema1`

Slutpunkts-URL som pekar på det första GraphQL-schemat.

- Obligatoriskt


#### `schema2`

Slutpunkts-URL som pekar på det andra GraphQL-schemat.

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--output`, `-o`

Sökväg till filen som ska exporteras (JSON-format)

- Accepterar ett värde


## `upgrade:check`

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

Kompatibilitetsverktyget för uppgradering är ett kommandoradsverktyg som kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla moduler som är installerade i den. Returnerar en lista med fel och varningar som måste åtgärdas innan du uppgraderar till den senaste versionen av Adobe Commerce.

### Argument

#### `dir`

Adobe Commerce installationskatalog.

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--current-version`, `-a`

Aktuell Adobe Commerce-version, version av Adobe Commerce-installationen, används om den utelämnas.

- Accepterar ett värde

#### `--coming-version`, `-c`

Målversion för Adobe Commerce. Den senaste stabila versionen av Adobe Commerce kommer att användas om den utelämnas. Tillgängliga Adobe Commerce-versioner: 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.4-p2 \| 2.4.4-p3 \| 2.4.4-p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-p7 \| 2.4.4-p8 \| 2.4.4-p9 \| 2.4.4-p10 \| 2.4.4-p11 \| 2.4.4-p12 \| 2.4.4-p13 \| 2.4.4-p14 \| 2.4.4-p15 \| 2.4.4-p16 \| 2.4.5 \| 2.4.5-p1 \| 2.4.5-p2 \| 2.4.5-p3 \| 2.4.5-p4 \| 2.4.5-p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.5-p8 \| 2.4.5-p9 \| 2.4.5-p10 \| 2.4.5-p11 \| 2.4.5-p12 \| 2.4.5-p13 \| 2.4.5-p14 \| 2.4.5-p15 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p2 \| 2.4.6-p3 \| 2.4.6-p4 \| 2.4.6-p5 \| 2.4.6-p6 \| 2.4.6-p7 \| 2.4.6-p8 \| 2.4.6-p9 \| 2.4.6-p10 \| 2.4.6-p11 \| 2.4.6-p12 \| 2.4.6-p13 \| 2.4.7-beta1 \| 2.4.7-beta2 \| 2.4.7-beta3 \| 2.4.7 \| 2.4.7-p1 \| 2.4.7-p2 \| 2.4.7-p3 \| 2.4.7-p4 \| 2.4.7-p5 \| 2.4.7-p6 \| 2.4.7-p7 \| 2.4.7-p8 \| 2.4.8-beta1 \| 2.4.8-beta2 \| 2.4.8 \| 2.4.8-p1 \| 2.4.8-p2 \| 2.4.8-p3 \| 2.4.9-alpha1 \| 2.4.9-alpha2 \| 2.4.9-alpha3

- Accepterar ett värde

#### `--json-output-path`

Sökväg till filen där utdata ska exporteras i JSON-format

- Accepterar ett värde

#### `--html-output-path`

Sökväg till filen där utdata ska exporteras i HTML-format

- Accepterar ett värde

#### `--min-issue-level`

Minimal problemnivå som du vill se i rapporten (varning, fel eller kritisk).

- Standard: `warning`
- Accepterar ett värde

#### `--ignore-current-version-compatibility-issues`, `-i`

Ignorera vanliga problem för aktuell och kommande version

- Standard: `false`
- Accepterar inte ett värde

#### `--context`

Körningskontext. Det här alternativet är avsett för integrering och påverkar inte körningsresultatet.

- Kräver ett värde

