---
source-git-commit: ba444c5f74cdeec86c842014d02775faf16b2f50
workflow-type: tm+mt
source-wordcount: '8253'
ht-degree: 0%

---
# bin/magento (Adobe Commerce lokalt)

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->

**Version**: 2.4.8

Den här referensen innehåller 145 kommandon som `bin/magento` är tillgängliga via kommandoradsverktyget.
Den första listan genereras automatiskt med hjälp av `bin/magento list` kommandot på Adobe Commerce.

## Allmänt

[Använd guiden &quot;Lägg till CLI-kommandon&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) för att lägga till ett anpassat CLI-kommando.

Du kan anropa `bin/magento` CLI-kommandon med hjälp av genvägar i stället för det fullständiga kommandonamnet. Du kan till exempel ringa `bin/magento setup:upgrade` med , `bin/magento s:up``bin/magento s:upg`. Se [kortkommandosyntax](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) för att förstå hur du använder genvägar med alla CLI-kommandon.

Den här referensdokumentationen genereras från programmets källkod. Om du vill ändra dokumentationen bör du öppna en pull-begäran för motsvarande kommando i den relevanta [kodbaslagringsplatsen](https://github.com/magento) . Se [Kodbidrag](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) för mer information.

### Globala alternativ

#### `--help`, `-h`

Visa hjälp för det givna kommandot. När inget kommando ges visas visningshjälp för listkommandot

- Standard: `false`
- Accepterar inte ett värde

#### `--quiet`, `-q`

Mata inte ut något meddelande

- Standard: `false`
- Accepterar inte ett värde

#### `--verbose`, `-v|-vv|-vvv`

Öka utförligheten för meddelanden: 1 för normala utdata, 2 för mer utförliga utdata och 3 för felsökning

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

Förneka flaggan &quot;--ansi&quot;

- Standard: `false`
- Accepterar inte ett värde

#### `--no-interaction`, `-n`

Ställ inga interaktiva frågor

- Standard: `false`
- Accepterar inte ett värde


## `_complete`

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Internt kommando för att ge förslag på komplettering av skal

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

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

API-versionen av slutförandeskriptet

- Kräver ett värde

#### `--symfony`, `-S`

Deprecated

- Kräver ett värde


## `completion`

```bash
bin/magento completion [--debug] [--] [<shell>]
```

Dumpa skriptet för slutförande av skalet

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

### Argument

#### `shell`

Gränssnittstypen (t.ex. &quot;bash&quot;), värdet för &quot;$SHELL&quot; env var, används om detta inte anges

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--debug`

Svansa felsökningsloggen för slutförande

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

För att mata ut rå kommandohjälp

- Standard: `false`
- Accepterar inte ett värde


## `list`

```bash
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Lista kommandon

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

### Argument

#### `namespace`

Namnet på namnområdet

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--raw`

För att mata ut rå kommandolista

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


## `admin:adobe-ims:disable`

```bash
bin/magento admin:adobe-ims:disable
```

Inaktivera Adobe IMS-modulen

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `admin:adobe-ims:enable`

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

Aktivera Adobe IMS-modulen.

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--organization-id`, `-o`

Ange organisations-ID för Adobe IMS-konfigurationen. Krävs när modulen aktiveras

- Accepterar ett värde

#### `--client-id`, `-c`

Ange klient-ID för Adobe IMS-konfigurationen. Krävs när du aktiverar modulen

- Accepterar ett värde

#### `--client-secret`, `-s`

Ange klienthemlighet för Adobe IMS-konfigurationen. Krävs när modulen aktiveras

- Accepterar ett värde

#### `--2fa`, `-t`

Kontrollera om 2FA är aktiverat för Organisation i Adobe Admin Console. Krävs när du aktiverar modulen

- Accepterar ett värde


## `admin:adobe-ims:info`

```bash
bin/magento admin:adobe-ims:info
```

Information om Adobe IMS-modulkonfiguration

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `admin:adobe-ims:status`

```bash
bin/magento admin:adobe-ims:status
```

Status för Adobe IMS-modul

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `admin:user:create`

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Skapar en administratör

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--admin-user`

(Obligatoriskt) Administratörsanvändare

- Kräver ett värde

#### `--admin-password`

(Obligatoriskt) Admin lösenord

- Kräver ett värde

#### `--admin-email`

(Obligatoriskt) Administratörens e-postadress

- Kräver ett värde

#### `--admin-firstname`

(Obligatoriskt) Förnamn för administratör

- Kräver ett värde

#### `--admin-lastname`

(Obligatoriskt) Administratörens efternamn

- Kräver ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


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

### Argument

#### `username`

Administratörens användarnamn som ska låsas upp

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `app:config:dump`

```bash
bin/magento app:config:dump [<config-types>...]
```

Skapa programdump

### Argument

#### `config-types`

Blankstegsavgränsad lista över konfigurationstyper eller utelämna att dumpa alla [omfång, teman, system, i18n]

- Standard: `[]`
- Samling

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `app:config:import`

```bash
bin/magento app:config:import
```

Importera data från delade konfigurationsfiler till lämplig datalagring

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `app:config:status`

```bash
bin/magento app:config:status
```

Kontrollerar om konfigurationsspridning kräver uppdatering

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `braintree:migrate`

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

Migrera lagrade kort från en Magento 1-databas

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--host`

Värdnamn/IP. Porten är valfri

- Kräver ett värde

#### `--dbname`

Databasnamn

- Kräver ett värde

#### `--username`

Användarnamn för databas. Måste ha läsåtkomst

- Kräver ett värde

#### `--password`

Lösenord

- Kräver ett värde


## `cache:clean`

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Rensar cachetyp(er)

### Argument

#### `types`

Blankstegsavgränsad lista över cachetyper eller utelämna att gälla för alla cachetyper.

- Standard: `[]`
- Samling

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--bootstrap`

Lägga till eller åsidosätta parametrar för Bootstrap

- Kräver ett värde


## `cache:clean:payment_services_merchant_scopes`

```bash
bin/magento cache:clean:payment_services_merchant_scopes
```

Cache för rena betaltjänster för handlare

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `cache:disable`

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Inaktiverar cachetyp(er)

### Argument

#### `types`

Blankstegsavgränsad lista över cachetyper eller utelämna att gälla för alla cachetyper.

- Standard: `[]`
- Samling

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--bootstrap`

lägga till eller åsidosätta parametrar för bootstrap

- Kräver ett värde


## `cache:enable`

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Aktiverar cachetyp(er)

### Argument

#### `types`

Blankstegsavgränsad lista över cachetyper eller utelämna att gälla för alla cachetyper.

- Standard: `[]`
- Samling

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--bootstrap`

Lägga till eller åsidosätta parametrar för Bootstrap

- Kräver ett värde


## `cache:flush`

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Tömmer cachelagring som används av cachetyper

### Argument

#### `types`

Blankstegsavgränsad lista med cachetyper eller utelämna att använda för alla cachetyper.

- Standard: `[]`
- Array

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--bootstrap`

lägga till eller åsidosätta parametrar för bootstrap

- Kräver ett värde


## `cache:status`

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

Kontrollerar cachestatus

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--bootstrap`

Lägga till eller åsidosätta parametrar för Bootstrap

- Kräver ett värde


## `catalog:images:resize`

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

Skapar storleksändrade produktbilder

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--async`, `-a`

Ändra storlek på bild i asynkront läge

- Standard: `false`
- Accepterar inte ett värde

#### `--skip_hidden_images`

Bearbeta inte bilder som markerats som dolda från produktsidan

- Standard: `false`
- Accepterar inte ett värde


## `catalog:product:attributes:cleanup`

```bash
bin/magento catalog:product:attributes:cleanup
```

Tar bort oanvända produktattribut.

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `cms:wysiwyg:restrict`

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

Ange om du vill framtvinga validering av användarens HTML-innehåll eller visa en varning i stället

### Argument

#### `restrict`

y\n

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `config:sensitive:set`

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

Ange känsliga konfigurationsvärden

### Argument

#### `path`

Konfigurationssökväg för exempelgrupp/avdelning/field_name


#### `value`

Konfigurations värde

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--interactive`, `-i`

Aktivera interaktivt läge för att ställa in alla känsliga variabler

- Standard: `false`
- Accepterar inte ett värde

#### `--scope`

Omfång för konfiguration, om det inte anges använder du &quot;standard&quot;

- Standard: `default`
- Accepterar ett värde

#### `--scope-code`

Omfångskod för konfiguration, tom sträng som standard

- Standard: &#39;&#39;
- Accepterar ett värde


## `config:set`

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

Ändra systemkonfiguration

### Argument

#### `path`

Konfigurationssökväg i formatavsnitt/grupp/field_name

- Krävs


#### `value`

Konfigurations värde

- Obligatoriskt

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--scope`

Konfigurationsomfång (standard, webbplats eller butik)

- Standard: `default`
- Kräver ett värde

#### `--scope-code`

Scope-kod (krävs endast om scope inte är &#39;default&#39;)

- Kräver ett värde

#### `--lock-env`, `-e`

Lås värde som förhindrar ändringar i Admin (sparas i app/etc/env.php)

- Standard: `false`
- Accepterar inte ett värde

#### `--lock-config`, `-c`

Lås och dela värdet med andra installationer, förhindra ändringar i Admin (sparas i app/etc/config.php)

- Standard: `false`
- Accepterar inte ett värde

#### `--lock`, `-l`

Inaktuell, använd alternativet --lock-env i stället.

- Standard: `false`
- Accepterar inte ett värde


## `config:show`

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

Visar konfigurationsvärde för angiven sökväg. Om sökväg inte anges visas alla sparade värden

### Argument

#### `path`

Konfigurationssökväg, till exempel section_id/group_id/field_id

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--scope`

Om inget konfigurationsområde anges används standardomfånget

- Standard: `default`
- Accepterar ett värde

#### `--scope-code`

Scope-kod (krävs endast om scope inte är `default`)

- Standard: &quot;
- Accepterar ett värde


## `cron:install`

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

Skapar och installerar crontab för aktuell användare

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--force`, `-f`

Tvinga fram installationsuppgifter

- Standard: `false`
- Accepterar inte ett värde

#### `--non-optional`, `-d`

Installera endast icke-valfria (standard) uppgifter

- Standard: `false`
- Accepterar inte ett värde


## `cron:remove`

```bash
bin/magento cron:remove
```

Tar bort uppgifter från crontab

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `cron:run`

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

Kör jobb enligt schema

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--group`

Kör endast jobb från angiven grupp

- Kräver ett värde

#### `--exclude-group`

Uteslut jobb från den angivna gruppen

- Standard: `[]`
- Accepterar flera värden

#### `--bootstrap`

Lägga till eller åsidosätta parametrar för bootstrap

- Kräver ett värde


## `customer:hash:upgrade`

```bash
bin/magento customer:hash:upgrade
```

Uppgradera kundens hash enligt den senaste algoritmen

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `deploy:mode:set`

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

Ange programläge.

### Argument

#### `mode`

Det programläge som ska anges. Tillgängliga alternativ är &quot;utvecklare&quot; eller &quot;produktion&quot;

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--skip-compilation`, `-s`

Hoppar över rensning och omgenerering av statiskt innehåll (genererad kod, förbearbetad CSS och resurser i pub/static/)

- Standard: `false`
- Accepterar inte ett värde


## `deploy:mode:show`

```bash
bin/magento deploy:mode:show
```

Visar det aktuella programläget.

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `dev:di:info`

```bash
bin/magento dev:di:info <class> [<area>]
```

Anger information om konfigurationen för beroendeinmatning för kommandot.

### Argument

#### `class`

Klassnamn

- Obligatoriskt


#### `area`

Riktnummer

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `dev:email:newsletter-compatibility-check`

```bash
bin/magento dev:email:newsletter-compatibility-check
```

Skannar nyhetsbrevsmallar efter potentiella kompatibilitetsproblem med variabel användning

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `dev:email:override-compatibility-check`

```bash
bin/magento dev:email:override-compatibility-check
```

Söker igenom e-postmallåsidosättningar för eventuella kompatibilitetsproblem med variabel användning

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `dev:profiler:disable`

```bash
bin/magento dev:profiler:disable
```

Inaktivera profileraren.

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `dev:profiler:enable`

```bash
bin/magento dev:profiler:enable [<type>]
```

Aktivera profileraren.

### Argument

#### `type`

Profilerartyp

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `dev:query-log:disable`

```bash
bin/magento dev:query-log:disable
```

Inaktivera loggning av databasfrågor

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `dev:query-log:enable`

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

Aktivera loggning av databasfrågor

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--include-all-queries`

Logga alla frågor. [sant\|falskt]

- Standard: `true`
- Accepterar ett värde

#### `--query-time-threshold`

Tröskelvärden för frågetid.

- Standard: `0.001`
- Accepterar ett värde

#### `--include-call-stack`

Inkludera anropsstacken. [true\|false]

- Standard: `true`
- Accepterar ett värde


## `dev:source-theme:deploy`

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

Samlar in och publicerar källfiler för temat.

### Argument

#### `file`

Filer som ska förbearbetas (filen ska anges utan tillägg)

- Standard: `css/styles-mcss/styles-l`

- Samling

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--type`

Typ av källfiler: [mindre]

- Standard: `less`
- Kräver ett värde

#### `--locale`

Språk: [en_US]

- Standard: `en_US`
- Kräver ett värde

#### `--area`

Område: [frontend\|adminhtml]

- Standard: `frontend`
- Kräver ett värde

#### `--theme`

Tema: [Leverantör/tema]

- Standard: `Magento/luma`
- Kräver ett värde


## `dev:template-hints:disable`

```bash
bin/magento dev:template-hints:disable
```

Inaktivera malltips för frontend. En cachetömning kan behövas.

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `dev:template-hints:enable`

```bash
bin/magento dev:template-hints:enable
```

Aktivera malltips för frontend. En cachetömning kan behövas.

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `dev:template-hints:status`

```bash
bin/magento dev:template-hints:status
```

Visa status för malltips för förgreningstips.

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `dev:tests:run`

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

Kör tester

### Argument

#### `type`

Typ av test som ska köras. Tillgängliga typer: all, unit, integration, integration, all, static, static-all, integrity, legacy, default

- Standard: `default`

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--arguments`, `-c`

Ytterligare argument för PHPUnit. Exempel: &quot;-c&quot;—filter=MyTest&quot; (inga blanksteg)

- Standard: &quot;
- Kräver ett värde


## `dev:urn-catalog:generate`

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

Skapar katalogen med URN:er till *.xsd-mappningar så att XML markeras.

### Argument

#### `path`

Sökväg till filen för att mata ut katalogen. För PhpStorm använd .idea/misc.xml

- Krävs

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--ide`

Format som katalogen ska genereras i. Stöds: [phpstorm, vscode]

- Standard: `phpstorm`
- Kräver ett värde


## `dev:xml:convert`

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

Konverterar XML-fil med hjälp av XSL-formatmallar

### Argument

#### `xml-file`

Sökväg till XML-fil som ska transformeras

- Obligatoriskt


#### `processor`

Sökväg till XSL-formatmall som ska användas i XML-filen

- Obligatoriskt

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--overwrite`, `-o`

Skriv över XML-fil

- Standard: `false`
- Accepterar inte ett värde


## `downloadable:domains:add`

```bash
bin/magento downloadable:domains:add [<domains>...]
```

Lägg till domäner i vitlistan över nedladdningsbara domäner

### Argument

#### `domains`

Domännamn

- Standard: `[]`
- Samling

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `downloadable:domains:remove`

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

Ta bort domäner från vitlistan över nedladdningsbara domäner

### Argument

#### `domains`

Domännamn

- Standard: `[]`
- Samling

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `downloadable:domains:show`

```bash
bin/magento downloadable:domains:show
```

Visa vitlista över nedladdningsbara domäner

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `encryption:data:list-re-encryptors`

```bash
bin/magento encryption:data:list-re-encryptors
```

Visar en lista över tillgängliga datakrypterare.

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `encryption:data:re-encrypt`

```bash
bin/magento encryption:data:re-encrypt [<encryptors>...]
```

Återkrypterar krypterade data med den aktuella krypteringsnyckeln.

### Argument

#### `encryptors`

Blankstegsavgränsad lista över omkrypterare som ska användas.

- Standard: `[]`
- Array

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `encryption:key:change`

```bash
bin/magento encryption:key:change [-k|--key [KEY]]
```

Ändra krypteringsnyckeln i env.php-filen.

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--key`, `-k`

Nyckeln måste vara en 32 tecken lång sträng. Om ingen anges genereras en slumpmässig nyckel.

- Accepterar ett värde


## `encryption:payment-data:update`

```bash
bin/magento encryption:payment-data:update
```

Återkrypterar krypterade kreditkortsdata med det senaste krypteringschiffret.

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `events:create-event-provider`

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]events:provider:create 
```

Skapa en anpassad händelseprovider i Adobe I/O Events för den här instansen. Om du inte anger alternativ för etikett och beskrivning måste de definieras i systemets app/etc/event-types.json.

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--label`

En etikett för att definiera din anpassade provider.

- Accepterar ett värde

#### `--description`

En beskrivning av din leverantör.

- Accepterar ett värde


## `events:generate:module`

```bash
bin/magento events:generate:module
```

Generera modul baserat på plugins-lista

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `events:info`

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```

Returnerar nyttolasten för den angivna händelsen.

### Argument

#### `event-code`

Händelsekod

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--depth`

Antalet nivåer i händelsens nyttolast som ska returneras

- Standard: `2`
- Accepterar ett värde


## `events:list`

```bash
bin/magento events:list
```

Visar en lista över prenumererade händelser

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `events:list:all`

```bash
bin/magento events:list:all <module_name>
```

Returnerar en lista över prenumerationsbara händelser som definierats i den angivna modulen

### Argument

#### `module_name`

Modulens namn

- Krävs

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `events:metadata:populate`

```bash
bin/magento events:metadata:populate
```

Skapar metadata i Adobe I/O från konfigurationslistan (XML- och programkonfigurationer)

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `events:provider:info`

```bash
bin/magento events:provider:info
```

Returnerar information om den konfigurerade händelseprovidern

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `events:registrations:list`

```bash
bin/magento events:registrations:list
```

Visar händelseregistreringar i ditt App Builder-projekt

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `events:subscribe`

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [-d|--destination DESTINATION] [--hipaaAuditRequired] [--] <event-code>
```

Prenumererar på evenemanget

### Argument

#### `event-code`

Händelsekod

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--force`, `-f`

Tvingar den angivna händelsen att prenumerera, även om den inte har definierats lokalt.

- Standard: `false`
- Accepterar inte ett värde

#### `--fields`

Listan över fält i nyttolasten för händelsedata.

- Standard: `[]`
- Kräver ett värde

#### `--parent`

Den överordnade händelsekoden för en händelseprenumeration med regler eller som ett alias.

- Kräver ett värde

#### `--rules`

Listan över regler för händelseprenumerationen, där varje regel är formaterad som &quot;field\|operator\|value&quot;. Om du vill använda det här alternativet måste du också ange alternativet &quot;överordnad&quot;.

- Standard: `[]`
- Kräver ett värde

#### `--priority`, `-p`

Underlättar överföringen av den här händelsen. Ange det här alternativet för händelser som måste levereras omedelbart. Som standard skickas händelser av cron en gång per minut.

- Standard: `false`
- Accepterar inte ett värde

#### `--destination`, `-d`

Målet för den här händelsen. Ange det här alternativet för de händelser som ska levereras till det anpassade målet.

- Standard: `default`
- Kräver ett värde

#### `--hipaaAuditRequired`

Anger att händelsen innehåller data som omfattas av HIPAA-granskning.

- Standard: `false`
- Accepterar inte ett värde


## `events:sync-events-metadata`

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

Synkronisera händelsemetadata för den här instansen

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--delete`, `-d`

Ta bort metadata för händelser som inte längre behövs

- Standard: `false`
- Accepterar inte ett värde


## `events:unsubscribe`

```bash
bin/magento events:unsubscribe <event-code>
```

Tar bort prenumerationen på den angivna händelsen

### Argument

#### `event-code`

Händelsekod att avbryta prenumerationen på

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `i18n:collect-phrases`

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

Identifierar fraser i kodbasen

### Argument

#### `directory`

Katalogsökväg som ska tolkas. Behövs inte om --magento-flaggan är satt

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--output`, `-o`

Sökväg (inklusive filnamn) till en utdatafil. Om ingen fil har angetts är standardinställningen stdout.

- Kräver ett värde

#### `--magento`, `-m`

Använd parametern —magento för att tolka den aktuella Magento-kodbasen. Utelämna parametern om en katalog anges.

- Standard: `false`
- Accepterar inte ett värde


## `i18n:pack`

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

Sparar språkpaket

### Argument

#### `source`

Sökväg till källordsfil med översättningar

- Obligatoriskt


#### `locale`

Målspråk för ordlista, till exempel &quot;de_DE&quot;

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--mode`, `-m`

Spara läge för ordlista -&quot;ersätt&quot; - ersätt språkpaket med nytt -&quot;sammanfoga&quot; - sammanfoga språkpaket, som standard&quot;ersätt&quot;

- Standard: `replace`
- Kräver ett värde

#### `--allow-duplicates`, `-d`

Använd parametern —allow-duplicates för att tillåta att dubbletter av translate sparas. Annars utelämnar du parametern.

- Standard: `false`
- Accepterar inte ett värde


## `i18n:uninstall`

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

Avinstallerar språkpaket

### Argument

#### `package`

Språkpaketets namn

- Standard: `[]`
- Obligatoriskt

- Samling

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--backup-code`, `-b`

Ta en säkerhetskopia av kod- och konfigurationsfiler (exklusive temporära filer)

- Standard: `false`
- Accepterar inte ett värde


## `indexer:info`

```bash
bin/magento indexer:info
```

Visar tillåtna indexerare

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `indexer:reindex`

```bash
bin/magento indexer:reindex [<index>...]
```

Indexerar om data

### Argument

#### `index`

Blankstegsavgränsad lista över indextyper eller utelämna att gälla för alla index.

- Standard: `[]`
- Samling

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `indexer:reset`

```bash
bin/magento indexer:reset [<index>...]
```

Återställer indexerarstatus till ogiltig

### Argument

#### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`
- Array

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `indexer:set-dimensions-mode`

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

Ange indexerardimensionsläge

### Argument

#### `indexer`

Indexerarnamn [catalog_product_price|catalogpermissions_category]


#### `mode`

Indexeringens dimensionslägen catalog_product_price          ingen,webbplats,kundgrupp,webbplats_och_kund_gruppkatalog behörigheter_kategori    ingen,kundgrupp

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `indexer:set-mode`

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

Ställer in indexlägestyp

### Argument

#### `mode`

Typ av indexerarläge [realtid|schema]


#### `index`

Blankstegsavgränsad lista över indextyper eller utelämna att gälla för alla index.

- Standard: `[]`
- Samling

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `indexer:set-status`

```bash
bin/magento indexer:set-status <status> [<index>...]
```

Anger den angivna indexerarstatusen

### Argument

#### `status`

Indexerarens statustyp [är ogiltig|pausad|giltig]

- Krävs


#### `index`

Blankstegsavgränsad lista över indextyper eller utelämna att gälla för alla index.

- Standard: `[]`
- Samling

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `indexer:show-dimensions-mode`

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

Visar dimensionsläge för indexerare

### Argument

#### `indexer`

Blankstegsavgränsad lista med indextyper eller utelämna den för alla index (catalog_product_price,catalogpermissions_category)

- Standard: `[]`
- Samling

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `indexer:show-mode`

```bash
bin/magento indexer:show-mode [<index>...]
```

Visar indexläge

### Argument

#### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`
- Samling

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `indexer:status`

```bash
bin/magento indexer:status [<index>...]
```

Visar indexerarens status

### Argument

#### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`
- Samling

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `info:adminuri`

```bash
bin/magento info:adminuri
```

Visar Magento Admin URI

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `info:backups:list`

```bash
bin/magento info:backups:list
```

Skriver ut lista över tillgängliga säkerhetskopior

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `info:currency:list`

```bash
bin/magento info:currency:list
```

Visar listan över tillgängliga valutor

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `info:dependencies:show-framework`

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

Visar antalet beroenden till Magento-ramverket

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--output`, `-o`

Filens namn för rapporten

- Standard: `framework-dependencies.csv`
- Kräver ett värde


## `info:dependencies:show-modules`

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

Visar antalet beroenden mellan moduler

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--output`, `-o`

Filens namn för rapporten

- Standard: `modules-dependencies.csv`
- Kräver ett värde


## `info:dependencies:show-modules-circular`

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

Visar antal cirkulära beroenden mellan moduler

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--output`, `-o`

Filens namn för rapporten

- Standard: `modules-circular-dependencies.csv`
- Kräver ett värde


## `info:language:list`

```bash
bin/magento info:language:list
```

Visar en lista över tillgängliga språkinställningar

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `info:timezone:list`

```bash
bin/magento info:timezone:list
```

Visar en lista över tillgängliga tidszoner

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `inventory:reservation:create-compensations`

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

Skapa reservationer med angivna kompensationsargument

### Argument

#### `compensations`

Lista över kompensationsargument i formatet &quot;:::&quot;

- Standard: `[]`
- Samling

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--raw`, `-r`

Rå utdata

- Standard: `false`
- Accepterar inte ett värde


## `inventory:reservation:list-inconsistencies`

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

Visa alla order och produkter med inkonsekvenser i försäljningsbar kvantitet

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--complete-orders`, `-c`

Visa endast inkonsekvenser för fullständiga order

- Standard: `false`
- Accepterar inte ett värde

#### `--incomplete-orders`, `-i`

Visa endast inkonsekvenser för ofullständiga order

- Standard: `false`
- Accepterar inte ett värde

#### `--bunch-size`, `-b`

Definierar hur många order som läses in samtidigt

- Standard: `50`
- Accepterar ett värde

#### `--raw`, `-r`

Råutdata

- Standard: `false`
- Accepterar inte ett värde


## `inventory-geonames:import`

```bash
bin/magento inventory-geonames:import <countries>...
```

Hämta och importera geonamn för källvalsalgoritm

### Argument

#### `countries`

Lista över landskoder som ska importeras

- Standard: `[]`
- Obligatoriskt

- Samling

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `maintenance:allow-ips`

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

Ställer in IP-adresser som är undantagna för underhållsläge

### Argument

#### `ip`

Tillåtna IP-adresser

- Standard: `[]`
- Samling

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--none`

Rensa tillåtna IP-adresser

- Standard: `false`
- Accepterar inte ett värde

#### `--add`

Lägg till IP-adressen i den befintliga listan

- Standard: `false`
- Accepterar inte ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento-initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `maintenance:disable`

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Inaktiverar underhållsläge

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--ip`

Tillåtna IP-adresser (använd &#39;none&#39; för att rensa tillåten IP-lista)

- Standard: `[]`
- Kräver ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `maintenance:enable`

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Aktiverar underhållsläge

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--ip`

Tillåtna IP-adresser (använd &#39;none&#39; för att rensa tillåten IP-lista)

- Standard: `[]`
- Kräver ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento-initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `maintenance:status`

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Visar status för underhållsläge

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento-initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `media-content:sync`

```bash
bin/magento media-content:sync
```

Synkronisera innehåll med resurser

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `media-gallery:sync`

```bash
bin/magento media-gallery:sync
```

Synkronisera medielagring och medieresurser i databasen

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `module:config:status`

```bash
bin/magento module:config:status
```

Kontrollerar modulkonfigurationen i filen app/etc/config.php och rapporterar om den är uppdaterad eller inte

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `module:disable`

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Inaktiverar angivna moduler

### Argument

#### `module`

Namn på modulen

- Standard: `[]`
- Array

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--force`, `-f`

Åsidosätt beroendekontroll

- Standard: `false`
- Accepterar inte ett värde

#### `--all`

Inaktivera alla moduler

- Standard: `false`
- Accepterar inte ett värde

#### `--clear-static-content`, `-c`

Rensa genererade statiska vyfiler. Nödvändigt om modulen/modulerna har statiska vyfiler

- Standard: `false`
- Accepterar inte ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `module:enable`

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Aktiverar angivna moduler

### Argument

#### `module`

Namn på modulen

- Standard: `[]`
- Samling

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--force`, `-f`

Kontroll av att kringgå beroenden

- Standard: `false`
- Accepterar inte ett värde

#### `--all`

Aktivera alla moduler

- Standard: `false`
- Accepterar inte ett värde

#### `--clear-static-content`, `-c`

Rensa genererade statiska vyfiler. Om modulerna har statiska visningsfiler krävs

- Standard: `false`
- Accepterar inte ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento-initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `module:status`

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

Visar status för moduler

### Argument

#### `module-names`

Modulnamn (valfritt)

- Standard: `[]`
- Array

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--enabled`

Skriv bara ut aktiverade moduler

- Standard: `false`
- Accepterar inte ett värde

#### `--disabled`

Skriv bara ut inaktiverade moduler

- Standard: `false`
- Accepterar inte ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `module:uninstall`

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

Avinstallerar moduler som installerats av kompositören

### Argument

#### `module`

Modulens namn

- Standard: `[]`
- Obligatoriskt

- Array

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--remove-data`, `-r`

Ta bort data som har installerats av moduler

- Standard: `false`
- Accepterar inte ett värde

#### `--backup-code`

Säkerhetskopiera kod och konfigurationsfiler (förutom temporära filer)

- Standard: `false`
- Accepterar inte ett värde

#### `--backup-media`

Ta en säkerhetskopia av media

- Standard: `false`
- Accepterar inte ett värde

#### `--backup-db`

Utför fullständig säkerhetskopiering av databasen

- Standard: `false`
- Accepterar inte ett värde

#### `--non-composer`

Alla moduler som kommer att finnas här kommer att vara icke-kompositörsbaserade

- Standard: `false`
- Accepterar inte ett värde

#### `--clear-static-content`, `-c`

Rensa genererade statiska vyfiler. Om modulerna har statiska visningsfiler krävs

- Standard: `false`
- Accepterar inte ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento-initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `newrelic:create:deploy-marker`

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

Kontrollera om det finns poster i distributionskön och skapa en lämplig distributionsmarkör.

### Argument

#### `message`

Distribuera meddelande?

- Krävs


#### `change_log`

Ändra logg?

- Krävs


#### `user`

Användare av distribution


#### `revision`

Revision

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `queue:consumers:list`

```bash
bin/magento queue:consumers:list
```

Lista över MessageQueue-konsumenter

```
This command shows list of MessageQueue consumers.
```

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `queue:consumers:restart`

```bash
bin/magento queue:consumers:restart
```

Starta om MessageQueue-konsumenter

```
Command put poison pill for MessageQueue consumers and force to restart them after next status check.
```

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


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

### Argument

#### `consumer`

Namnet på den konsument som ska startas.

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--max-messages`

Antalet meddelanden som ska bearbetas av konsumenten innan processen avslutas. Om inget anges – avsluta när du har bearbetat alla köade meddelanden.

- Kräver ett värde

#### `--batch-size`

Antalet meddelanden per batch. Gäller endast för batchkonsumenten.

- Kräver ett värde

#### `--area-code`

Det föredragna området (globalt, adminhtml, etc...) är som standard globalt.

- Kräver ett värde

#### `--single-thread`

Det här alternativet förhindrar att flera kopior av en kund körs samtidigt.

- Standard: `false`
- Accepterar inte ett värde

#### `--multi-process`

Antalet processer per kund.

- Accepterar ett värde

#### `--pid-file-path`

Filsökvägen för att spara PID (det här alternativet är föråldrat, använd —single-thread i stället)

- Kräver ett värde


## `remote-storage:sync`

```bash
bin/magento remote-storage:sync
```

Synkronisera mediefiler med fjärrlagring.

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `saas:resync`

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync] [--by-ids BY-IDS] [--id-type ID-TYPE]
```

Synkroniserar om flödesdata till SaaS-tjänsten.

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--feed`

Feednamnet ska synkroniseras helt och hållet till SaaS-tjänsten. Tillgängliga feeds: Orderproduktion för betaltjänster, Betalningstjänster ordersandlåda, Orderstatus för betaltjänster, Orderstatus för betaltjänster sandbox, Produktion av betaltjänstbutik, Sandbox för betaltjänstbutik

- Kräver ett värde

#### `--no-reindex`

Kör endast omsändning av feed-data till SaaS-tjänsten. Indexerar inte om. (Detta alternativ gäller inte för produkterna, produkterna, åsidosättningarna, prisflödena)

- Standard: `false`
- Accepterar inte ett värde

#### `--cleanup-feed`

Tvinga rensning av flödesindexerartabellen före synkronisering.

- Standard: `false`
- Accepterar inte ett värde

#### `--dry-run`

Torrkörning. Data kommer inte att exporteras. Om du vill spara nyttolast i loggfilen var/log/saas-export.log kör du med env-variabeln EXPORTER_EXTENDED_LOG=1.

- Standard: `false`
- Accepterar inte ett värde

#### `--thread-count`

Ange antalet synkroniseringstråd.

- Kräver ett värde

#### `--batch-size`

Ange batchstorlek för synkronisering

- Kräver ett värde

#### `--continue-resync`

Fortsätt omsynkronisera från den senast lagrade positionen (det här alternativet gäller för produkterna, produktionsåsidosättningar, prisflöden)

- Standard: `false`
- Accepterar inte ett värde

#### `--by-ids`

Synkronisera om delvis efter en lista över angivna identifierare. (Det här alternativet gäller för flödena produkter, produktåsidosättningar och priser)

- Kräver ett värde

#### `--id-type`

Typ av identifierare för partiell omsynkronisering (till exempel: sku, productId osv.)

- Kräver ett värde


## `sampledata:deploy`

```bash
bin/magento sampledata:deploy [--no-update]
```

Distribuera exempeldatamoduler för kompositörsbaserade Magento-installationer

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--no-update`

Uppdatera composer.json utan att köra composer update

- Standard: `false`
- Accepterar inte ett värde


## `sampledata:remove`

```bash
bin/magento sampledata:remove [--no-update]
```

Ta bort alla exempeldatapaket från Composer.json

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--no-update`

Uppdatera Composer.json utan att köra Composer-uppdatering

- Standard: `false`
- Accepterar inte ett värde


## `sampledata:reset`

```bash
bin/magento sampledata:reset
```

Återställ alla exempeldatamoduler för ominstallation

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `security:recaptcha:disable-for-user-forgot-password`

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

Inaktivera reCAPTCHA för administratörsanvändaren har glömt lösenordsformuläret

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `security:recaptcha:disable-for-user-login`

```bash
bin/magento security:recaptcha:disable-for-user-login
```

Inaktivera reCAPTCHA för inloggningsformulär för administratörsanvändare

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `security:tfa:google:set-secret`

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

Ange hemligheten som används för Google OTP-generering.

### Argument

#### `user`

Användarnamn

- Obligatoriskt


#### `secret`

Hemlighet

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `security:tfa:providers`

```bash
bin/magento security:tfa:providers
```

Visa alla tillgängliga leverantörer

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `security:tfa:reset`

```bash
bin/magento security:tfa:reset <user> <provider>
```

Återställ konfigurationen för en användare

### Argument

#### `user`

Användarnamn

- Obligatoriskt


#### `provider`

Kod för leverantör

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `server:run`

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

Köra programserver

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--port`, `-p`

port att betjäna på

- Standard: `9501`
- Accepterar ett värde

#### `--background`, `-b`

flagga för bakgrundsläge

- Standard: `0`
- Accepterar ett värde

#### `--workerNum`, `-wn`

antal arbetsprocesser att starta

- Standard: `4`
- Accepterar ett värde

#### `--dispatchMode`, `-dm`

läge för att skicka anslutningar till arbetsprocesserna

- Standard: `3`
- Accepterar ett värde

#### `--maxRequests`, `-mr`

max antal begäranden innan arbetsprocessen startas om

- Standard: `10000`
- Accepterar ett värde

#### `--area`, `-a`

programserverområde

- Standard: `graphql`
- Accepterar ett värde

#### `--magento-init-params`, `-mip`

magento bootstrap init parametrar

- Standard: &quot;
- Accepterar ett värde

#### `--maxWaitTime`, `-mwt`

Hur länge ska man vänta på arbetare efter omladdning (t.ex. config ändring) innan du dödar dem

- Standard: `3600`
- Accepterar ett värde

#### `--state-monitor`

Aktivera tillståndsövervakning. Använd endast detta för felsökning av tillståndsproblem!

- Standard: `false`
- Accepterar inte ett värde


## `server:state-monitor:aggregate-output`

```bash
bin/magento server:state-monitor:aggregate-output
```

Aggregerade utdata från tillståndsövervakaren för ApplicationServer

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `setup:backup`

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Säkerhetskopierar Magento programkodbas, media och databas

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--code`

Säkerhetskopiera kod och konfigurationsfiler (förutom temporära filer)

- Standard: `false`
- Accepterar inte ett värde

#### `--media`

Ta en säkerhetskopia av media

- Standard: `false`
- Accepterar inte ett värde

#### `--db`

Utför fullständig säkerhetskopiering av databasen

- Standard: `false`
- Accepterar inte ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento-initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `setup:config:set`

```bash
bin/magento setup:config:set [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Skapar eller ändrar distributionskonfigurationen

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--remote-storage-driver`

Drivrutin för fjärrlagring

- Kräver ett värde

#### `--remote-storage-prefix`

Prefix för fjärrlagring

- Standard: &quot;
- Kräver ett värde

#### `--remote-storage-endpoint`

Slutpunkt för fjärrlagring

- Kräver ett värde

#### `--remote-storage-bucket`

Fjärrlagringsbucket

- Kräver ett värde

#### `--remote-storage-region`

Fjärrlagringsregion

- Kräver ett värde

#### `--remote-storage-key`

Åtkomstnyckel för fjärrlagring

- Standard: &#39;&#39;
- Kräver ett värde

#### `--remote-storage-secret`

Hemlig nyckel för fjärrlagring

- Standard: &quot;
- Kräver ett värde

#### `--remote-storage-path-style`

Stil för fjärrlagringssökväg

- Standard: `0`
- Kräver ett värde

#### `--backend-frontname`

Förnamn för serverdel (genereras automatiskt om det saknas)

- Kräver ett värde

#### `--enable-debug-logging`

Aktivera felsökningsloggning

- Kräver ett värde

#### `--enable-syslog-logging`

Aktivera syslog-loggning

- Kräver ett värde

#### `--id_salt`

GraphQl Salt

- Kräver ett värde

#### `--checkout-async`

Vill du aktivera asynkron orderbearbetning? 1 - Ja, 0 - Nej

- Kräver ett värde

#### `--config-async`

Vill du aktivera Spara async Admin Config? 1 - Ja, 0 - Nej

- Kräver ett värde

#### `--amqp-host`

AMQP-servervärd

- Standard: &quot;
- Kräver ett värde

#### `--amqp-port`

AMQP-serverport

- Standard: `5672`
- Kräver ett värde

#### `--amqp-user`

Användarnamn för AMQP-server

- Standard: &quot;
- Kräver ett värde

#### `--amqp-password`

Lösenord för AMQP-server

- Standard: &#39;&#39;
- Kräver ett värde

#### `--amqp-virtualhost`

Virtualhost för Amqp

- Standard: `/`
- Kräver ett värde

#### `--amqp-ssl`

Amqp SSL

- Standard: &quot;
- Kräver ett värde

#### `--amqp-ssl-options`

Amqp SSL-alternativ (JSON)

- Standard: &#39;&#39;
- Kräver ett värde

#### `--consumers-wait-for-messages`

Ska konsumenterna vänta på ett meddelande från kön? 1 - Ja, 0 - Nej

- Kräver ett värde

#### `--queue-default-connection`

Standardanslutning för Message Queues. Kan vara db, amqp eller ett anpassat kösystem. Kösystemet måste vara installerat och konfigurerat, annars kommer meddelanden inte att behandlas korrekt.

- Kräver ett värde

#### `--deferred-total-calculating`

Vill du aktivera beräkning av uppskjuten totalsumma? 1 - Ja, 0 - Nej

- Kräver ett värde

#### `--key`

Krypteringsnyckel

- Kräver ett värde

#### `--db-host`

Värd för databasserver

- Kräver ett värde

#### `--db-name`

Databasens namn

- Kräver ett värde

#### `--db-user`

Användarnamn för databasserver

- Kräver ett värde

#### `--db-engine`

Motor för databasserver

- Kräver ett värde

#### `--db-password`

Lösenord för databasserver

- Kräver ett värde

#### `--db-prefix`

Prefix för databastabell

- Kräver ett värde

#### `--db-model`

Typ av databas

- Kräver ett värde

#### `--db-init-statements`

Databasens ursprungliga uppsättning kommandon

- Kräver ett värde

#### `--skip-db-validation`, `-s`

Om det anges hoppas db-anslutningsverifieringen över

- Standard: `false`
- Accepterar inte ett värde

#### `--http-cache-hosts`

http Cache-värdar

- Kräver ett värde

#### `--db-ssl-key`

Fullständig sökväg till klientnyckelfilen för att upprätta db-anslutning via SSL

- Standard: &#39;&#39;
- Kräver ett värde

#### `--db-ssl-cert`

Fullständig sökväg till klientcertifikatfilen för att upprätta db-anslutning via SSL

- Standard: &#39;&#39;
- Kräver ett värde

#### `--db-ssl-ca`

Fullständig sökväg till servercertifikatfilen för att upprätta db-anslutning via SSL

- Standard: &#39;&#39;
- Kräver ett värde

#### `--db-ssl-verify`

Verifiera servercertifiering

- Standard: `false`
- Accepterar inte ett värde

#### `--session-save`

Hanterare för sessionssparande

- Kräver ett värde

#### `--session-save-redis-host`

Fullständigt kvalificerat värdnamn, IP-adress eller absolut sökväg om du använder UNIX-socketar

- Kräver ett värde

#### `--session-save-redis-port`

Redis-serverns lyssningsport

- Kräver ett värde

#### `--session-save-redis-password`

Redis-serverlösenord

- Kräver ett värde

#### `--session-save-redis-timeout`

Anslutningens timeout, i sekunder

- Kräver ett värde

#### `--session-save-redis-retries`

Redis-anslutningsförsök.

- Kräver ett värde

#### `--session-save-redis-persistent-id`

Unik sträng för att aktivera beständiga anslutningar

- Kräver ett värde

#### `--session-save-redis-db`

Redis-databasnummer

- Kräver ett värde

#### `--session-save-redis-compression-threshold`

Tröskelvärde för Redis-komprimering

- Kräver ett värde

#### `--session-save-redis-compression-lib`

Redis-komprimeringsbibliotek. Värden: gzip (standard), lzf, lz4, snappy

- Kräver ett värde

#### `--session-save-redis-log-level`

Redis-loggnivå. Värden: 0 (minst utförlig) till 7 (mest utförlig)

- Kräver ett värde

#### `--session-save-redis-max-concurrency`

Maximalt antal processer som kan vänta på ett lås på en session

- Kräver ett värde

#### `--session-save-redis-break-after-frontend`

Antal sekunder att vänta innan du försöker bryta ett lås för klientdelssessionen

- Kräver ett värde

#### `--session-save-redis-break-after-adminhtml`

Antal sekunder att vänta innan ett lås för administratörssessionen bryts

- Kräver ett värde

#### `--session-save-redis-first-lifetime`

Livslängd, i sekunder, för sessionen för icke-robotar vid den första skrivningen (använd 0 för att inaktivera)

- Kräver ett värde

#### `--session-save-redis-bot-first-lifetime`

Livslängd, i sekunder, för sessionen för robotar vid den första skrivningen (använd 0 för att inaktivera)

- Kräver ett värde

#### `--session-save-redis-bot-lifetime`

Sessionens livstid för start vid efterföljande skrivningar (använd 0 för att inaktivera)

- Kräver ett värde

#### `--session-save-redis-disable-locking`

Redis inaktiverar låsning. Värden: false (standard), true

- Kräver ett värde

#### `--session-save-redis-min-lifetime`

Redis-sessionens livstid i sekunder

- Kräver ett värde

#### `--session-save-redis-max-lifetime`

Maximal sessionstid för Redis, i sekunder

- Kräver ett värde

#### `--session-save-redis-sentinel-master`

Redis Sentinel-huvudserver

- Kräver ett värde

#### `--session-save-redis-sentinel-servers`

Redis Sentinel-servrar, kommaseparerade

- Kräver ett värde

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel-verifierad huvudreplik. Värden: false (standard), true

- Kräver ett värde

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel-anslutningsförsök.

- Kräver ett värde

#### `--cache-backend`

Standardhanterare för cache

- Kräver ett värde

#### `--cache-backend-redis-server`

Redis-server

- Kräver ett värde

#### `--cache-backend-redis-db`

Databasnummer för cachen

- Kräver ett värde

#### `--cache-backend-redis-port`

Redis-serverns lyssningsport

- Kräver ett värde

#### `--cache-backend-redis-password`

Lösenord för Redis-server

- Kräver ett värde

#### `--cache-backend-redis-compress-data`

Ställ in på 0 för att inaktivera komprimering (standard är 1, aktiverat)

- Kräver ett värde

#### `--cache-backend-redis-compression-lib`

Komprimeringslib för att använda [snappy,lzf,l4z,zstd,gzip] (lämna tomt för att bestämma automatiskt)

- Kräver ett värde

#### `--cache-backend-redis-use-lua`

Ställ in på 1 för att aktivera lua (standard är 0, inaktiverad)

- Kräver ett värde

#### `--cache-backend-redis-use-lua-on-gc`

Ange 0 om du vill inaktivera plugin-program för skräpinsamling (standardinställningen är 1, aktiverad)

- Kräver ett värde

#### `--cache-id-prefix`

ID-prefix för cachenycklar

- Kräver ett värde

#### `--allow-parallel-generation`

Tillåt generering av cache på ett icke-blockerande sätt

- Standard: `false`
- Accepterar inte ett värde

#### `--page-cache`

Standardhanterare för cache

- Kräver ett värde

#### `--page-cache-redis-server`

Redis-server

- Kräver ett värde

#### `--page-cache-redis-db`

Databasnummer för cachen

- Kräver ett värde

#### `--page-cache-redis-port`

Redis-serverns lyssningsport

- Kräver ett värde

#### `--page-cache-redis-password`

Lösenord för Redis-server

- Kräver ett värde

#### `--page-cache-redis-compress-data`

Ange 1 för att komprimera helsidescachen (använd 0 för att inaktivera)

- Kräver ett värde

#### `--page-cache-redis-compression-lib`

Komprimeringsbibliotek som ska använda [snappy,lzf,l4z,zstd,gzip] (lämna tomt för att avgöra automatiskt)

- Kräver ett värde

#### `--page-cache-id-prefix`

ID-prefix för cachenycklar

- Kräver ett värde

#### `--lock-provider`

Lås leverantörsnamn

- Kräver ett värde

#### `--lock-db-prefix`

Installationsspecifikt låsprefix för att undvika låskonflikter

- Kräver ett värde

#### `--lock-zookeeper-host`

Värd och port för anslutning till Zookeeper-klustret. Till exempel: 127.0.0.1:2181

- Kräver ett värde

#### `--lock-zookeeper-path`

Sökvägen där Zookeeper sparar lås. Standardsökvägen är: /magento/locks

- Kräver ett värde

#### `--lock-file-path`

Sökvägen där fillås sparas.

- Kräver ett värde

#### `--document-root-is-pub`

Flagga som ska visas är Pub är på roten, kan bara vara true eller false

- Kräver ett värde

#### `--backpressure-logger`

Hanterare för mottrycksloggare

- Kräver ett värde

#### `--backpressure-logger-redis-server`

Redis-server

- Kräver ett värde

#### `--backpressure-logger-redis-port`

Redis-serverlyssningsport

- Kräver ett värde

#### `--backpressure-logger-redis-timeout`

Servertimeout för Redis

- Kräver ett värde

#### `--backpressure-logger-redis-persistent`

Redis beständig

- Kräver ett värde

#### `--backpressure-logger-redis-db`

Redis-databasnummer

- Kräver ett värde

#### `--backpressure-logger-redis-password`

Redis-serverlösenord

- Kräver ett värde

#### `--backpressure-logger-redis-user`

Redis-serveranvändare

- Kräver ett värde

#### `--backpressure-logger-id-prefix`

ID-prefix för nycklar

- Kräver ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `setup:db-data:upgrade`

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installerar och uppgraderar data i databasen

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `setup:db-declaration:generate-patch`

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

Generera patch och lägg den i en specifik mapp.

### Argument

#### `module`

Modulens namn

- Obligatoriskt


#### `patch`

Namn på korrigering

- Krävs

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--revertable`

Kontrollera om patchen kan återställas eller inte.

- Standard: `false`
- Accepterar ett värde

#### `--type`

Ta reda på vilken typ av korrigering som ska skapas. Tillgängliga värden: `data`, `schema`.

- Standard: `data`
- Accepterar ett värde


## `setup:db-declaration:generate-whitelist`

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

Generera vitlista över tabeller och kolumner som kan redigeras av deklarationsinstallationsprogrammet

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--module-name`

Namnet på modulen där vitlistan ska genereras

- Standard: `all`
- Accepterar ett värde


## `setup:db-schema:add-slave`

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Flytta kassaoffertrelaterade tabeller till en separat DB-server

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--host`

Slav DB-servervärd

- Standard: `localhost`
- Kräver ett värde

#### `--dbname`

Namn på slavdatabas

- Kräver ett värde

#### `--username`

Slave DB-användarnamn

- Standard: `root`
- Kräver ett värde

#### `--password`

Användarlösenord för slavdatabas

- Accepterar ett värde

#### `--connection`

Namn på slavanslutning

- Standard: `default`
- Accepterar ett värde

#### `--resource`

Namn på slavresurs

- Standard: `default`
- Accepterar ett värde

#### `--maxAllowedLag`

Max tillåten fördröjning slavanslutning (i sekunder)

- Standard: &#39;&#39;
- Accepterar ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento-initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `setup:db-schema:split-quote`

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Flytta tabeller relaterade till utcheckningsofferter till en separat databasserver. Föråldrad sedan 2.4.2 och kommer att tas bort

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--host`

Checkout DB Server-värd

- Kräver ett värde

#### `--dbname`

Namn på utcheckningsdatabas

- Kräver ett värde

#### `--username`

Användarnamn för utcheckning av databas

- Kräver ett värde

#### `--password`

Checkout-användarlösenord för DB

- Accepterar ett värde

#### `--connection`

Anslutningsnamn för utcheckning

- Standard: `checkout`
- Accepterar ett värde

#### `--resource`

Utcheckningsresursnamn

- Standard: `checkout`
- Accepterar ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `setup:db-schema:split-sales`

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Flytta försäljningsrelaterade register till en separat databasserver. Borttagen sedan 2.4.2 och kommer att tas bort

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--host`

Sales DB Server-värd

- Kräver ett värde

#### `--dbname`

Namn på försäljningsdatabas

- Kräver ett värde

#### `--username`

Användarnamn för försäljningsdatabas

- Kräver ett värde

#### `--password`

Passowrd för Sales DB-användare

- Accepterar ett värde

#### `--connection`

Namn på försäljningsanslutning

- Standard: `sales`
- Accepterar ett värde

#### `--resource`

Namn på försäljningsresurs

- Standard: `sales`
- Accepterar ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `setup:db-schema:upgrade`

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installerar och uppgraderar DB-schemat

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--convert-old-scripts`

Gör det möjligt att konvertera gamla skript (InstallSchema, UpgradeSchema) till db_schema.xml format

- Standard: `false`
- Accepterar ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento-initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `setup:db:status`

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Kontrollerar om DB-schemat eller data kräver uppgradering

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento-initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `setup:di:compile`

```bash
bin/magento setup:di:compile
```

Genererar DI-konfiguration och alla saknade klasser som kan genereras automatiskt

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `setup:install`

```bash
bin/magento setup:install [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installerar Magento-programmet

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--remote-storage-driver`

Drivrutin för fjärrlagring

- Kräver ett värde

#### `--remote-storage-prefix`

Prefix för fjärrlagring

- Standard: &#39;&#39;
- Kräver ett värde

#### `--remote-storage-endpoint`

Slutpunkt för fjärrlagring

- Kräver ett värde

#### `--remote-storage-bucket`

Bucket för fjärrlagring

- Kräver ett värde

#### `--remote-storage-region`

Område för fjärrlagring

- Kräver ett värde

#### `--remote-storage-key`

Åtkomstnyckel för fjärrlagring

- Standard: &quot;
- Kräver ett värde

#### `--remote-storage-secret`

Hemlig nyckel för fjärrlagring

- Standard: &#39;&#39;
- Kräver ett värde

#### `--remote-storage-path-style`

Sökvägsformat för fjärrlagring

- Standard: `0`
- Kräver ett värde

#### `--backend-frontname`

Förnamn för serverdel (genereras automatiskt om det saknas)

- Kräver ett värde

#### `--enable-debug-logging`

Aktivera felsökningsloggning

- Kräver ett värde

#### `--enable-syslog-logging`

Aktivera syslog-loggning

- Kräver ett värde

#### `--id_salt`

GraphQl Salt

- Kräver ett värde

#### `--checkout-async`

Vill du aktivera asynkron orderbearbetning? 1 - Ja, 0 - Nej

- Kräver ett värde

#### `--config-async`

Vill du aktivera Spara async Admin Config? 1 - Ja, 0 - Nej

- Kräver ett värde

#### `--amqp-host`

AMQP-servervärd

- Standard: &quot;
- Kräver ett värde

#### `--amqp-port`

AMQP-serverport

- Standard: `5672`
- Kräver ett värde

#### `--amqp-user`

Användarnamn för AMQP-server

- Standard: &quot;
- Kräver ett värde

#### `--amqp-password`

Lösenord för Amqp-server

- Standard: &quot;
- Kräver ett värde

#### `--amqp-virtualhost`

Virtualhost för Amqp

- Standard: `/`
- Kräver ett värde

#### `--amqp-ssl`

Amqp SSL

- Standard: &#39;&#39;
- Kräver ett värde

#### `--amqp-ssl-options`

Amqp SSL-alternativ (JSON)

- Standard: &quot;
- Kräver ett värde

#### `--consumers-wait-for-messages`

Ska konsumenterna vänta på ett meddelande från kön? 1 - Ja, 0 - Nej

- Kräver ett värde

#### `--queue-default-connection`

Standardanslutning för meddelandeköer. Kan vara db, amqp eller ett anpassat kösystem. Kösystemet måste vara installerat och konfigurerat, annars kommer meddelanden inte att behandlas korrekt.

- Kräver ett värde

#### `--deferred-total-calculating`

Vill du aktivera fördröjd total beräkning? 1 - Ja, 0 - Nej

- Kräver ett värde

#### `--key`

Krypteringsnyckel

- Kräver ett värde

#### `--db-host`

Databasservervärd

- Kräver ett värde

#### `--db-name`

Databasnamn

- Kräver ett värde

#### `--db-user`

Användarnamn för databasserver

- Kräver ett värde

#### `--db-engine`

Databasservermotor

- Kräver ett värde

#### `--db-password`

Lösenord för databasserver

- Kräver ett värde

#### `--db-prefix`

Prefix för databastabell

- Kräver ett värde

#### `--db-model`

Typ av databas

- Kräver ett värde

#### `--db-init-statements`

Databasens ursprungliga uppsättning kommandon

- Kräver ett värde

#### `--skip-db-validation`, `-s`

Om det anges hoppas validering av databasanslutning över

- Standard: `false`
- Accepterar inte ett värde

#### `--http-cache-hosts`

http-cachevärdar

- Kräver ett värde

#### `--db-ssl-key`

Fullständig sökväg till klientnyckelfilen för att upprätta en databasanslutning via SSL

- Standard: &quot;
- Kräver ett värde

#### `--db-ssl-cert`

Fullständig sökväg till klientcertifikatfilen för att upprätta en databasanslutning via SSL

- Standard: &quot;
- Kräver ett värde

#### `--db-ssl-ca`

Fullständig sökväg till servercertifikatfilen för att upprätta en databasanslutning via SSL

- Standard: &quot;
- Kräver ett värde

#### `--db-ssl-verify`

Verifiera servercertifiering

- Standard: `false`
- Accepterar inte ett värde

#### `--session-save`

Hanterare för sessionssparande

- Kräver ett värde

#### `--session-save-redis-host`

Fullständigt kvalificerat värdnamn, IP-adress eller absolut sökväg om UNIX-socketar används

- Kräver ett värde

#### `--session-save-redis-port`

Redis-serverlyssningsport

- Kräver ett värde

#### `--session-save-redis-password`

Lösenord för Redis-server

- Kräver ett värde

#### `--session-save-redis-timeout`

Anslutningens timeout, i sekunder

- Kräver ett värde

#### `--session-save-redis-retries`

Redis-anslutningsförsök.

- Kräver ett värde

#### `--session-save-redis-persistent-id`

Unik sträng för att aktivera beständiga anslutningar

- Kräver ett värde

#### `--session-save-redis-db`

Redis-databasnummer

- Kräver ett värde

#### `--session-save-redis-compression-threshold`

Tröskelvärde för Redis-komprimering

- Kräver ett värde

#### `--session-save-redis-compression-lib`

Redis-komprimeringsbibliotek. Värden: gzip (standard), lzf, lz4, snappy

- Kräver ett värde

#### `--session-save-redis-log-level`

Redis-loggnivå. Värden: 0 (minst utförlig) till 7 (mest utförlig)

- Kräver ett värde

#### `--session-save-redis-max-concurrency`

Maximalt antal processer som kan vänta på ett lås i en session

- Kräver ett värde

#### `--session-save-redis-break-after-frontend`

Antal sekunder att vänta innan ett lås för en klientsession bryts

- Kräver ett värde

#### `--session-save-redis-break-after-adminhtml`

Antal sekunder att vänta innan ett lås för administratörssessionen bryts

- Kräver ett värde

#### `--session-save-redis-first-lifetime`

Livstid, i sekunder, för session för icke-bots vid första skrivning (använd 0 för att inaktivera)

- Kräver ett värde

#### `--session-save-redis-bot-first-lifetime`

Livstid, i sekunder, för session för bots vid första skrivning (använd 0 för att inaktivera)

- Kräver ett värde

#### `--session-save-redis-bot-lifetime`

Sessionens livstid för start vid efterföljande skrivningar (använd 0 för att inaktivera)

- Kräver ett värde

#### `--session-save-redis-disable-locking`

Redis inaktiverar låsning. Värden: false (standard), true

- Kräver ett värde

#### `--session-save-redis-min-lifetime`

Redis-sessionens livstid i sekunder

- Kräver ett värde

#### `--session-save-redis-max-lifetime`

Maximal sessionstid för Redis, i sekunder

- Kräver ett värde

#### `--session-save-redis-sentinel-master`

Redis Sentinel master

- Kräver ett värde

#### `--session-save-redis-sentinel-servers`

Redis Sentinel-servrar, kommaseparerade

- Kräver ett värde

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel-verifierad huvudreplik. Värden: false (standard), true

- Kräver ett värde

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel-anslutningsförsök.

- Kräver ett värde

#### `--cache-backend`

Standardhanterare för cache

- Kräver ett värde

#### `--cache-backend-redis-server`

Redis-server

- Kräver ett värde

#### `--cache-backend-redis-db`

Databasnummer för cachen

- Kräver ett värde

#### `--cache-backend-redis-port`

Redis-serverlyssningsport

- Kräver ett värde

#### `--cache-backend-redis-password`

Lösenord för Redis-server

- Kräver ett värde

#### `--cache-backend-redis-compress-data`

Ställ in på 0 för att inaktivera komprimering (standard är 1, aktiverat)

- Kräver ett värde

#### `--cache-backend-redis-compression-lib`

Komprimeringslib för att använda [snappy,lzf,l4z,zstd,gzip] (lämna tomt för att bestämma automatiskt)

- Kräver ett värde

#### `--cache-backend-redis-use-lua`

Ställ in på 1 för att aktivera lua (standard är 0, inaktiverad)

- Kräver ett värde

#### `--cache-backend-redis-use-lua-on-gc`

Ställ in på 0 för att inaktivera lua vid skräpinsamling (standard är 1, aktiverat)

- Kräver ett värde

#### `--cache-id-prefix`

ID-prefix för cachenycklar

- Kräver ett värde

#### `--allow-parallel-generation`

Tillåt generering av cache på ett icke-blockerande sätt

- Standard: `false`
- Accepterar inte ett värde

#### `--page-cache`

Standardhanterare för cache

- Kräver ett värde

#### `--page-cache-redis-server`

Redis-server

- Kräver ett värde

#### `--page-cache-redis-db`

Databasnummer för cachen

- Kräver ett värde

#### `--page-cache-redis-port`

Redis-serverns lyssningsport

- Kräver ett värde

#### `--page-cache-redis-password`

Lösenord för Redis-server

- Kräver ett värde

#### `--page-cache-redis-compress-data`

Ställ in på 1 för att komprimera hela sidans cache (använd 0 för att inaktivera)

- Kräver ett värde

#### `--page-cache-redis-compression-lib`

Komprimeringsbibliotek för att använda [snappy,lzf,l4z,zstd,gzip] (lämna tomt för att bestämma automatiskt)

- Kräver ett värde

#### `--page-cache-id-prefix`

ID-prefix för cachenycklar

- Kräver ett värde

#### `--lock-provider`

Namn på låsprovider

- Kräver ett värde

#### `--lock-db-prefix`

Installationsspecifikt låsprefix för att undvika låskonflikter

- Kräver ett värde

#### `--lock-zookeeper-host`

Värd och port för att ansluta till Zookeeper-klustret. Till exempel: 127.0.0.1:2181

- Kräver ett värde

#### `--lock-zookeeper-path`

Stigen där Zookeeper kommer att spara lås. Standardsökvägen är: /magento/locks

- Kräver ett värde

#### `--lock-file-path`

Sökvägen där fillåsen ska sparas.

- Kräver ett värde

#### `--document-root-is-pub`

Flaggan som ska visas är att Pub är på roten, kan endast vara sant eller falskt

- Kräver ett värde

#### `--backpressure-logger`

Hanterare för mottryckslogger

- Kräver ett värde

#### `--backpressure-logger-redis-server`

Redis-server

- Kräver ett värde

#### `--backpressure-logger-redis-port`

Redis-serverns lyssningsport

- Kräver ett värde

#### `--backpressure-logger-redis-timeout`

Tidsgräns för Redis-server

- Kräver ett värde

#### `--backpressure-logger-redis-persistent`

Redis beständig

- Kräver ett värde

#### `--backpressure-logger-redis-db`

Redis db-nummer

- Kräver ett värde

#### `--backpressure-logger-redis-password`

Lösenord för Redis-server

- Kräver ett värde

#### `--backpressure-logger-redis-user`

Användare av Redis-server

- Kräver ett värde

#### `--backpressure-logger-id-prefix`

ID-prefix för nycklar

- Kräver ett värde

#### `--base-url`

URL som butiken ska vara tillgänglig på. Föråldrad, använd config:set med sökväg web/unsecure/base_url

- Kräver ett värde

#### `--language`

Standardspråkkod. Inaktuell, använd config:set med sökväg general/locale/code

- Kräver ett värde

#### `--timezone`

Standardkod för tidszon. Föråldrad, använd config:set med sökvägen allmänt/språk/tidszon

- Kräver ett värde

#### `--currency`

Standardvalutakod. Föråldrad, använd config:set med sökvägen currency/options/base, currency/options/default och currency/options/allow

- Kräver ett värde

#### `--use-rewrites`

Använd omskrivningar. Inaktuell, använd config:set med sökväg web/seo/use_rewrites

- Kräver ett värde

#### `--use-secure`

Använd säkra URL:er. Aktivera bara det här alternativet om SSL är tillgängligt. Föråldrad, använd config:set med sökväg web/secure/use_in_frontend

- Kräver ett värde

#### `--base-url-secure`

Bas-URL för SSL-anslutning. Inaktuell, använd config:set med sökvägen web/secure/base_url

- Kräver ett värde

#### `--use-secure-admin`

Kör administratörsgränssnitt med SSL. Inaktuell, använd config:set med sökvägen web/secure/use_in_adminhtml

- Kräver ett värde

#### `--admin-use-security-key`

Om du vill använda en &quot;säkerhetsnyckel&quot;-funktion i Magento Admin URL:er och formulär. Föråldrad, använd config:set med sökvägen admin/security/use_form_key

- Kräver ett värde

#### `--admin-user`

Admin-användare

- Accepterar ett värde

#### `--admin-password`

Administratörslösenord

- Accepterar ett värde

#### `--admin-email`

E-postadress för administratör

- Accepterar ett värde

#### `--admin-firstname`

Administratörens förnamn

- Accepterar ett värde

#### `--admin-lastname`

Administratörens efternamn

- Accepterar ett värde

#### `--search-engine`

Sökmotor. Värden: elasticsearch8, opensearch

- Kräver ett värde

#### `--elasticsearch-host`

Elasticsearch servervärd.

- Kräver ett värde

#### `--elasticsearch-port`

Elasticsearch serverport.

- Kräver ett värde

#### `--elasticsearch-enable-auth`

Ange 1 för att aktivera autentisering. (standard är 0, inaktiverad)

- Kräver ett värde

#### `--elasticsearch-username`

Användarnamn för Elasticsearch. Gäller endast om HTTP-autentisering är aktiverat

- Kräver ett värde

#### `--elasticsearch-password`

Elasticsearch-lösenord. Gäller endast om HTTP-autentisering är aktiverat

- Kräver ett värde

#### `--elasticsearch-index-prefix`

Elasticsearch indexprefix.

- Kräver ett värde

#### `--elasticsearch-timeout`

Tidsgräns för Elasticsearch-server.

- Kräver ett värde

#### `--opensearch-host`

OpenSearch server värd.

- Kräver ett värde

#### `--opensearch-port`

OpenSearch serverport.

- Kräver ett värde

#### `--opensearch-enable-auth`

Ställ in på 1 för att aktivera autentisering. (standard är 0, inaktiverad)

- Kräver ett värde

#### `--opensearch-username`

OpenSearch användarnamn. Gäller endast om HTTP-autentisering är aktiverat

- Kräver ett värde

#### `--opensearch-password`

OpenSearch-lösenord. Gäller endast om HTTP-autentisering är aktiverat

- Kräver ett värde

#### `--opensearch-index-prefix`

Index för OpenSearch.

- Kräver ett värde

#### `--opensearch-timeout`

Tidsgräns för OpenSearch-server.

- Kräver ett värde

#### `--cleanup-database`

Rensa databasen före installationen

- Standard: `false`
- Accepterar inte ett värde

#### `--sales-order-increment-prefix`

Prefix för försäljningsordernummer

- Kräver ett värde

#### `--use-sample-data`

Använd exempeldata

- Standard: `false`
- Accepterar inte ett värde

#### `--enable-modules`

Lista över kommaavgränsade modulnamn. Det måste ingå under installationen. Tillgängliga magiska param &quot;all&quot;.

- Accepterar ett värde

#### `--disable-modules`

Lista med kommaavgränsade modulnamn. Detta måste undvikas under installationen. Tillgängliga magiska param &quot;all&quot;.

- Accepterar ett värde

#### `--convert-old-scripts`

Tillåter konvertering av gamla skript (InstallSchema, UpgradeSchema) till formatet db_schema.xml

- Standard: `false`
- Accepterar ett värde

#### `--interactive`, `-i`

Interaktiv installation av Magento

- Standard: `false`
- Accepterar inte ett värde

#### `--safe-mode`

Säker installation av Magento med dumpar vid destruktiva åtgärder, som borttagning av spalter

- Accepterar ett värde

#### `--data-restore`

Återställ borttagna data från dumpar

- Accepterar ett värde

#### `--dry-run`

Magento-installationen körs i torrt läge

- Standard: `false`
- Accepterar ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `setup:performance:generate-fixtures`

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

Skapar korrigeringar

### Argument

#### `profile`

Sökväg till profilkonfigurationsfilen

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--skip-reindex`, `-s`

Hoppa över omindexering

- Standard: `false`
- Accepterar inte ett värde


## `setup:rollback`

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Återställer Magento-applikationens kodbas, media och databas

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--code-file`, `-c`

Basnamn för kodsäkerhetskopian i var/backups

- Kräver ett värde

#### `--media-file`, `-m`

Basnamn för mediesäkerhetskopieringsfilen i var/backups

- Kräver ett värde

#### `--db-file`, `-d`

Basnamn för db-säkerhetskopian i var/backups

- Kräver ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento-initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `setup:static-content:deploy`

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

Distribuerar statiska vyfiler

### Argument

#### `languages`

Blankstegsavgränsad lista med ISO-639-språkkoder som statiska vyfiler ska skrivas ut för.

- Standard: `[]`
- Array

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--force`, `-f`

Distribuera filer i valfritt läge.

- Standard: `false`
- Accepterar inte ett värde

#### `--strategy`, `-s`

Distribuera filer med hjälp av angiven strategi.

- Standard: `quick`
- Accepterar ett värde

#### `--area`, `-a`

Generera filer endast för de angivna områdena.

- Standard: `all`
- Accepterar flera värden

#### `--exclude-area`

Generera inga filer för de angivna områdena.

- Standard: `none`
- Accepterar flera värden

#### `--theme`, `-t`

Generera statiska vyfiler för endast de angivna temana.

- Standard: `all`
- Accepterar flera värden

#### `--exclude-theme`

Generera inte filer för de angivna temana.

- Standard: `none`
- Accepterar flera värden

#### `--language`, `-l`

Generera endast filer för de angivna språken.

- Standard: `all`
- Accepterar flera värden

#### `--exclude-language`

Generera inte filer för de angivna språken.

- Standard: `none`
- Accepterar flera värden

#### `--jobs`, `-j`

Aktivera parallell bearbetning med angivet antal jobb.

- Standard: `0`
- Accepterar ett värde

#### `--max-execution-time`

Maximal förväntad körningstid för den statiska distributionsprocessen (i sekunder).

- Standard: `900`
- Accepterar ett värde

#### `--symlink-locale`

Skapa symboliska länkar för filerna i dessa språk, som skickas för distribution, men som inte har några anpassningar.

- Standard: `false`
- Accepterar inte ett värde

#### `--content-version`

Anpassad version av statiskt innehåll kan användas om du kör distribution på flera noder för att säkerställa att versionen av statiskt innehåll är identisk och att cachelagringen fungerar korrekt.

- Kräver ett värde

#### `--refresh-content-version-only`

Om du bara uppdaterar versionen av statiskt innehåll kan du uppdatera statiskt innehåll i webbläsarens cache och CDN-cache.

- Standard: `false`
- Accepterar inte ett värde

#### `--no-javascript`

Distribuera inte JavaScript-filer.

- Standard: `false`
- Accepterar inte ett värde

#### `--no-js-bundle`

Distribuera inte JavaScript paketfiler.

- Standard: `false`
- Accepterar inte ett värde

#### `--no-css`

Distribuera inte CSS-filer.

- Standard: `false`
- Accepterar inte ett värde

#### `--no-less`

Distribuera inte LESS-filer.

- Standard: `false`
- Accepterar inte ett värde

#### `--no-images`

Distribuera inte avbildningar.

- Standard: `false`
- Accepterar inte ett värde

#### `--no-fonts`

Distribuera inte teckensnittsfiler.

- Standard: `false`
- Accepterar inte ett värde

#### `--no-html`

Distribuera inte HTML-filer.

- Standard: `false`
- Accepterar inte ett värde

#### `--no-misc`

Distribuera inte filer av andra typer (.md, .jbf, .csv osv.).

- Standard: `false`
- Accepterar inte ett värde

#### `--no-html-minify`

Minifiera inte HTML-filer.

- Standard: `false`
- Accepterar inte ett värde

#### `--no-parent`

Kompilera inte överordnade teman. Stöds endast i snabb- och standardstrategier.

- Standard: `false`
- Accepterar inte ett värde


## `setup:store-config:set`

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installerar butikskonfigurationen. Föråldrad sedan 2.2.0. Använd config:set istället

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--base-url`

URL som butiken ska vara tillgänglig på. Föråldrad, använd config:set med sökväg web/unsecure/base_url

- Kräver ett värde

#### `--language`

Standardspråkkod. Föråldrad, använd config:set med sökvägen allmänt/språk/kod

- Kräver ett värde

#### `--timezone`

Standardkod för tidszon. Föråldrad, använd config:set med sökvägen allmänt/språk/tidszon

- Kräver ett värde

#### `--currency`

Standardvalutakod. Föråldrad, använd config:set med sökvägen currency/options/base, currency/options/default och currency/options/allow

- Kräver ett värde

#### `--use-rewrites`

Använd omskrivningar. Föråldrad, använd config:set med sökväg web/seo/use_rewrites

- Kräver ett värde

#### `--use-secure`

Använd säkra webbadresser. Aktivera bara det här alternativet om SSL är tillgängligt. Föråldrad, använd config:set med sökväg web/secure/use_in_frontend

- Kräver ett värde

#### `--base-url-secure`

Bas-URL för SSL-anslutning. Föråldrad, använd config:set med sökväg web/secure/base_url

- Kräver ett värde

#### `--use-secure-admin`

Kör administratörsgränssnittet med SSL. Inaktuell, använd config:set med sökvägen web/secure/use_in_adminhtml

- Kräver ett värde

#### `--admin-use-security-key`

Om en säkerhetsnyckel ska användas i Magento Admin URL:er och formulär. Inaktuell, använd config:set med sökvägsadministratör/säkerhet/use_form_key

- Kräver ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `setup:uninstall`

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

Avinstallerar Magento-programmet

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento-initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `setup:upgrade`

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Uppgraderar Magento-applikationen, DB-data och schemat

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--keep-generated`

Förhindrar att genererade filer tas bort. Vi avråder från att använda det här alternativet förutom när du distribuerar till produktion. Kontakta din systemintegrerare eller administratör om du vill ha mer information.

- Standard: `false`
- Accepterar inte ett värde

#### `--convert-old-scripts`

Tillåter konvertering av gamla skript (InstallSchema, UpgradeSchema) till formatet db_schema.xml

- Standard: `false`
- Accepterar ett värde

#### `--safe-mode`

Säker installation av Magento med dumpar vid destruktiva åtgärder, som borttagning av spalter

- Accepterar ett värde

#### `--data-restore`

Återställa borttagna data från dumpar

- Accepterar ett värde

#### `--dry-run`

Magento Installation kommer att köras i torrkörningsläge

- Standard: `false`
- Accepterar ett värde

#### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa Magento-initieringsparametrar Till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Kräver ett värde


## `store:list`

```bash
bin/magento store:list
```

Visar listan över butiker

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `store:website:list`

```bash
bin/magento store:website:list
```

Visar en lista över webbplatser

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `support:backup:code`

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

Skapa en säkerhetskopia av kod

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--name`

Namn på dump

- Accepterar ett värde

#### `--output`, `-o`

Utdatasökväg

- Accepterar ett värde

#### `--logs`, `-l`

Inkludera loggar

- Standard: `false`
- Accepterar inte ett värde


## `support:backup:db`

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

Skapa DB-säkerhetskopiering

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--name`

Namn på dump

- Accepterar ett värde

#### `--output`, `-o`

Sökväg för utdata

- Accepterar ett värde

#### `--logs`, `-l`

Inkludera loggar

- Standard: `false`
- Accepterar inte ett värde

#### `--ignore-sanitize`, `-i`

Ignorera sanera

- Standard: `false`
- Accepterar inte ett värde


## `support:utility:check`

```bash
bin/magento support:utility:check [--hide-paths]
```

Kontrollera nödvändiga säkerhetskopieringsverktyg

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--hide-paths`

Kontrollera endast nödvändiga konsolverktyg

- Standard: `false`
- Accepterar inte ett värde


## `support:utility:paths`

```bash
bin/magento support:utility:paths [-f|--force]
```

Skapa verktygssökvägslista

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--force`, `-f`

Tvinga

- Standard: `false`
- Accepterar inte ett värde


## `theme:uninstall`

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

Avinstallerar tema

### Argument

#### `theme`

Sökväg till temat. Temasökvägen ska anges som fullständig sökväg, vilket är område/leverantör/namn. Till exempel front/Magento/blank

- Standard: `[]`
- Obligatoriskt

- Samling

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).

#### `--backup-code`

Säkerhetskopiera kod (förutom tillfälliga filer)

- Standard: `false`
- Accepterar inte ett värde

#### `--clear-static-content`, `-c`

Rensa genererade statiska vyfiler.

- Standard: `false`
- Accepterar inte ett värde


## `varnish:vcl:generate`

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

Skapar lack VCL och lägger det på kommandoraden

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--access-list`

IP-åtkomstlista som kan rensa engelska

- Standard: `localhost`
- Kräver ett värde

#### `--backend-host`

Värd för webbserverdelen

- Standard: `localhost`
- Kräver ett värde

#### `--backend-port`

Port för webbserverdelen

- Standard: `8080`
- Kräver ett värde

#### `--export-version`

Versionen av Varnish-filen

- Standard: `6`
- Kräver ett värde

#### `--grace-period`

Behåll programmet i sekunder

- Standard: `300`
- Kräver ett värde

#### `--input-file`

Indatafil att generera cl från

- Kräver ett värde

#### `--output-file`

Sökväg till filen som ska skrivas vcl

- Kräver ett värde


## `webhooks:dev:run`

```bash
bin/magento webhooks:dev:run <name> <payload>
```

Kör en registrerad webkrok i utvecklingssyfte.

### Argument

#### `name`

Webkrocksnamn

- Obligatoriskt


#### `payload`

Webkroknyttolasten i JSON-format

- Obligatoriskt

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).


## `webhooks:generate:module`

```bash
bin/magento webhooks:generate:module
```

Generera plugin-program baserat på webhook-registreringar

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `webhooks:info`

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```

Returnerar nyttolasten för den angivna webhooken.

### Argument

#### `webhook-name`

Namn på webkrockmetod

- Obligatoriskt


#### `webhook-type`

Webkrotyp (före, efter)

- Standard: `before`

### Alternativ

Information om globala alternativ finns i [Globala alternativ](#global-options).

#### `--depth`

Antalet nivåer i webkroks nyttolast som ska returneras

- Standard: `3`
- Accepterar ett värde


## `webhooks:list`

```bash
bin/magento webhooks:list
```

Visar en lista över webbhookar som prenumererar

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).


## `webhooks:list:all`

```bash
bin/magento webhooks:list:all <module_name>
```

Returnerar en lista över namn på webhook-metoder som stöds för den angivna modulen

### Argument

#### `module_name`

Modulens namn

- Krävs

### Alternativ

För globala alternativ, se [Globala alternativ](#global-options).
