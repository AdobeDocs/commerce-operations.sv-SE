---
source-git-commit: 19d19ef385cf4aaee3a255930af8e6d3b81de23a
workflow-type: tm+mt
source-wordcount: '1638'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Version**: 3.0.16

Den här referensen innehåller 9 kommandon som är tillgängliga via `bin/uct` kommandoradsverktyg.
Den inledande listan genereras automatiskt med `bin/uct list` på Adobe Commerce.

Läs mer om verktyget i [Ökning](/help/upgrade/upgrade-compatibility-tool/overview.md).

>[!NOTE]
>
>Den här referensen genereras från programmets kodbas. Om du vill ändra innehållet kan du uppdatera källkoden för motsvarande kommandoimplementering i [kodbas](https://github.com/magento) arkivera och skicka in dina ändringar för granskning. Ett annat sätt är att _Ge oss feedback_ (hitta länken i det övre högra hörnet). Information om riktlinjer för bidrag finns i [Kodavgifter](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

Internt kommando för att ge förslag på komplettering av skalet


### `--shell`, `-s`

Gränssnittstypen (&quot;bash&quot;)

- Kräver ett värde

### `--input`, `-i`

En array med indatatoken (t.ex. COMP_WORDS eller argv)

- Standard: `[]`
- Kräver ett värde

### `--current`, `-c`

Indexvärdet för den inmatningsarray där markören finns (t.ex. COMP_CWORD)

- Kräver ett värde

### `--symfony`, `-S`

Versionen av det slutförda skriptet

- Kräver ett värde

### `--help`, `-h`

Visa hjälp för det angivna kommandot. När inget kommando anges visas hjälpen för listkommandot

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas utförlighet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Tvinga (eller inaktivera) ANSI-utdata

- Accepterar inte ett värde

### `--no-ansi`

Ignorera alternativet &quot;—ansi&quot;

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`, `-n`

Ställ inga interaktiva frågor

- Standard: `false`
- Accepterar inte ett värde


## `completion`

```bash
bin/uct completion [--debug] [--] [<shell>]
```

Dumpa skriptet för gränssnittets slutförande


```
The completion command dumps the shell completion script required
to use shell autocompletion (currently only bash completion is supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    uct/bin/uct completion bash | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    uct/bin/uct completion bash > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/jenkins/workspace/gendocs-uct-cli/uct/bin/uct completion bash)"
```


### `shell`

Gränssnittstypen (t.ex. &quot;bash&quot;), värdet för &quot;$SHELL&quot; env var, används om detta inte anges


### `--debug`

Avsluta felsökningsloggen

- Standard: `false`
- Accepterar inte ett värde

### `--help`, `-h`

Visa hjälp för det angivna kommandot. När inget kommando anges visas hjälpen för listkommandot

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas utförlighet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Tvinga (eller inaktivera) ANSI-utdata

- Accepterar inte ett värde

### `--no-ansi`

Ignorera alternativet &quot;—ansi&quot;

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`, `-n`

Ställ inga interaktiva frågor

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

Visa hjälp för det angivna kommandot. När inget kommando anges visas hjälpen för listkommandot

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas utförlighet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Tvinga (eller inaktivera) ANSI-utdata

- Accepterar inte ett värde

### `--no-ansi`

Ignorera alternativet &quot;—ansi&quot;

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`, `-n`

Ställ inga interaktiva frågor

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

### `--short`

Så här beskriver du inte kommandots argument

- Standard: `false`
- Accepterar inte ett värde

### `--help`, `-h`

Visa hjälp för det angivna kommandot. När inget kommando anges visas hjälpen för listkommandot

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas utförlighet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Tvinga (eller inaktivera) ANSI-utdata

- Accepterar inte ett värde

### `--no-ansi`

Ignorera alternativet &quot;—ansi&quot;

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`, `-n`

Ställ inga interaktiva frågor

- Standard: `false`
- Accepterar inte ett värde


## `refactor`

```bash
bin/uct refactor <path>
```

Åtgärdar problem som kan korrigeras automatiskt. Koden i sökvägen uppdateras.



### `path`

Sökväg för att lösa problem i.

- Obligatoriskt

### `--help`, `-h`

Visa hjälp för det angivna kommandot. När inget kommando anges visas hjälpen för listkommandot

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas utförlighet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Tvinga (eller inaktivera) ANSI-utdata

- Accepterar inte ett värde

### `--no-ansi`

Ignorera alternativet &quot;—ansi&quot;

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`, `-n`

Ställ inga interaktiva frågor

- Standard: `false`
- Accepterar inte ett värde


## `core:code:changes`

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

Kompatibilitetsverktyget för uppgradering är ett kommandoradsverktyg som kontrollerar en Adobe Commerce-instans mot en viss version genom att analysera alla andra moduler än Adobe Commerce som är installerade i den. Returnerar en lista med fel och varningar som du måste åtgärda innan du uppgraderar till en ny version av Adobe Commerce-koden.



### `dir`

Adobe Commerce installationskatalog.

- Obligatoriskt

### `vanilla-dir`

Installationskatalogen för Adobe Commerce vanilla.


### `--output`, `-o`

Sökväg till filen som ska exporteras (Json-format)

- Accepterar ett värde

### `--help`, `-h`

Visa hjälp för det angivna kommandot. När inget kommando anges visas hjälpen för listkommandot

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas utförlighet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Tvinga (eller inaktivera) ANSI-utdata

- Accepterar inte ett värde

### `--no-ansi`

Ignorera alternativet &quot;—ansi&quot;

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`, `-n`

Ställ inga interaktiva frågor

- Standard: `false`
- Accepterar inte ett värde


## `dbschema:diff`

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Tillåt att lista skillnader i Adobe Commerce DB-scheman mellan två valda versioner. Tillgängliga versioner: 2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4-p1 | 2.3.4-p2 | 2.3.5 | 2.3.5-p1 | 2.3.5-p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0 | 2.4.0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4-p2 | 2.4.5-p1 | 2.4.4-p3 | 2.4.4-p4 | 2.4.4-p5 | 2.4.5-p2 | 2.4.5-p3 | 2.4.5-p4 | 2.4.6 | 2.4.6-p1 | 2.4.6-p2 | 2.4.7-beta1 | 2.4.4-p6 | 2.4.5-p5 | 2.4.6-p3 | 2.4.7-beta2 | 2.4.4-p7 | 2.4.5-p6 | 2.4.6-p4 | 2.4.7-beta3 | 2.4.7 | 2.4.6-p5 | 2.4.5-p7 | 2.4.4-p8



### `current-version`

aktuell version (t.ex. 2.3.2).

- Obligatoriskt

### `target-version`

målversion (t.ex. 2.4.5).

- Obligatoriskt

### `--help`, `-h`

Visa hjälp för det angivna kommandot. När inget kommando anges visas hjälpen för listkommandot

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas utförlighet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Tvinga (eller inaktivera) ANSI-utdata

- Accepterar inte ett värde

### `--no-ansi`

Ignorera alternativet &quot;—ansi&quot;

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`, `-n`

Ställ inga interaktiva frågor

- Standard: `false`
- Accepterar inte ett värde


## `graphql:compare`

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

Verifiering av schemakompatibilitet med GraphQL



### `schema1`

Slutpunkts-URL som pekar på det första GraphQL-schemat.

- Obligatoriskt

### `schema2`

Slutpunkts-URL som pekar på det andra GraphQL-schemat.

- Obligatoriskt

### `--output`, `-o`

Sökväg till filen som ska exporteras (JSON-format)

- Accepterar ett värde

### `--help`, `-h`

Visa hjälp för det angivna kommandot. När inget kommando anges visas hjälpen för listkommandot

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas utförlighet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Tvinga (eller inaktivera) ANSI-utdata

- Accepterar inte ett värde

### `--no-ansi`

Ignorera alternativet &quot;—ansi&quot;

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`, `-n`

Ställ inga interaktiva frågor

- Standard: `false`
- Accepterar inte ett värde


## `upgrade:check`

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

Kompatibilitetsverktyget för uppgradering är ett kommandoradsverktyg som kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla moduler som är installerade i den. Returnerar en lista med fel och varningar som måste åtgärdas innan du uppgraderar till den senaste versionen av Adobe Commerce.



### `dir`

Adobe Commerce installationskatalog.

- Obligatoriskt

### `--current-version`, `-a`

Aktuell Adobe Commerce-version, version av Adobe Commerce-installationen, används om den utelämnas.

- Accepterar ett värde

### `--coming-version`, `-c`

Målversion för Adobe Commerce. Den senaste stabila versionen av Adobe Commerce kommer att användas om den utelämnas. Tillgängliga Adobe Commerce-versioner: 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.4-p2 \| 2.4.4-p3 \| 2.4.4-p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-p7 \| 2.4.4-p8 \| 2.4.5 \| 2.4.5-p1 \| 2.4.5-p2 \| 2.4.5-p3 \| 2.4.5-p4 \| 2.4.5-p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p2 \| 2.4.6-p3 \| 2.4.6-p4 \| 2.4.6-p5 \| 2.4.7-beta1 \| 2.4.7-beta2 \| 2.4.7-beta3 \| 2.4.7

- Accepterar ett värde

### `--json-output-path`

Sökväg till filen där utdata ska exporteras i JSON-format

- Accepterar ett värde

### `--html-output-path`

Sökväg till filen där utdata ska exporteras i HTML-format

- Accepterar ett värde

### `--min-issue-level`

Minimal problemnivå som du vill se i rapporten (varning, fel eller kritisk).

- Standard: `warning`
- Accepterar ett värde

### `--ignore-current-version-compatibility-issues`, `-i`

Ignorera vanliga problem för aktuell och kommande version

- Standard: `false`
- Accepterar inte ett värde

### `--context`

Körningskontext. Det här alternativet är avsett för integrering och påverkar inte körningsresultatet.

- Kräver ett värde

### `--help`, `-h`

Visa hjälp för det angivna kommandot. När inget kommando anges visas hjälpen för listkommandot

- Standard: `false`
- Accepterar inte ett värde

### `--quiet`, `-q`

Skriv inget meddelande

- Standard: `false`
- Accepterar inte ett värde

### `--verbose`, `-v|-vv|-vvv`

Öka meddelandenas utförlighet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning

- Standard: `false`
- Accepterar inte ett värde

### `--version`, `-V`

Visa den här programversionen

- Standard: `false`
- Accepterar inte ett värde

### `--ansi`

Tvinga (eller inaktivera) ANSI-utdata

- Accepterar inte ett värde

### `--no-ansi`

Ignorera alternativet &quot;—ansi&quot;

- Standard: `false`
- Accepterar inte ett värde

### `--no-interaction`, `-n`

Ställ inga interaktiva frågor

- Standard: `false`
- Accepterar inte ett värde

