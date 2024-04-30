---
source-git-commit: 19d19ef385cf4aaee3a255930af8e6d3b81de23a
workflow-type: tm+mt
source-wordcount: '21169'
ht-degree: 0%

---
# bin/magento (Adobe Commerce lokal)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->

**Version**: 2.4.7

Referensen innehåller 141 kommandon som är tillgängliga via `bin/magento` kommandoradsverktyg.
Den inledande listan genereras automatiskt med `bin/magento list` på Adobe Commerce.
Använd [&quot;Lägg till CLI-kommandon&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) för att lägga till ett eget CLI-kommando.

>[!NOTE]
>
>Du kan ringa `bin/magento` CLI-kommandon som använder genvägar i stället för det fullständiga kommandonamnet. Du kan till exempel ringa `bin/magento setup:upgrade` använda `bin/magento s:up`, `bin/magento s:upg`. Se [genvägssyntax](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) för att förstå hur du använder kortkommandon med valfritt CLI-kommando.

>[!NOTE]
>
>Den här referensen genereras från programmets kodbas. Om du vill ändra innehållet kan du uppdatera källkoden för motsvarande kommandoimplementering i [kodbas](https://github.com/magento) arkivera och skicka in dina ändringar för granskning. Ett annat sätt är att _Ge oss feedback_ (hitta länken i det övre högra hörnet). Information om riktlinjer för bidrag finns i [Kodavgifter](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Internt kommando för att ge förslag på komplettering av skalet


### `--shell`, `-s`

Skaltypen (&quot;bash&quot;, &quot;fish&quot;, &quot;zsh&quot;)

- Kräver ett värde

### `--input`, `-i`

En array med indatatoken (t.ex. COMP_WORDS eller argv)

- Standard: `[]`
- Kräver ett värde

### `--current`, `-c`

Indexvärdet för den inmatningsarray där markören finns (t.ex. COMP_CWORD)

- Kräver ett värde

### `--api-version`, `-a`

API-versionen av det slutförda skriptet

- Kräver ett värde

### `--symfony`, `-S`

inaktuell

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
bin/magento completion [--debug] [--] [<shell>]
```

Dumpa skriptet för gränssnittets slutförande


```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    bin/magento completion  | sudo tee /etc/bash_completion.d/magento

Or dump the script to a local file and source it:

    bin/magento completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/www/html/magento2/bin/magento completion )"
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
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```

Visa hjälp för ett kommando


```
The help command displays help for a given command:

  bin/magento help list

You can also output the help in other formats by using the --format option:

  bin/magento help --format=xml list

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
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Listkommandon


```
The list command lists all commands:

  bin/magento list

You can also display the commands for a specific namespace:

  bin/magento list test

You can also output the information in other formats by using the --format option:

  bin/magento list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  bin/magento list --raw
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


## `admin:adobe-ims:disable`

```bash
bin/magento admin:adobe-ims:disable
```

Inaktivera Adobe IMS-modul


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


## `admin:adobe-ims:enable`

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

Aktivera Adobe IMS-modulen.


### `--organization-id`, `-o`

Ange organisations-ID för Adobe IMS-konfigurationen. Krävs när modulen aktiveras

- Accepterar ett värde

### `--client-id`, `-c`

Ange klient-ID för Adobe IMS-konfigurationen. Krävs när modulen aktiveras

- Accepterar ett värde

### `--client-secret`, `-s`

Ange klienthemlighet för Adobe IMS-konfigurationen. Krävs när modulen aktiveras

- Accepterar ett värde

### `--2fa`, `-t`

Kontrollera om 2FA är aktiverat för Organisation i Adobe Admin Console. Krävs när modulen aktiveras

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


## `admin:adobe-ims:info`

```bash
bin/magento admin:adobe-ims:info
```

Information om Adobe IMS-modulkonfiguration


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


## `admin:adobe-ims:status`

```bash
bin/magento admin:adobe-ims:status
```

Status för Adobe IMS-modul


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


## `admin:user:create`

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Skapar en administratör


### `--admin-user`

(Obligatoriskt) Administratörsanvändare

- Kräver ett värde

### `--admin-password`

(Obligatoriskt) Administratörslösenord

- Kräver ett värde

### `--admin-email`

(Obligatoriskt) Administratörens e-postadress

- Kräver ett värde

### `--admin-firstname`

(Obligatoriskt) Förnamn för administratör

- Kräver ett värde

### `--admin-lastname`

(Obligatoriskt) Administratörens efternamn

- Kräver ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `admin:user:unlock`

```bash
bin/magento admin:user:unlock <username>
```

Lås upp administratörskonto


```
This command unlocks an admin account by its username.
To unlock:
      bin/magento admin:user:unlock username
```


### `username`

Administratörens användarnamn som ska låsas upp

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


## `app:config:dump`

```bash
bin/magento app:config:dump [<config-types>...]
```

Skapa programdump



### `config-types`

Blankstegsavgränsad lista med konfigurationstyper eller utelämna att dumpa alla [scope, system, teman, i18n]

- Standard: `[]`

- Array

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


## `app:config:import`

```bash
bin/magento app:config:import
```

Importera data från delade konfigurationsfiler till lämplig datalagring


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


## `app:config:status`

```bash
bin/magento app:config:status
```

Kontrollerar om konfigurationsspridning kräver uppdatering


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


## `braintree:migrate`

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

Migrera lagrade kort från en Magento 1-databas


### `--host`

Värdnamn/IP. Porten är valfri

- Kräver ett värde

### `--dbname`

Databasnamn

- Kräver ett värde

### `--username`

Användarnamn för databas. Måste ha läsåtkomst

- Kräver ett värde

### `--password`

Lösenord

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


## `cache:clean`

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Rensar cachetyper



### `types`

Blankstegsavgränsad lista med cachetyper eller utelämna att använda för alla cachetyper.

- Standard: `[]`

- Array

### `--bootstrap`

lägga till eller åsidosätta parametrar för bootstrap

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


## `cache:disable`

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Inaktiverar cachetyp(er)



### `types`

Blankstegsavgränsad lista med cachetyper eller utelämna att använda för alla cachetyper.

- Standard: `[]`

- Array

### `--bootstrap`

lägga till eller åsidosätta parametrar för bootstrap

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


## `cache:enable`

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Aktiverar cachetyp(er)



### `types`

Blankstegsavgränsad lista med cachetyper eller utelämna att använda för alla cachetyper.

- Standard: `[]`

- Array

### `--bootstrap`

lägga till eller åsidosätta parametrar för bootstrap

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


## `cache:flush`

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Tömmer cache-lagring som används av cachetyper



### `types`

Blankstegsavgränsad lista med cachetyper eller utelämna att använda för alla cachetyper.

- Standard: `[]`

- Array

### `--bootstrap`

lägga till eller åsidosätta parametrar för bootstrap

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


## `cache:status`

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

Kontrollerar cachestatus


### `--bootstrap`

lägga till eller åsidosätta parametrar för bootstrap

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


## `catalog:images:resize`

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

Skapar storleksändrade produktbilder


### `--async`, `-a`

Ändra storlek på bild i asynkront läge

- Standard: `false`
- Accepterar inte ett värde

### `--skip_hidden_images`

Bearbeta inte bilder som markerats som dolda från produktsidan

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


## `catalog:product:attributes:cleanup`

```bash
bin/magento catalog:product:attributes:cleanup
```

Tar bort oanvända produktattribut.


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


## `cms:wysiwyg:restrict`

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

Ange om innehållsvalidering från HTML ska framtvingas eller om en varning ska visas i stället



### `restrict`

y\n

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


## `config:sensitive:set`

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

Ange känsliga konfigurationsvärden



### `path`

Konfigurationssökväg för exempelvis grupp/avsnitt/fältnamn


### `value`

Konfigurationsvärde


### `--interactive`, `-i`

Aktivera interaktivt läge för att ställa in alla känsliga variabler

- Standard: `false`
- Accepterar inte ett värde

### `--scope`

Omfång för konfiguration, om den inte anges, använd &#39;default&#39;

- Standard: `default`
- Accepterar ett värde

### `--scope-code`

Omfångskod för konfiguration, tom sträng som standard

- Standard: &quot;
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


## `config:set`

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

Ändra systemkonfiguration



### `path`

Konfigurationssökväg i formatavsnitt/grupp/fältnamn

- Obligatoriskt

### `value`

Konfigurationsvärde

- Obligatoriskt

### `--scope`

Konfigurationsomfång (standard, webbplats eller butik)

- Standard: `default`
- Kräver ett värde

### `--scope-code`

Scope-kod (krävs endast om scope inte är &#39;default&#39;)

- Kräver ett värde

### `--lock-env`, `-e`

Lås värde som förhindrar ändringar i Admin (sparas i app/etc/env.php)

- Standard: `false`
- Accepterar inte ett värde

### `--lock-config`, `-c`

Lås och dela värdet med andra installationer, förhindra ändringar i Admin (sparas i app/etc/config.php)

- Standard: `false`
- Accepterar inte ett värde

### `--lock`, `-l`

Inaktuellt använder du alternativet —lock-env i stället.

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


## `config:show`

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

Visar konfigurationsvärde för angiven sökväg. Om ingen sökväg anges visas alla sparade värden



### `path`

Konfigurationssökväg, till exempel section_id/group_id/field_id


### `--scope`

Om inget konfigurationsområde anges används standardomfånget

- Standard: `default`
- Accepterar ett värde

### `--scope-code`

Omfångskod (krävs endast om omfånget inte är det `default`)

- Standard: &quot;
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


## `cron:install`

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

Skapar och installerar crontab för aktuell användare


### `--force`, `-f`

Tvinga installationsaktiviteter

- Standard: `false`
- Accepterar inte ett värde

### `--non-optional`, `-d`

Installera endast icke-valfria (standard) uppgifter

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


## `cron:remove`

```bash
bin/magento cron:remove
```

Tar bort uppgifter från crontab


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


## `cron:run`

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

Kör jobb enligt schema


### `--group`

Kör endast jobb från angiven grupp

- Kräver ett värde

### `--exclude-group`

Uteslut jobb från den angivna gruppen

- Standard: `[]`
- Accepterar flera värden

### `--bootstrap`

Lägga till eller åsidosätta parametrar för bootstrap

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


## `customer:hash:upgrade`

```bash
bin/magento customer:hash:upgrade
```

Uppgradera kundens hash enligt den senaste algoritmen


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


## `deploy:mode:set`

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

Ange programläge.



### `mode`

Det programläge som ska anges. Tillgängliga alternativ är &quot;utvecklare&quot; eller &quot;produktion&quot;

- Obligatoriskt

### `--skip-compilation`, `-s`

Hoppar över rensning och omgenerering av statiskt innehåll (genererad kod, förbearbetad CSS och resurser i pub/static/)

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


## `deploy:mode:show`

```bash
bin/magento deploy:mode:show
```

Visar det aktuella programläget.


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


## `dev:di:info`

```bash
bin/magento dev:di:info <class>
```

Anger information om konfigurationen för beroendeinmatning för kommandot.



### `class`

Klassnamn

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


## `dev:email:newsletter-compatibility-check`

```bash
bin/magento dev:email:newsletter-compatibility-check
```

Skannar nyhetsbrevmallar för potentiella kompatibilitetsproblem med variabel användning


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


## `dev:email:override-compatibility-check`

```bash
bin/magento dev:email:override-compatibility-check
```

Söker igenom e-postmallåsidosättningar för eventuella kompatibilitetsproblem med variabel användning


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


## `dev:profiler:disable`

```bash
bin/magento dev:profiler:disable
```

Inaktivera profileraren.


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


## `dev:profiler:enable`

```bash
bin/magento dev:profiler:enable [<type>]
```

Aktivera profileraren.



### `type`

Profilerartyp


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


## `dev:query-log:disable`

```bash
bin/magento dev:query-log:disable
```

Inaktivera loggning av databasfrågor


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


## `dev:query-log:enable`

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

Aktivera loggning av databasfrågor


### `--include-all-queries`

Logga alla frågor. [true\|false]

- Standard: `true`
- Accepterar ett värde

### `--query-time-threshold`

Frågetidströsklar.

- Standard: `0.001`
- Accepterar ett värde

### `--include-call-stack`

Inkludera anropsstacken. [true\|false]

- Standard: `true`
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


## `dev:source-theme:deploy`

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

Samlar in och publicerar källfiler för temat.



### `file`

Filer som ska förbearbetas (filen ska anges utan filtillägg)

- Standard: `css/styles-mcss/styles-l`

- Array

### `--type`

Typ av källfiler: [mindre]

- Standard: `less`
- Kräver ett värde

### `--locale`

Språk: [sv_SE]

- Standard: `en_US`
- Kräver ett värde

### `--area`

Område: [front\|adminhtml]

- Standard: `frontend`
- Kräver ett värde

### `--theme`

Tema: [Leverantör/tema]

- Standard: `Magento/luma`
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


## `dev:template-hints:disable`

```bash
bin/magento dev:template-hints:disable
```

Inaktivera malltips för frontend. En cachetömning kan behövas.


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


## `dev:template-hints:enable`

```bash
bin/magento dev:template-hints:enable
```

Aktivera malltips för frontend. En cachetömning kan behövas.


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


## `dev:template-hints:status`

```bash
bin/magento dev:template-hints:status
```

Visa status för malltips för förgreningstips.


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


## `dev:tests:run`

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

Kör tester



### `type`

Typ av test som ska köras. Tillgängliga typer: all, unit, integration, integration, all, static, static-all, integrity, legacy, default

- Standard: `default`


### `--arguments`, `-c`

Ytterligare argument för PHPUnit. Exempel: &quot;-c&quot;—filter=MyTest&quot; (inga blanksteg)

- Standard: &quot;
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


## `dev:urn-catalog:generate`

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

Skapar katalogen med URN:er till *.xsd-mappningar så att XML markeras.



### `path`

Sökväg till fil för att mata ut katalogen. För PhpStorm använder du .idea/misc.xml

- Obligatoriskt

### `--ide`

Formatet som katalogen ska skapas i. Stöds: [oväder, vscode]

- Standard: `phpstorm`
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


## `dev:xml:convert`

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

Konverterar XML-fil med XSL-formatmallar



### `xml-file`

Sökväg till XML-fil som ska omvandlas

- Obligatoriskt

### `processor`

Sökväg till XSL-formatmall som ska användas i XML-filen

- Obligatoriskt

### `--overwrite`, `-o`

Skriv över XML-fil

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


## `downloadable:domains:add`

```bash
bin/magento downloadable:domains:add [<domains>...]
```

Lägg till domäner i vitlistan över nedladdningsbara domäner



### `domains`

Domännamn

- Standard: `[]`

- Array

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


## `downloadable:domains:remove`

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

Ta bort domäner från vitlistan över nedladdningsbara domäner



### `domains`

Domännamn

- Standard: `[]`

- Array

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


## `downloadable:domains:show`

```bash
bin/magento downloadable:domains:show
```

Visa lista över nedladdningsbara domäner


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


## `encryption:payment-data:update`

```bash
bin/magento encryption:payment-data:update
```

Återkrypterar krypterade kreditkortsdata med det senaste krypteringschiffret.


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


## `events:create-event-provider`

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]events:provider:create 
```

Skapa en anpassad händelseprovider i Adobe I/O Events för den här instansen. Om du inte anger alternativ för etikett och beskrivning måste de definieras i systemets app/etc/event-types.json.


### `--label`

En etikett som definierar din anpassade leverantör.

- Accepterar ett värde

### `--description`

En beskrivning av din leverantör.

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


## `events:generate:module`

```bash
bin/magento events:generate:module
```

Generera modul baserat på plugin-programlista


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


## `events:info`

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```

Returnerar nyttolasten för den angivna händelsen.



### `event-code`

Händelsekod

- Obligatoriskt

### `--depth`

Antalet nivåer i händelsens nyttolast som ska returneras

- Standard: `2`
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


## `events:list`

```bash
bin/magento events:list
```

Visar en lista över prenumererade händelser


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


## `events:list:all`

```bash
bin/magento events:list:all <module_name>
```

Returnerar en lista med prenumererbara händelser som definieras i den angivna modulen



### `module_name`

Modulnamn

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


## `events:metadata:populate`

```bash
bin/magento events:metadata:populate
```

Skapar metadata i Adobe I/O från konfigurationslistan (XML och programkonfigurationer)


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


## `events:provider:info`

```bash
bin/magento events:provider:info
```

Returnerar information om den konfigurerade händelseprovidern


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


## `events:registrations:list`

```bash
bin/magento events:registrations:list
```

Visar händelseregistreringar i ditt App Builder-projekt


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


## `events:subscribe`

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [-d|--destination DESTINATION] [--] <event-code>
```

Prenumererar på evenemanget



### `event-code`

Händelsekod

- Obligatoriskt

### `--force`, `-f`

Tvingar den angivna händelsen att prenumereras, även om den inte har definierats lokalt.

- Standard: `false`
- Accepterar inte ett värde

### `--fields`

Listan med fält i händelsedatanyttolasten.

- Standard: `[]`
- Kräver ett värde

### `--parent`

Den överordnade händelsekoden för en händelseprenumeration med regler.

- Kräver ett värde

### `--rules`

Listan med regler för händelseprenumerationen, där varje regel formateras som&quot;field\|operator\|value&quot;.

- Standard: `[]`
- Kräver ett värde

### `--priority`, `-p`

Underlättar överföringen av den här händelsen. Ange det här alternativet för händelser som måste levereras omedelbart. Som standard skickas händelser av cron en gång per minut.

- Standard: `false`
- Accepterar inte ett värde

### `--destination`, `-d`

Målet för den här händelsen. Ange det här alternativet för händelser som ska levereras till det anpassade målet.

- Standard: `default`
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


## `events:sync-events-metadata`

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

Synkronisera händelsemetadata för instansen


### `--delete`, `-d`

Ta bort metadata för händelser som inte längre behövs

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


## `events:unsubscribe`

```bash
bin/magento events:unsubscribe <event-code>
```

Tar bort prenumerationen på den angivna händelsen



### `event-code`

Händelsekod att avbryta prenumerationen på

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


## `i18n:collect-phrases`

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

Upptäcker fraser i kodbasen



### `directory`

Katalogsökväg som ska tolkas. Behövs inte om flaggan —magento är inställd


### `--output`, `-o`

Sökväg (inklusive filnamn) till en utdatafil. Om ingen fil har angetts är standardinställningen stdout.

- Kräver ett värde

### `--magento`, `-m`

Använd parametern —magento för att tolka den aktuella Magento-kodbasen. Utelämna parametern om en katalog anges.

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


## `i18n:pack`

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

Sparar språkpaket



### `source`

Sökväg till källordsfil med översättningar

- Obligatoriskt

### `locale`

Målspråk för ordlista, till exempel &quot;de_DE&quot;

- Obligatoriskt

### `--mode`, `-m`

Spara läge för ordlista -&quot;ersätt&quot; - ersätt språkpaket med nytt -&quot;sammanfoga&quot; - sammanfoga språkpaket, som standard&quot;ersätt&quot;

- Standard: `replace`
- Kräver ett värde

### `--allow-duplicates`, `-d`

Använd parametern —allow-duplicates för att tillåta att dubbletter av translate sparas. Annars utelämnar du parametern.

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


## `i18n:uninstall`

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

Avinstallerar språkpaket



### `package`

Språkpaketets namn

- Standard: `[]`

- Obligatoriskt
- Array

### `--backup-code`, `-b`

Säkerhetskopiera kod och konfigurationsfiler (förutom temporära filer)

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


## `indexer:info`

```bash
bin/magento indexer:info
```

Visar tillåtna indexerare


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


## `indexer:reindex`

```bash
bin/magento indexer:reindex [<index>...]
```

Indexerar om data



### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`

- Array

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


## `indexer:reset`

```bash
bin/magento indexer:reset [<index>...]
```

Återställer indexerarstatus till ogiltig



### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`

- Array

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


## `indexer:set-dimensions-mode`

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

Ange indexeringsläge för Dimensioner



### `indexer`

Indexerarnamn [catalog_product_price|catalogpermissions_category]


### `mode`

Dimensionslägena katalog_product_price none,webbplats,kundgrupp,webbplats_och_kund_grupp katalog permissions_category none,kundgrupp


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


## `indexer:set-mode`

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

Anger typ av indexläge



### `mode`

Typ av indexeringsläge [realtid|schema]


### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`

- Array

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


## `indexer:set-status`

```bash
bin/magento indexer:set-status <status> [<index>...]
```

Anger angiven indexerarstatus



### `status`

Statustyp för indexerare [ogiltig|pausad|giltig]

- Obligatoriskt

### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`

- Array

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


## `indexer:show-dimensions-mode`

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

Visar indexerarens Dimension



### `indexer`

Blankstegsavgränsad lista med indextyper eller utelämna den för alla index (catalog_product_price,catalogpermissions_category)

- Standard: `[]`

- Array

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


## `indexer:show-mode`

```bash
bin/magento indexer:show-mode [<index>...]
```

Visar indexläge



### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`

- Array

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


## `indexer:status`

```bash
bin/magento indexer:status [<index>...]
```

Visar indexerarens status



### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`

- Array

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


## `info:adminuri`

```bash
bin/magento info:adminuri
```

Visar Magento Admin URI


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


## `info:backups:list`

```bash
bin/magento info:backups:list
```

Skriver ut lista över tillgängliga säkerhetskopior


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


## `info:currency:list`

```bash
bin/magento info:currency:list
```

Visar listan över tillgängliga valutor


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


## `info:dependencies:show-framework`

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

Visar antalet beroenden till Magento-ramverket


### `--output`, `-o`

Rapportfilnamn

- Standard: `framework-dependencies.csv`
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


## `info:dependencies:show-modules`

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

Visar antalet beroenden mellan moduler


### `--output`, `-o`

Rapportfilnamn

- Standard: `modules-dependencies.csv`
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


## `info:dependencies:show-modules-circular`

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

Visar antalet cirkulära beroenden mellan moduler


### `--output`, `-o`

Rapportfilnamn

- Standard: `modules-circular-dependencies.csv`
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


## `info:language:list`

```bash
bin/magento info:language:list
```

Visar en lista över tillgängliga språkområden


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


## `info:timezone:list`

```bash
bin/magento info:timezone:list
```

Visar listan över tillgängliga tidszoner


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


## `inventory:reservation:create-compensations`

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

Skapa reservationer med angivna kompensationsargument



### `compensations`

Lista med kompensationsargument i formatet &quot;::::&quot;

- Standard: `[]`

- Array

### `--raw`, `-r`

Råutdata

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


## `inventory:reservation:list-inconsistencies`

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

Visa alla order och produkter med inkonsekvenser i försäljningsbar kvantitet


### `--complete-orders`, `-c`

Visa endast inkonsekvenser för fullständiga order

- Standard: `false`
- Accepterar inte ett värde

### `--incomplete-orders`, `-i`

Visa endast inkonsekvenser för ofullständiga order

- Standard: `false`
- Accepterar inte ett värde

### `--bunch-size`, `-b`

Definierar hur många order som läses in samtidigt

- Standard: `50`
- Accepterar ett värde

### `--raw`, `-r`

Råutdata

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


## `inventory-geonames:import`

```bash
bin/magento inventory-geonames:import <countries>...
```

Hämta och importera geonamn för källvalsalgoritm



### `countries`

Lista över landskoder som ska importeras

- Standard: `[]`

- Obligatoriskt
- Array

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


## `maintenance:allow-ips`

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

Anger undantagna IP-adresser i underhållsläge



### `ip`

Tillåtna IP-adresser

- Standard: `[]`

- Array

### `--none`

Rensa tillåtna IP-adresser

- Standard: `false`
- Accepterar inte ett värde

### `--add`

Lägg till IP-adressen i den befintliga listan

- Standard: `false`
- Accepterar inte ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `maintenance:disable`

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Inaktiverar underhållsläge


### `--ip`

Tillåtna IP-adresser (använd &#39;none&#39; för att rensa tillåten IP-lista)

- Standard: `[]`
- Kräver ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `maintenance:enable`

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Aktiverar underhållsläge


### `--ip`

Tillåtna IP-adresser (använd &#39;none&#39; för att rensa tillåten IP-lista)

- Standard: `[]`
- Kräver ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `maintenance:status`

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Visar status för underhållsläge


### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `media-content:sync`

```bash
bin/magento media-content:sync
```

Synkronisera innehåll med resurser


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


## `media-gallery:sync`

```bash
bin/magento media-gallery:sync
```

Synkronisera medielagring och medieresurser i databasen


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


## `module:config:status`

```bash
bin/magento module:config:status
```

Kontrollerar modulkonfigurationen i filen app/etc/config.php och rapporterar om den är uppdaterad eller inte


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


## `module:disable`

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Inaktiverar angivna moduler



### `module`

Namn på modulen

- Standard: `[]`

- Array

### `--force`, `-f`

Åsidosätt beroendekontroll

- Standard: `false`
- Accepterar inte ett värde

### `--all`

Inaktivera alla moduler

- Standard: `false`
- Accepterar inte ett värde

### `--clear-static-content`, `-c`

Rensa genererade statiska vyfiler. Om modulerna har statiska visningsfiler krävs

- Standard: `false`
- Accepterar inte ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `module:enable`

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Aktiverar angivna moduler



### `module`

Namn på modulen

- Standard: `[]`

- Array

### `--force`, `-f`

Åsidosätt beroendekontroll

- Standard: `false`
- Accepterar inte ett värde

### `--all`

Aktivera alla moduler

- Standard: `false`
- Accepterar inte ett värde

### `--clear-static-content`, `-c`

Rensa genererade statiska vyfiler. Om modulerna har statiska visningsfiler krävs

- Standard: `false`
- Accepterar inte ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `module:status`

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

Visar status för moduler



### `module-names`

Modulnamn (valfritt)

- Standard: `[]`

- Array

### `--enabled`

Skriv bara ut aktiverade moduler

- Standard: `false`
- Accepterar inte ett värde

### `--disabled`

Skriv bara ut inaktiverade moduler

- Standard: `false`
- Accepterar inte ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `module:uninstall`

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

Avinstallerar moduler som installerats av disposition



### `module`

Namn på modulen

- Standard: `[]`

- Obligatoriskt
- Array

### `--remove-data`, `-r`

Ta bort data som har installerats av moduler

- Standard: `false`
- Accepterar inte ett värde

### `--backup-code`

Säkerhetskopiera kod och konfigurationsfiler (förutom temporära filer)

- Standard: `false`
- Accepterar inte ett värde

### `--backup-media`

Säkerhetskopiera media

- Standard: `false`
- Accepterar inte ett värde

### `--backup-db`

Utför fullständig säkerhetskopiering av databasen

- Standard: `false`
- Accepterar inte ett värde

### `--non-composer`

Alla moduler som kommer att ligga utanför här är inte dispositionsbaserade

- Standard: `false`
- Accepterar inte ett värde

### `--clear-static-content`, `-c`

Rensa genererade statiska vyfiler. Om modulerna har statiska visningsfiler krävs

- Standard: `false`
- Accepterar inte ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `newrelic:create:deploy-marker`

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

Kontrollera om det finns poster i distributionskön och skapa en lämplig distributionsmarkör.



### `message`

Vill du distribuera meddelandet?

- Obligatoriskt

### `change_log`

Ändra logg?

- Obligatoriskt

### `user`

Distributionsanvändare


### `revision`

Revision


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


## `queue:consumers:list`

```bash
bin/magento queue:consumers:list
```

Lista över MessageQueue-användare


```
This command shows list of MessageQueue consumers.
```

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


## `queue:consumers:restart`

```bash
bin/magento queue:consumers:restart
```

Starta om MessageQueue-användare


```
Command put poison pill for MessageQueue consumers and force to restart them after next status check.
```

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


## `queue:consumers:start`

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

Starta MessageQueue-konsument


```
This command starts MessageQueue consumer by its name.

To start consumer which will process all queued messages and terminate execution:

    bin/magento queue:consumers:start someConsumer

To specify the number of messages which should be processed by consumer before its termination:

    bin/magento queue:consumers:start someConsumer --max-messages=50

To specify the number of messages per batch for the batch consumer:

    bin/magento queue:consumers:start someConsumer --batch-size=500

To specify the preferred area:

    bin/magento queue:consumers:start someConsumer --area-code='adminhtml'

To do not run multiple copies of one consumer simultaneously:

    bin/magento queue:consumers:start someConsumer --single-thread

To save PID enter path (This option is deprecated, use --single-thread instead):

    bin/magento queue:consumers:start someConsumer --pid-file-path='/var/someConsumer.pid'

To define the number of processes per consumer:

    bin/magento queue:consumers:start someConsumer --multi-process=4
```


### `consumer`

Namnet på den konsument som ska startas.

- Obligatoriskt

### `--max-messages`

Antalet meddelanden som ska bearbetas av konsumenten innan processen avslutas. Om inget anges avslutas alla meddelanden som står i kö.

- Kräver ett värde

### `--batch-size`

Antalet meddelanden per batch. Gäller endast för batchkonsumenten.

- Kräver ett värde

### `--area-code`

Standardområdet (global, adminhtml, osv.) är globalt.

- Kräver ett värde

### `--single-thread`

Det här alternativet förhindrar att flera kopior av en kund körs samtidigt.

- Standard: `false`
- Accepterar inte ett värde

### `--multi-process`

Antalet processer per kund.

- Accepterar ett värde

### `--pid-file-path`

Filsökvägen för att spara PID (det här alternativet är föråldrat, använd —single-thread i stället)

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


## `remote-storage:sync`

```bash
bin/magento remote-storage:sync
```

Synkronisera mediefiler med fjärrlagring.


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


## `saas:resync`

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync]
```

Synkroniserar om feed-data till SaaS-tjänsten.


### `--feed`

Feed-namn för att helt synkronisera om till SaaS-tjänsten. Tillgängliga feeds: Betalningstjänster, Orderproduktion, Betalningstjänster, Ordersandlåda, Betalningstjänster, Orderstatus, Statussandlåda för Betalningstjänster, Butiksproduktion för Betalningstjänster, Butikssandlåda för Betalningstjänster

- Kräver ett värde

### `--no-reindex`

Kör endast omsändning av feed-data till SaaS-tjänsten. Indexerar inte om. (Detta alternativ gäller inte för produkterna, produkterna, åsidosättningarna, prisflödena)

- Standard: `false`
- Accepterar inte ett värde

### `--cleanup-feed`

Tvinga rensning av flödesindexerartabellen före synkronisering.

- Standard: `false`
- Accepterar inte ett värde

### `--dry-run`

Torr körning. Data exporteras inte. Spara nyttolast i loggfilen var/log/saas-export.log med miljövariabeln EXPORTER_EXTENDED_LOG=1.

- Standard: `false`
- Accepterar inte ett värde

### `--thread-count`

Ange antalet synkroniseringstråd.

- Kräver ett värde

### `--batch-size`

Ange batchstorlek för synkronisering

- Kräver ett värde

### `--continue-resync`

Fortsätt omsynkronisera från den senast lagrade positionen (det här alternativet gäller för produkterna, produktionsåsidosättningar, prisflöden)

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


## `sampledata:deploy`

```bash
bin/magento sampledata:deploy [--no-update]
```

Distribuera exempeldatamoduler för dispositionsbaserade Magento-installationer


### `--no-update`

Uppdatera Composer.json utan att köra Composer-uppdatering

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


## `sampledata:remove`

```bash
bin/magento sampledata:remove [--no-update]
```

Ta bort alla exempeldatapaket från Composer.json


### `--no-update`

Uppdatera Composer.json utan att köra Composer-uppdatering

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


## `sampledata:reset`

```bash
bin/magento sampledata:reset
```

Återställ alla exempeldatamoduler för ominstallation


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


## `security:recaptcha:disable-for-user-forgot-password`

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

Inaktivera reCAPTCHA för administratörsanvändaren har glömt lösenordsformuläret


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


## `security:recaptcha:disable-for-user-login`

```bash
bin/magento security:recaptcha:disable-for-user-login
```

Inaktivera reCAPTCHA för inloggningsformulär för administratörer


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


## `security:tfa:google:set-secret`

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

Ange hemligheten som används för generering av engångslösenord i Google.



### `user`

Användarnamn

- Obligatoriskt

### `secret`

Hemlighet

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


## `security:tfa:providers`

```bash
bin/magento security:tfa:providers
```

Visa alla tillgängliga leverantörer


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


## `security:tfa:reset`

```bash
bin/magento security:tfa:reset <user> <provider>
```

Återställ konfigurationen för en användare



### `user`

Användarnamn

- Obligatoriskt

### `provider`

Providerkod

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


## `server:run`

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

Kör programserver


### `--port`, `-p`

port att servera på

- Standard: `9501`
- Accepterar ett värde

### `--background`, `-b`

flagga för bakgrundsläge

- Standard: `0`
- Accepterar ett värde

### `--workerNum`, `-wn`

antal arbetsprocesser att starta

- Standard: `4`
- Accepterar ett värde

### `--dispatchMode`, `-dm`

läge för att skicka anslutningar till arbetsprocesserna

- Standard: `3`
- Accepterar ett värde

### `--maxRequests`, `-mr`

max antal begäranden innan arbetsprocessen startas om

- Standard: `10000`
- Accepterar ett värde

### `--area`, `-a`

programserverområde

- Standard: `graphql`
- Accepterar ett värde

### `--magento-init-params`, `-mip`

magento bootstrap init params

- Standard: &quot;
- Accepterar ett värde

### `--maxWaitTime`, `-mwt`

Hur länge du väntar på arbetare efter omladdning (t.ex. konfigurationsändring) innan de dör

- Standard: `3600`
- Accepterar ett värde

### `--state-monitor`

Aktivera tillståndsövervakning. Använd endast detta för felsökning av tillståndsproblem!

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


## `server:state-monitor:aggregate-output`

```bash
bin/magento server:state-monitor:aggregate-output
```

Sammanställa utdata från tillståndsövervakaren för ApplicationServer


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


## `setup:backup`

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Säkerhetskopierar Magento programkodbas, media och databas


### `--code`

Säkerhetskopiera kod och konfigurationsfiler (förutom temporära filer)

- Standard: `false`
- Accepterar inte ett värde

### `--media`

Säkerhetskopiera media

- Standard: `false`
- Accepterar inte ett värde

### `--db`

Utför fullständig säkerhetskopiering av databasen

- Standard: `false`
- Accepterar inte ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:config:set`

```bash
bin/magento setup:config:set [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Skapar eller ändrar distributionskonfigurationen


### `--enable-debug-logging`

Aktivera felsökningsloggning

- Kräver ett värde

### `--enable-syslog-logging`

Aktivera syslog-loggning

- Kräver ett värde

### `--backend-frontname`

Förnamn för serverdel (genereras automatiskt om det saknas)

- Kräver ett värde

### `--remote-storage-driver`

Drivrutin för fjärrlagring

- Kräver ett värde

### `--remote-storage-prefix`

Prefix för fjärrlagring

- Standard: &quot;
- Kräver ett värde

### `--remote-storage-endpoint`

Slutpunkt för fjärrlagring

- Kräver ett värde

### `--remote-storage-bucket`

Fjärrlagringsbucket

- Kräver ett värde

### `--remote-storage-region`

Fjärrlagringsregion

- Kräver ett värde

### `--remote-storage-key`

Åtkomstnyckel för fjärrlagring

- Standard: &quot;
- Kräver ett värde

### `--remote-storage-secret`

Hemlig nyckel för fjärrlagring

- Standard: &quot;
- Kräver ett värde

### `--remote-storage-path-style`

Stil för fjärrlagringssökväg

- Standard: `0`
- Kräver ett värde

### `--id_salt`

GraphQl Salt

- Kräver ett värde

### `--config-async`

Vill du aktivera Spara async Admin Config? 1 - Ja, 0 - Nej

- Kräver ett värde

### `--checkout-async`

Vill du aktivera asynkron orderbearbetning? 1 - Ja, 0 - Nej

- Kräver ett värde

### `--amqp-host`

AMQP-servervärd

- Standard: &quot;
- Kräver ett värde

### `--amqp-port`

AMQP-serverport

- Standard: `5672`
- Kräver ett värde

### `--amqp-user`

Användarnamn för AMQP-server

- Standard: &quot;
- Kräver ett värde

### `--amqp-password`

Lösenord för AMQP-server

- Standard: &quot;
- Kräver ett värde

### `--amqp-virtualhost`

Virtualhost för Amqp

- Standard: `/`
- Kräver ett värde

### `--amqp-ssl`

Amqp SSL

- Standard: &quot;
- Kräver ett värde

### `--amqp-ssl-options`

AMQP SSL-alternativ (JSON)

- Standard: &quot;
- Kräver ett värde

### `--consumers-wait-for-messages`

Ska konsumenterna vänta på ett meddelande från kön? 1 - Ja, 0 - Nej

- Kräver ett värde

### `--queue-default-connection`

Standardanslutning för Message Queues. Kan vara db, amqp eller ett anpassat kösystem. Kösystemet måste vara installerat och konfigurerat, annars kommer meddelanden inte att behandlas korrekt.

- Kräver ett värde

### `--deferred-total-calculating`

Vill du aktivera fördröjd total beräkning? 1 - Ja, 0 - Nej

- Kräver ett värde

### `--key`

Krypteringsnyckel

- Kräver ett värde

### `--db-host`

Databasservervärd

- Kräver ett värde

### `--db-name`

Databasnamn

- Kräver ett värde

### `--db-user`

Användarnamn för databasserver

- Kräver ett värde

### `--db-engine`

Databasservermotor

- Kräver ett värde

### `--db-password`

Lösenord för databasserver

- Kräver ett värde

### `--db-prefix`

Prefix för databastabell

- Kräver ett värde

### `--db-model`

Databastyp

- Kräver ett värde

### `--db-init-statements`

Initial uppsättning kommandon för databas

- Kräver ett värde

### `--skip-db-validation`, `-s`

Om det anges hoppas validering av databasanslutning över

- Standard: `false`
- Accepterar inte ett värde

### `--http-cache-hosts`

http-cachevärdar

- Kräver ett värde

### `--db-ssl-key`

Fullständig sökväg till klientnyckelfilen för att upprätta en databasanslutning via SSL

- Standard: &quot;
- Kräver ett värde

### `--db-ssl-cert`

Fullständig sökväg till klientcertifikatfilen för att upprätta en databasanslutning via SSL

- Standard: &quot;
- Kräver ett värde

### `--db-ssl-ca`

Fullständig sökväg till servercertifikatfilen för att upprätta en databasanslutning via SSL

- Standard: &quot;
- Kräver ett värde

### `--db-ssl-verify`

Verifiera servercertifiering

- Standard: `false`
- Accepterar inte ett värde

### `--session-save`

Hanterare för sessionssparande

- Kräver ett värde

### `--session-save-redis-host`

Fullständigt kvalificerat värdnamn, IP-adress eller absolut sökväg om UNIX-socketar används

- Kräver ett värde

### `--session-save-redis-port`

Redis-serverlyssningsport

- Kräver ett värde

### `--session-save-redis-password`

Redis-serverlösenord

- Kräver ett värde

### `--session-save-redis-timeout`

Anslutningens timeout, i sekunder

- Kräver ett värde

### `--session-save-redis-persistent-id`

Unik sträng för att aktivera beständiga anslutningar

- Kräver ett värde

### `--session-save-redis-db`

Redis-databasnummer

- Kräver ett värde

### `--session-save-redis-compression-threshold`

Komprimeringströskel för Redis

- Kräver ett värde

### `--session-save-redis-compression-lib`

Redis-komprimeringsbibliotek. Värden: gzip (standard), lzf, lz4, snappy

- Kräver ett värde

### `--session-save-redis-log-level`

Redis-loggnivå. Värden: 0 (minst utförlig) till 7 (mest utförlig)

- Kräver ett värde

### `--session-save-redis-max-concurrency`

Maximalt antal processer som kan vänta på ett lås i en session

- Kräver ett värde

### `--session-save-redis-break-after-frontend`

Antal sekunder att vänta innan ett lås för en klientsession bryts

- Kräver ett värde

### `--session-save-redis-break-after-adminhtml`

Antal sekunder att vänta innan ett lås för administratörssessionen bryts

- Kräver ett värde

### `--session-save-redis-first-lifetime`

Livstid, i sekunder, för session för icke-bots vid första skrivning (använd 0 för att inaktivera)

- Kräver ett värde

### `--session-save-redis-bot-first-lifetime`

Livstid, i sekunder, för session för bots vid första skrivning (använd 0 för att inaktivera)

- Kräver ett värde

### `--session-save-redis-bot-lifetime`

Sessionens livstid för start vid efterföljande skrivningar (använd 0 för att inaktivera)

- Kräver ett värde

### `--session-save-redis-disable-locking`

Redis inaktiverar låsning. Värden: false (standard), true

- Kräver ett värde

### `--session-save-redis-min-lifetime`

Redis-sessionens livstid i sekunder

- Kräver ett värde

### `--session-save-redis-max-lifetime`

Maximal sessionstid för Redis, i sekunder

- Kräver ett värde

### `--session-save-redis-sentinel-master`

Redis Sentinel master

- Kräver ett värde

### `--session-save-redis-sentinel-servers`

Redis Sentinel-servrar, kommaseparerade

- Kräver ett värde

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel, verifiera master. Värden: false (standard), true

- Kräver ett värde

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel-anslutningsförsök.

- Kräver ett värde

### `--cache-backend`

Standardhanterare för cache

- Kräver ett värde

### `--cache-backend-redis-server`

Redis-server

- Kräver ett värde

### `--cache-backend-redis-db`

Databasnummer för cachen

- Kräver ett värde

### `--cache-backend-redis-port`

Redis-serverlyssningsport

- Kräver ett värde

### `--cache-backend-redis-password`

Redis-serverlösenord

- Kräver ett värde

### `--cache-backend-redis-compress-data`

Ange 0 om du vill inaktivera komprimering (standard är 1, aktiverad)

- Kräver ett värde

### `--cache-backend-redis-compression-lib`

Komprimeringsbibliotek att använda [snappy,lzf,l4z,zstd,gzip] (lämna tomt för att bestämma automatiskt)

- Kräver ett värde

### `--cache-backend-redis-use-lua`

Ange 1 för att aktivera Llua (standard är 0, inaktiverat)

- Kräver ett värde

### `--cache-id-prefix`

ID-prefix för cachenycklar

- Kräver ett värde

### `--allow-parallel-generation`

Tillåt generering av cache på ett icke-blockerande sätt

- Standard: `false`
- Accepterar inte ett värde

### `--page-cache`

Standardhanterare för cache

- Kräver ett värde

### `--page-cache-redis-server`

Redis-server

- Kräver ett värde

### `--page-cache-redis-db`

Databasnummer för cachen

- Kräver ett värde

### `--page-cache-redis-port`

Redis-serverlyssningsport

- Kräver ett värde

### `--page-cache-redis-password`

Redis-serverlösenord

- Kräver ett värde

### `--page-cache-redis-compress-data`

Ange 1 för att komprimera helsidescachen (använd 0 för att inaktivera)

- Kräver ett värde

### `--page-cache-redis-compression-lib`

Komprimeringsbibliotek att använda [snappy,lzf,l4z,zstd,gzip] (lämna tomt för att bestämma automatiskt)

- Kräver ett värde

### `--page-cache-id-prefix`

ID-prefix för cachenycklar

- Kräver ett värde

### `--lock-provider`

Lås leverantörsnamn

- Kräver ett värde

### `--lock-db-prefix`

Installationsspecifikt låsprefix för att undvika låskonflikter

- Kräver ett värde

### `--lock-zookeeper-host`

Värd och port för anslutning till Zookeeper-klustret. Exempel: 127.0.0.1:2181

- Kräver ett värde

### `--lock-zookeeper-path`

Sökvägen där Zookeeper sparar lås. Standardsökvägen är: /magento/locks

- Kräver ett värde

### `--lock-file-path`

Sökvägen där fillås sparas.

- Kräver ett värde

### `--document-root-is-pub`

Flagga som ska visas är Pub är på roten, kan bara vara true eller false

- Kräver ett värde

### `--backpressure-logger`

Hanterare för mottrycksloggare

- Kräver ett värde

### `--backpressure-logger-redis-server`

Redis-server

- Kräver ett värde

### `--backpressure-logger-redis-port`

Redis-serverlyssningsport

- Kräver ett värde

### `--backpressure-logger-redis-timeout`

Servertimeout för Redis

- Kräver ett värde

### `--backpressure-logger-redis-persistent`

Redis persistent

- Kräver ett värde

### `--backpressure-logger-redis-db`

Redis-databasnummer

- Kräver ett värde

### `--backpressure-logger-redis-password`

Redis-serverlösenord

- Kräver ett värde

### `--backpressure-logger-redis-user`

Redis-serveranvändare

- Kräver ett värde

### `--backpressure-logger-id-prefix`

ID-prefix för nycklar

- Kräver ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-data:upgrade`

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installerar och uppgraderar data i databasen


### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-declaration:generate-patch`

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

Generera en patch och placera den i en specifik mapp.



### `module`

Modulnamn

- Obligatoriskt

### `patch`

Namn på korrigering

- Obligatoriskt

### `--revertable`

Kontrollera om korrigeringen kan ångras eller inte.

- Standard: `false`
- Accepterar ett värde

### `--type`

Ta reda på vilken typ av korrigering som ska skapas. Tillgängliga värden: `data`, `schema`.

- Standard: `data`
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


## `setup:db-declaration:generate-whitelist`

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

Generera vitlista över tabeller och kolumner som kan redigeras av deklarationsinstallationsprogrammet


### `--module-name`

Namn på modulen där vitlistan ska genereras

- Standard: `all`
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


## `setup:db-schema:add-slave`

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Flytta tabeller relaterade till utcheckningsofferter till en separat databasserver


### `--host`

Slave DB-servervärd

- Standard: `localhost`
- Kräver ett värde

### `--dbname`

Slave-databasnamn

- Kräver ett värde

### `--username`

Slave DB-användarnamn

- Standard: `root`
- Kräver ett värde

### `--password`

Slave DB-användarlösenord

- Accepterar ett värde

### `--connection`

Slavanslutningsnamn

- Standard: `default`
- Accepterar ett värde

### `--resource`

Slavresursnamn

- Standard: `default`
- Accepterar ett värde

### `--maxAllowedLag`

Maximal tillåten fördröjd slavanslutning (i sekunder)

- Standard: &quot;
- Accepterar ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-schema:split-quote`

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Flytta tabeller relaterade till utcheckningsofferter till en separat databasserver. Borttagen sedan 2.4.2 och kommer att tas bort


### `--host`

Checkout DB Server-värd

- Kräver ett värde

### `--dbname`

Namn på utcheckningsdatabas

- Kräver ett värde

### `--username`

Användarnamn för utcheckning av databas

- Kräver ett värde

### `--password`

Checkout-användarlösenord för DB

- Accepterar ett värde

### `--connection`

Anslutningsnamn för utcheckning

- Standard: `checkout`
- Accepterar ett värde

### `--resource`

Utcheckningsresursnamn

- Standard: `checkout`
- Accepterar ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-schema:split-sales`

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Flytta försäljningsrelaterade register till en separat databasserver. Borttagen sedan 2.4.2 och kommer att tas bort


### `--host`

Sales DB Server-värd

- Kräver ett värde

### `--dbname`

Namn på försäljningsdatabas

- Kräver ett värde

### `--username`

Användarnamn för försäljningsdatabas

- Kräver ett värde

### `--password`

Användarlösenord för försäljningsdatabas

- Accepterar ett värde

### `--connection`

Namn på försäljningsanslutning

- Standard: `sales`
- Accepterar ett värde

### `--resource`

Namn på försäljningsresurs

- Standard: `sales`
- Accepterar ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-schema:upgrade`

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installerar och uppgraderar databasschemat


### `--convert-old-scripts`

Tillåter konvertering av gamla skript (InstallSchema, UpgradeSchema) till formatet db_schema.xml

- Standard: `false`
- Accepterar ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db:status`

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Kontrollerar om databasschemat eller data kräver uppgradering


### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:di:compile`

```bash
bin/magento setup:di:compile
```

Genererar DI-konfiguration och alla saknade klasser som kan genereras automatiskt


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


## `setup:install`

```bash
bin/magento setup:install [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installerar programmet Magento


### `--enable-debug-logging`

Aktivera felsökningsloggning

- Kräver ett värde

### `--enable-syslog-logging`

Aktivera syslog-loggning

- Kräver ett värde

### `--backend-frontname`

Förnamn för serverdel (genereras automatiskt om det saknas)

- Kräver ett värde

### `--remote-storage-driver`

Drivrutin för fjärrlagring

- Kräver ett värde

### `--remote-storage-prefix`

Prefix för fjärrlagring

- Standard: &quot;
- Kräver ett värde

### `--remote-storage-endpoint`

Slutpunkt för fjärrlagring

- Kräver ett värde

### `--remote-storage-bucket`

Fjärrlagringsbucket

- Kräver ett värde

### `--remote-storage-region`

Fjärrlagringsregion

- Kräver ett värde

### `--remote-storage-key`

Åtkomstnyckel för fjärrlagring

- Standard: &quot;
- Kräver ett värde

### `--remote-storage-secret`

Hemlig nyckel för fjärrlagring

- Standard: &quot;
- Kräver ett värde

### `--remote-storage-path-style`

Stil för fjärrlagringssökväg

- Standard: `0`
- Kräver ett värde

### `--id_salt`

GraphQl Salt

- Kräver ett värde

### `--config-async`

Vill du aktivera Spara async Admin Config? 1 - Ja, 0 - Nej

- Kräver ett värde

### `--checkout-async`

Vill du aktivera asynkron orderbearbetning? 1 - Ja, 0 - Nej

- Kräver ett värde

### `--amqp-host`

AMQP-servervärd

- Standard: &quot;
- Kräver ett värde

### `--amqp-port`

AMQP-serverport

- Standard: `5672`
- Kräver ett värde

### `--amqp-user`

Användarnamn för AMQP-server

- Standard: &quot;
- Kräver ett värde

### `--amqp-password`

Lösenord för AMQP-server

- Standard: &quot;
- Kräver ett värde

### `--amqp-virtualhost`

Virtualhost för Amqp

- Standard: `/`
- Kräver ett värde

### `--amqp-ssl`

Amqp SSL

- Standard: &quot;
- Kräver ett värde

### `--amqp-ssl-options`

AMQP SSL-alternativ (JSON)

- Standard: &quot;
- Kräver ett värde

### `--consumers-wait-for-messages`

Ska konsumenterna vänta på ett meddelande från kön? 1 - Ja, 0 - Nej

- Kräver ett värde

### `--queue-default-connection`

Standardanslutning för Message Queues. Kan vara db, amqp eller ett anpassat kösystem. Kösystemet måste vara installerat och konfigurerat, annars kommer meddelanden inte att behandlas korrekt.

- Kräver ett värde

### `--deferred-total-calculating`

Vill du aktivera fördröjd total beräkning? 1 - Ja, 0 - Nej

- Kräver ett värde

### `--key`

Krypteringsnyckel

- Kräver ett värde

### `--db-host`

Databasservervärd

- Kräver ett värde

### `--db-name`

Databasnamn

- Kräver ett värde

### `--db-user`

Användarnamn för databasserver

- Kräver ett värde

### `--db-engine`

Databasservermotor

- Kräver ett värde

### `--db-password`

Lösenord för databasserver

- Kräver ett värde

### `--db-prefix`

Prefix för databastabell

- Kräver ett värde

### `--db-model`

Databastyp

- Kräver ett värde

### `--db-init-statements`

Initial uppsättning kommandon för databas

- Kräver ett värde

### `--skip-db-validation`, `-s`

Om det anges hoppas validering av databasanslutning över

- Standard: `false`
- Accepterar inte ett värde

### `--http-cache-hosts`

http-cachevärdar

- Kräver ett värde

### `--db-ssl-key`

Fullständig sökväg till klientnyckelfilen för att upprätta en databasanslutning via SSL

- Standard: &quot;
- Kräver ett värde

### `--db-ssl-cert`

Fullständig sökväg till klientcertifikatfilen för att upprätta en databasanslutning via SSL

- Standard: &quot;
- Kräver ett värde

### `--db-ssl-ca`

Fullständig sökväg till servercertifikatfilen för att upprätta en databasanslutning via SSL

- Standard: &quot;
- Kräver ett värde

### `--db-ssl-verify`

Verifiera servercertifiering

- Standard: `false`
- Accepterar inte ett värde

### `--session-save`

Hanterare för sessionssparande

- Kräver ett värde

### `--session-save-redis-host`

Fullständigt kvalificerat värdnamn, IP-adress eller absolut sökväg om UNIX-socketar används

- Kräver ett värde

### `--session-save-redis-port`

Redis-serverlyssningsport

- Kräver ett värde

### `--session-save-redis-password`

Redis-serverlösenord

- Kräver ett värde

### `--session-save-redis-timeout`

Anslutningens timeout, i sekunder

- Kräver ett värde

### `--session-save-redis-persistent-id`

Unik sträng för att aktivera beständiga anslutningar

- Kräver ett värde

### `--session-save-redis-db`

Redis-databasnummer

- Kräver ett värde

### `--session-save-redis-compression-threshold`

Komprimeringströskel för Redis

- Kräver ett värde

### `--session-save-redis-compression-lib`

Redis-komprimeringsbibliotek. Värden: gzip (standard), lzf, lz4, snappy

- Kräver ett värde

### `--session-save-redis-log-level`

Redis-loggnivå. Värden: 0 (minst utförlig) till 7 (mest utförlig)

- Kräver ett värde

### `--session-save-redis-max-concurrency`

Maximalt antal processer som kan vänta på ett lås i en session

- Kräver ett värde

### `--session-save-redis-break-after-frontend`

Antal sekunder att vänta innan ett lås för en klientsession bryts

- Kräver ett värde

### `--session-save-redis-break-after-adminhtml`

Antal sekunder att vänta innan ett lås för administratörssessionen bryts

- Kräver ett värde

### `--session-save-redis-first-lifetime`

Livstid, i sekunder, för session för icke-bots vid första skrivning (använd 0 för att inaktivera)

- Kräver ett värde

### `--session-save-redis-bot-first-lifetime`

Livstid, i sekunder, för session för bots vid första skrivning (använd 0 för att inaktivera)

- Kräver ett värde

### `--session-save-redis-bot-lifetime`

Sessionens livstid för start vid efterföljande skrivningar (använd 0 för att inaktivera)

- Kräver ett värde

### `--session-save-redis-disable-locking`

Redis inaktiverar låsning. Värden: false (standard), true

- Kräver ett värde

### `--session-save-redis-min-lifetime`

Redis-sessionens livstid i sekunder

- Kräver ett värde

### `--session-save-redis-max-lifetime`

Maximal sessionstid för Redis, i sekunder

- Kräver ett värde

### `--session-save-redis-sentinel-master`

Redis Sentinel master

- Kräver ett värde

### `--session-save-redis-sentinel-servers`

Redis Sentinel-servrar, kommaseparerade

- Kräver ett värde

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel, verifiera master. Värden: false (standard), true

- Kräver ett värde

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel-anslutningsförsök.

- Kräver ett värde

### `--cache-backend`

Standardhanterare för cache

- Kräver ett värde

### `--cache-backend-redis-server`

Redis-server

- Kräver ett värde

### `--cache-backend-redis-db`

Databasnummer för cachen

- Kräver ett värde

### `--cache-backend-redis-port`

Redis-serverlyssningsport

- Kräver ett värde

### `--cache-backend-redis-password`

Redis-serverlösenord

- Kräver ett värde

### `--cache-backend-redis-compress-data`

Ange 0 om du vill inaktivera komprimering (standard är 1, aktiverad)

- Kräver ett värde

### `--cache-backend-redis-compression-lib`

Komprimeringsbibliotek att använda [snappy,lzf,l4z,zstd,gzip] (lämna tomt för att bestämma automatiskt)

- Kräver ett värde

### `--cache-backend-redis-use-lua`

Ange 1 för att aktivera Llua (standard är 0, inaktiverat)

- Kräver ett värde

### `--cache-id-prefix`

ID-prefix för cachenycklar

- Kräver ett värde

### `--allow-parallel-generation`

Tillåt generering av cache på ett icke-blockerande sätt

- Standard: `false`
- Accepterar inte ett värde

### `--page-cache`

Standardhanterare för cache

- Kräver ett värde

### `--page-cache-redis-server`

Redis-server

- Kräver ett värde

### `--page-cache-redis-db`

Databasnummer för cachen

- Kräver ett värde

### `--page-cache-redis-port`

Redis-serverlyssningsport

- Kräver ett värde

### `--page-cache-redis-password`

Redis-serverlösenord

- Kräver ett värde

### `--page-cache-redis-compress-data`

Ange 1 för att komprimera helsidescachen (använd 0 för att inaktivera)

- Kräver ett värde

### `--page-cache-redis-compression-lib`

Komprimeringsbibliotek att använda [snappy,lzf,l4z,zstd,gzip] (lämna tomt för att bestämma automatiskt)

- Kräver ett värde

### `--page-cache-id-prefix`

ID-prefix för cachenycklar

- Kräver ett värde

### `--lock-provider`

Lås leverantörsnamn

- Kräver ett värde

### `--lock-db-prefix`

Installationsspecifikt låsprefix för att undvika låskonflikter

- Kräver ett värde

### `--lock-zookeeper-host`

Värd och port för anslutning till Zookeeper-klustret. Exempel: 127.0.0.1:2181

- Kräver ett värde

### `--lock-zookeeper-path`

Sökvägen där Zookeeper sparar lås. Standardsökvägen är: /magento/locks

- Kräver ett värde

### `--lock-file-path`

Sökvägen där fillås sparas.

- Kräver ett värde

### `--document-root-is-pub`

Flagga som ska visas är Pub är på roten, kan bara vara true eller false

- Kräver ett värde

### `--backpressure-logger`

Hanterare för mottrycksloggare

- Kräver ett värde

### `--backpressure-logger-redis-server`

Redis-server

- Kräver ett värde

### `--backpressure-logger-redis-port`

Redis-serverlyssningsport

- Kräver ett värde

### `--backpressure-logger-redis-timeout`

Servertimeout för Redis

- Kräver ett värde

### `--backpressure-logger-redis-persistent`

Redis persistent

- Kräver ett värde

### `--backpressure-logger-redis-db`

Redis-databasnummer

- Kräver ett värde

### `--backpressure-logger-redis-password`

Redis-serverlösenord

- Kräver ett värde

### `--backpressure-logger-redis-user`

Redis-serveranvändare

- Kräver ett värde

### `--backpressure-logger-id-prefix`

ID-prefix för nycklar

- Kräver ett värde

### `--base-url`

Den URL som butiken ska vara tillgänglig på. Inaktuell, använd config:set med sökväg web/unsecure/base_url

- Kräver ett värde

### `--language`

Standardspråkkod. Inaktuell, använd config:set med sökväg general/locale/code

- Kräver ett värde

### `--timezone`

Standardkod för tidszon. Inaktuell, använd config:set med sökväg allmän/nationell inställning/tidszon

- Kräver ett värde

### `--currency`

Standardvalutakod. Inaktuellt, använd config:set med sökvägsvaluta/alternativ/bas, valuta/alternativ/standard och valuta/alternativ/tillåt

- Kräver ett värde

### `--use-rewrites`

Använd omskrivningar. Inaktuell, använd config:set med sökväg web/seo/use_rewrites

- Kräver ett värde

### `--use-secure`

Använd säkra URL:er. Aktivera bara det här alternativet om SSL är tillgängligt. Inaktuell, använd config:set med sökväg web/secure/use_in_frontTur

- Kräver ett värde

### `--base-url-secure`

Bas-URL för SSL-anslutning. Inaktuell, använd config:set med sökvägen web/secure/base_url

- Kräver ett värde

### `--use-secure-admin`

Kör administratörsgränssnitt med SSL. Inaktuell, använd config:set med sökvägen web/secure/use_in_adminhtml

- Kräver ett värde

### `--admin-use-security-key`

Anger om en säkerhetsnyckelfunktion ska användas i Magento Admin-URL:er och -formulär. Inaktuell, använd config:set med sökvägsadministratör/säkerhet/use_form_key

- Kräver ett värde

### `--admin-user`

Administratörsanvändare

- Accepterar ett värde

### `--admin-password`

Administratörslösenord

- Accepterar ett värde

### `--admin-email`

Administratörens e-postadress

- Accepterar ett värde

### `--admin-firstname`

Förnamn för administratör

- Accepterar ett värde

### `--admin-lastname`

Administratörens efternamn

- Accepterar ett värde

### `--search-engine`

Sökmotor. Värden: elasticsearch7, elasticsearch8, opensearch

- Kräver ett värde

### `--elasticsearch-host`

Elasticsearch servervärd.

- Kräver ett värde

### `--elasticsearch-port`

Elasticsearch serverport.

- Kräver ett värde

### `--elasticsearch-enable-auth`

Ange 1 för att aktivera autentisering. (standard är 0, inaktiverad)

- Kräver ett värde

### `--elasticsearch-username`

Elasticsearch användarnamn. Gäller endast om HTTP-autentisering är aktiverat

- Kräver ett värde

### `--elasticsearch-password`

Elasticsearch lösenord. Gäller endast om HTTP-autentisering är aktiverat

- Kräver ett värde

### `--elasticsearch-index-prefix`

Elasticsearch-indexprefix.

- Kräver ett värde

### `--elasticsearch-timeout`

Servertimeout för Elasticsearch.

- Kräver ett värde

### `--opensearch-host`

OpenSearch-servervärd.

- Kräver ett värde

### `--opensearch-port`

OpenSearch-serverport.

- Kräver ett värde

### `--opensearch-enable-auth`

Ange 1 för att aktivera autentisering. (standard är 0, inaktiverad)

- Kräver ett värde

### `--opensearch-username`

OpenSearch-användarnamn. Gäller endast om HTTP-autentisering är aktiverat

- Kräver ett värde

### `--opensearch-password`

OpenSearch-lösenord. Gäller endast om HTTP-autentisering är aktiverat

- Kräver ett värde

### `--opensearch-index-prefix`

Index för OpenSearch.

- Kräver ett värde

### `--opensearch-timeout`

Tidsgräns för OpenSearch-server.

- Kräver ett värde

### `--cleanup-database`

Rensa databasen före installationen

- Standard: `false`
- Accepterar inte ett värde

### `--sales-order-increment-prefix`

Prefix för försäljningsordernummer

- Kräver ett värde

### `--use-sample-data`

Använd exempeldata

- Standard: `false`
- Accepterar inte ett värde

### `--enable-modules`

Lista med kommaavgränsade modulnamn. Detta måste ingå under installationen. Tillgängliga magiska param &quot;all&quot;.

- Accepterar ett värde

### `--disable-modules`

Lista med kommaavgränsade modulnamn. Detta måste undvikas under installationen. Tillgängliga magiska param &quot;all&quot;.

- Accepterar ett värde

### `--convert-old-scripts`

Tillåter konvertering av gamla skript (InstallSchema, UpgradeSchema) till formatet db_schema.xml

- Standard: `false`
- Accepterar ett värde

### `--interactive`, `-i`

Interaktiv installation av Magento

- Standard: `false`
- Accepterar inte ett värde

### `--safe-mode`

Säker installation av Magento med dumpar på destruktiva operationer, som borttagning av spalter

- Accepterar ett värde

### `--data-restore`

Återställ borttagna data från dumpar

- Accepterar ett värde

### `--dry-run`

Installationen av Magento kommer att köras i torrkörningsläge

- Standard: `false`
- Accepterar ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:performance:generate-fixtures`

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

Skapar korrigeringar



### `profile`

Sökväg till profilkonfigurationsfil

- Obligatoriskt

### `--skip-reindex`, `-s`

Hoppa över omindexering

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


## `setup:rollback`

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Återställer Magento-programkodbas, media och databas


### `--code-file`, `-c`

Basnamn för säkerhetskopieringsfilen för kod i var/backups

- Kräver ett värde

### `--media-file`, `-m`

Basnamn för mediesäkerhetskopieringsfilen i var/backups

- Kräver ett värde

### `--db-file`, `-d`

Basnamn för databassäkerhetskopieringsfilen i var/backups

- Kräver ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:static-content:deploy`

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

Distribuerar statiska vyfiler



### `languages`

Blankstegsavgränsad lista med ISO-639-språkkoder som statiska vyfiler ska skrivas ut för.

- Standard: `[]`

- Array

### `--force`, `-f`

Distribuera filer i valfritt läge.

- Standard: `false`
- Accepterar inte ett värde

### `--strategy`, `-s`

Distribuera filer med angiven strategi.

- Standard: `quick`
- Accepterar ett värde

### `--area`, `-a`

Generera filer endast för de angivna områdena.

- Standard: `all`
- Accepterar flera värden

### `--exclude-area`

Generera inga filer för de angivna områdena.

- Standard: `none`
- Accepterar flera värden

### `--theme`, `-t`

Generera statiska vyfiler endast för de angivna temana.

- Standard: `all`
- Accepterar flera värden

### `--exclude-theme`

Generera inte filer för de angivna temana.

- Standard: `none`
- Accepterar flera värden

### `--language`, `-l`

Generera filer endast för de angivna språken.

- Standard: `all`
- Accepterar flera värden

### `--exclude-language`

Generera inte filer för de angivna språken.

- Standard: `none`
- Accepterar flera värden

### `--jobs`, `-j`

Aktivera parallell bearbetning med angivet antal jobb.

- Standard: `0`
- Accepterar ett värde

### `--max-execution-time`

Maximal förväntad körningstid för den statiska distributionsprocessen (i sekunder).

- Standard: `900`
- Accepterar ett värde

### `--symlink-locale`

Skapa länkar för filerna för de språkinställningarna som skickas för distribution, men som inte har några anpassningar.

- Standard: `false`
- Accepterar inte ett värde

### `--content-version`

Anpassad version av statiskt innehåll kan användas om distributionen körs på flera noder för att säkerställa att den statiska innehållsversionen är identisk och att cachelagring fungerar som den ska.

- Kräver ett värde

### `--refresh-content-version-only`

Om du bara uppdaterar versionen av statiskt innehåll kan du uppdatera statiskt innehåll i webbläsarens cache och CDN-cache.

- Standard: `false`
- Accepterar inte ett värde

### `--no-javascript`

Distribuera inte JavaScript-filer.

- Standard: `false`
- Accepterar inte ett värde

### `--no-js-bundle`

Distribuera inte JavaScript-paketfiler.

- Standard: `false`
- Accepterar inte ett värde

### `--no-css`

Distribuera inte CSS-filer.

- Standard: `false`
- Accepterar inte ett värde

### `--no-less`

Distribuera inte LESS-filer.

- Standard: `false`
- Accepterar inte ett värde

### `--no-images`

Distribuera inte bilder.

- Standard: `false`
- Accepterar inte ett värde

### `--no-fonts`

Distribuera inte teckensnittsfiler.

- Standard: `false`
- Accepterar inte ett värde

### `--no-html`

Distribuera inte HTML-filer.

- Standard: `false`
- Accepterar inte ett värde

### `--no-misc`

Distribuera inte filer av andra typer (.md, .jbf, .csv osv.).

- Standard: `false`
- Accepterar inte ett värde

### `--no-html-minify`

Minimera inte HTML-filer.

- Standard: `false`
- Accepterar inte ett värde

### `--no-parent`

Kompilera inte överordnade teman. Stöds endast i snabba och standardiserade strategier.

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


## `setup:store-config:set`

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installerar butikskonfigurationen. Borttagen sedan 2.2.0. Använd config:set i stället


### `--base-url`

Den URL som butiken ska vara tillgänglig på. Inaktuell, använd config:set med sökväg web/unsecure/base_url

- Kräver ett värde

### `--language`

Standardspråkkod. Inaktuell, använd config:set med sökväg general/locale/code

- Kräver ett värde

### `--timezone`

Standardkod för tidszon. Inaktuell, använd config:set med sökväg allmän/nationell inställning/tidszon

- Kräver ett värde

### `--currency`

Standardvalutakod. Inaktuellt, använd config:set med sökvägsvaluta/alternativ/bas, valuta/alternativ/standard och valuta/alternativ/tillåt

- Kräver ett värde

### `--use-rewrites`

Använd omskrivningar. Inaktuell, använd config:set med sökväg web/seo/use_rewrites

- Kräver ett värde

### `--use-secure`

Använd säkra URL:er. Aktivera bara det här alternativet om SSL är tillgängligt. Inaktuell, använd config:set med sökväg web/secure/use_in_frontTur

- Kräver ett värde

### `--base-url-secure`

Bas-URL för SSL-anslutning. Inaktuell, använd config:set med sökvägen web/secure/base_url

- Kräver ett värde

### `--use-secure-admin`

Kör administratörsgränssnitt med SSL. Inaktuell, använd config:set med sökvägen web/secure/use_in_adminhtml

- Kräver ett värde

### `--admin-use-security-key`

Anger om en säkerhetsnyckelfunktion ska användas i Magento Admin-URL:er och -formulär. Inaktuell, använd config:set med sökvägsadministratör/säkerhet/use_form_key

- Kräver ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:uninstall`

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

Avinstallerar programmet Magento


### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:upgrade`

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Uppgraderar Magento-programmet, DB-data och schema


### `--keep-generated`

Förhindrar att genererade filer tas bort. Vi avråder från att använda det här alternativet förutom när vi distribuerar till produktion. Kontakta systemintegratören eller administratören om du vill ha mer information.

- Standard: `false`
- Accepterar inte ett värde

### `--convert-old-scripts`

Tillåter konvertering av gamla skript (InstallSchema, UpgradeSchema) till formatet db_schema.xml

- Standard: `false`
- Accepterar ett värde

### `--safe-mode`

Säker installation av Magento med dumpar på destruktiva operationer, som borttagning av spalter

- Accepterar ett värde

### `--data-restore`

Återställ borttagna data från dumpar

- Accepterar ett värde

### `--dry-run`

Installationen av Magento kommer att köras i torrkörningsläge

- Standard: `false`
- Accepterar ett värde

### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `store:list`

```bash
bin/magento store:list
```

Visar listan över butiker


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


## `store:website:list`

```bash
bin/magento store:website:list
```

Visar listan över webbplatser


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


## `support:backup:code`

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

Skapa säkerhetskopia av kod


### `--name`

Dumpa namn

- Accepterar ett värde

### `--output`, `-o`

Utdatasökväg

- Accepterar ett värde

### `--logs`, `-l`

Inkludera loggar

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


## `support:backup:db`

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

Skapa DB-säkerhetskopiering


### `--name`

Dumpa namn

- Accepterar ett värde

### `--output`, `-o`

Utdatasökväg

- Accepterar ett värde

### `--logs`, `-l`

Inkludera loggar

- Standard: `false`
- Accepterar inte ett värde

### `--ignore-sanitize`, `-i`

Ignorera sanering

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


## `support:utility:check`

```bash
bin/magento support:utility:check [--hide-paths]
```

Kontrollera nödvändiga verktyg för säkerhetskopiering


### `--hide-paths`

Kontrollera bara nödvändiga konsolverktyg

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


## `support:utility:paths`

```bash
bin/magento support:utility:paths [-f|--force]
```

Skapa verktygssökvägslista


### `--force`, `-f`

Tvinga

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


## `theme:uninstall`

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

Avinstallerar tema



### `theme`

Sökväg till temat. Temasökvägen ska anges som fullständig sökväg, vilket är område/leverantör/namn. Till exempel front/Magento/blank

- Standard: `[]`

- Obligatoriskt
- Array

### `--backup-code`

Säkerhetskopiera kod (förutom tillfälliga filer)

- Standard: `false`
- Accepterar inte ett värde

### `--clear-static-content`, `-c`

Rensa genererade statiska vyfiler.

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


## `varnish:vcl:generate`

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

Skapar lack VCL och lägger det på kommandoraden


### `--access-list`

IP-åtkomstlista som kan rensa engelska

- Standard: `localhost`
- Kräver ett värde

### `--backend-host`

Värd för webbserverdelen

- Standard: `localhost`
- Kräver ett värde

### `--backend-port`

Port för webbserverdelen

- Standard: `8080`
- Kräver ett värde

### `--export-version`

The version of Varnish file

- Standard: `6`
- Kräver ett värde

### `--grace-period`

Behåll programmet i sekunder

- Standard: `300`
- Kräver ett värde

### `--input-file`

Indatafil att generera cl från

- Kräver ett värde

### `--output-file`

Sökväg till filen som ska skrivas vcl

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


## `webhooks:dev:run`

```bash
bin/magento webhooks:dev:run <name> <payload>
```

Kör en registrerad webkrok i utvecklingssyfte.



### `name`

Webkrocksnamn

- Obligatoriskt

### `payload`

Webkroknyttolasten i JSON-format

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


## `webhooks:generate:module`

```bash
bin/magento webhooks:generate:module
```

Generera plugin-program baserat på webkroks registreringar


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


## `webhooks:info`

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```

Returnerar nyttolasten för den angivna webkroken.



### `webhook-name`

Namn på webkrockmetod

- Obligatoriskt

### `webhook-type`

Webkrotyp (före, efter)

- Standard: `before`


### `--depth`

Antalet nivåer i webkroks nyttolast som ska returneras

- Standard: `3`
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


## `webhooks:list`

```bash
bin/magento webhooks:list
```

Visar en lista över webbhookar som prenumererar


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


## `webhooks:list:all`

```bash
bin/magento webhooks:list:all <module_name>
```

Returnerar en lista över webbhovsmetodnamn som stöds för den angivna modulen



### `module_name`

Modulnamn

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
