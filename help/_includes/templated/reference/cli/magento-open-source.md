---
source-git-commit: a5777f437430bc48b87aaea65c0e101d4ecd6574
workflow-type: tm+mt
source-wordcount: '14684'
ht-degree: 0%

---
# bin/magento (Magento Open Source)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Version**: 2.4.5 <!-- app.version -->

Referensen innehåller 111 kommandon som är tillgängliga via `bin/magento` kommandoradsverktyg.
Den inledande listan genereras automatiskt med `bin/magento list` i utgåvan.
Använd [&quot;Lägg till CLI-kommandon&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) för att lägga till ett eget CLI-kommando.

>[!NOTE]
>
>Du kan ringa `bin/magento` CLI-kommandon som använder genvägar i stället för det fullständiga kommandonamnet. Du kan till exempel ringa `bin/magento setup:upgrade` använda `bin/magento s:up`, `bin/magento s:upg`. Se [genvägssyntax](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) för att förstå hur du använder kortkommandon med valfritt CLI-kommando.

>[!NOTE]
>
>Den här referensen genereras från programmets kodbas. Om du vill ändra innehållet kan du uppdatera källkoden för motsvarande kommandoimplementering i [kodbas](https://github.com/magento) arkivera och skicka in dina ändringar för granskning. Ett annat sätt är att _Ge oss feedback_ (hitta länken i det övre högra hörnet). Information om riktlinjer för bidrag finns i [Kodavgifter](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `help`

Visa hjälp för ett kommando

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `list`

Listkommandon

```bash
bin/magento list [--raw] [--format FORMAT] [--] [<namespace>]
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

## `admin:adobe-ims:disable`

Inaktivera Adobe IMS-modul

```bash
bin/magento admin:adobe-ims:disable
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `admin:adobe-ims:enable`

Aktivera Adobe IMS-modulen.

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `admin:adobe-ims:info`

Information om konfigurationen av Adobe IMS-modulen

```bash
bin/magento admin:adobe-ims:info
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `admin:adobe-ims:status`

Status för Adobe IMS-modul

```bash
bin/magento admin:adobe-ims:status
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `admin:user:create`

Skapar en administratör

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `admin:user:unlock`

Lås upp administratörskonto

```bash
bin/magento admin:user:unlock <username>
```

<!-- app.name --> <!-- command.usage -->

### `username`

Administratörens användarnamn som ska låsas upp
- Obligatoriskt

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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `app:config:dump`

Skapa programdump

```bash
bin/magento app:config:dump [<config-types>...]
```

<!-- app.name --> <!-- command.usage -->

### `config-types`

Blankstegsavgränsad lista med konfigurationstyper eller utelämna att dumpa alla [omfång, teman, system, i18n]

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `app:config:import`

Importera data från delade konfigurationsfiler till lämplig datalagring

```bash
bin/magento app:config:import
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `app:config:status`

Kontrollerar om konfigurationsspridning kräver uppdatering

```bash
bin/magento app:config:status
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `braintree:migrate`

Migrera lagrade kort från en Magento 1-databas

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `cache:clean`

Rensar cachetyper

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Blankstegsavgränsad lista med cachetyper eller utelämna att använda för alla cachetyper.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

lägga till eller åsidosätta parametrar för bootstrap
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `cache:disable`

Inaktiverar cachetyp(er)

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Blankstegsavgränsad lista med cachetyper eller utelämna att använda för alla cachetyper.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

lägga till eller åsidosätta parametrar för bootstrap
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `cache:enable`

Aktiverar cachetyp(er)

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Blankstegsavgränsad lista med cachetyper eller utelämna att använda för alla cachetyper.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

lägga till eller åsidosätta parametrar för bootstrap
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `cache:flush`

Tömmer cache-lagring som används av cachetyper

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Blankstegsavgränsad lista med cachetyper eller utelämna att använda för alla cachetyper.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

lägga till eller åsidosätta parametrar för bootstrap
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `cache:status`

Kontrollerar cachestatus

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--bootstrap`

lägga till eller åsidosätta parametrar för bootstrap
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `catalog:images:resize`

Skapar storleksändrade produktbilder

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--async`, `-a`



Ändra storlek på bild i asynkront läge
- Standard: `false`
- Accepterar inte ett värde


### `--skip_hidden_images`

Bearbeta inte bilder som markerats som dolda från produktsidan
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `catalog:product:attributes:cleanup`

Tar bort oanvända produktattribut.

```bash
bin/magento catalog:product:attributes:cleanup
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `cms:wysiwyg:restrict`

Ange om innehållsvalidering från HTML ska framtvingas eller om en varning ska visas i stället

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

<!-- app.name --> <!-- command.usage -->

### `restrict`

y\n
- Obligatoriskt

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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `config:sensitive:set`

Ange känsliga konfigurationsvärden

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Konfigurationssökväg för exempelvis grupp/avsnitt/fältnamn
<!-- argument -->

### `value`

Konfigurationsvärde
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `config:set`

Ändra systemkonfiguration

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

<!-- app.name --> <!-- command.usage -->

### `path`

Konfigurationssökväg i formatavsnitt/grupp/fältnamn
- Obligatoriskt

   <!-- argument -->

### `value`

Konfigurationsvärde
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `config:show`

Visar konfigurationsvärde för angiven sökväg. Om ingen sökväg anges visas alla sparade värden

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Konfigurationssökväg, till exempel section_id/group_id/field_id
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--scope`

Om inget konfigurationsområde anges används standardomfånget
- Standard: `default`
- Accepterar ett värde


### `--scope-code`

Omfångskod (krävs endast om omfånget inte är det `default`)
- Standard: &quot;
- Accepterar ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `cron:install`

Skapar och installerar crontab för aktuell användare

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



Tvinga installationsaktiviteter
- Standard: `false`
- Accepterar inte ett värde



### `--non-optional`, `-d`



Installera endast icke-valfria (standard) uppgifter
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `cron:remove`

Tar bort uppgifter från crontab

```bash
bin/magento cron:remove
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `cron:run`

Kör jobb enligt schema

```bash
bin/magento cron:run [--group GROUP] [--bootstrap BOOTSTRAP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--group`

Kör endast jobb från angiven grupp
- Kräver ett värde


### `--bootstrap`

Lägga till eller åsidosätta parametrar för bootstrap
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `customer:hash:upgrade`

Uppgradera kundens hash enligt den senaste algoritmen

```bash
bin/magento customer:hash:upgrade
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `deploy:mode:set`

Ange programläge.

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

<!-- app.name --> <!-- command.usage -->

### `mode`

Det programläge som ska anges. Tillgängliga alternativ är &quot;utvecklare&quot; eller &quot;produktion&quot;
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--skip-compilation`, `-s`



Hoppar över rensning och omgenerering av statiskt innehåll (genererad kod, förbearbetad CSS och resurser i pub/static/)
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `deploy:mode:show`

Visar det aktuella programläget.

```bash
bin/magento deploy:mode:show
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:di:info`

Anger information om konfigurationen för beroendeinmatning för kommandot.

```bash
bin/magento dev:di:info <class>
```

<!-- app.name --> <!-- command.usage -->

### `class`

Klassnamn
- Obligatoriskt

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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:email:newsletter-compatibility-check`

Skannar nyhetsbrevmallar för potentiella kompatibilitetsproblem med variabel användning

```bash
bin/magento dev:email:newsletter-compatibility-check
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:email:override-compatibility-check`

Söker igenom e-postmallåsidosättningar för eventuella kompatibilitetsproblem med variabel användning

```bash
bin/magento dev:email:override-compatibility-check
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:profiler:disable`

Inaktivera profileraren.

```bash
bin/magento dev:profiler:disable
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:profiler:enable`

Aktivera profileraren.

```bash
bin/magento dev:profiler:enable [<type>]
```

<!-- app.name --> <!-- command.usage -->

### `type`

Profilerartyp
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:query-log:disable`

Inaktivera DB-frågeloggning

```bash
bin/magento dev:query-log:disable
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:query-log:enable`

Aktivera loggning av databasfrågor

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:source-theme:deploy`

Samlar in och publicerar källfiler för temat.

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

<!-- app.name --> <!-- command.usage -->

### `file`

Filer som ska förbearbetas (filen ska anges utan filtillägg)
- Standard: `css/styles-mcss/styles-l`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Typ av källfiler: [mindre]
- Standard: `less`
- Kräver ett värde


### `--locale`

Språk: [en_US]
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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:template-hints:disable`

Inaktivera malltips för frontend. En cachetömning kan behövas.

```bash
bin/magento dev:template-hints:disable
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:template-hints:enable`

Aktivera malltips för frontend. En cachetömning kan behövas.

```bash
bin/magento dev:template-hints:enable
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:template-hints:status`

Visa status för malltips för förgreningstips.

```bash
bin/magento dev:template-hints:status
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:tests:run`

Kör tester

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

<!-- app.name --> <!-- command.usage -->

### `type`

Typ av test som ska köras. Tillgängliga typer: all, unit, integration, integration-all, static, static-all, integrity, legacy, default
- Standard: `default`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--arguments`, `-c`



Ytterligare argument för PHPUnit. Exempel: &quot;-c&#39;—filter=MyTest&#39;&quot; (inga blanksteg)
- Standard: &quot;
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:urn-catalog:generate`

Skapar katalogen med URN:er till *.xsd-mappningar så att XML markeras.

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

Sökväg till fil som katalogen ska skrivas ut från. För PhpStorm använder du .idea/misc.xml
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--ide`

Formatet som katalogen ska skapas i. Stöds: [oväder, vscode]
- Standard: `phpstorm`
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `dev:xml:convert`

Konverterar XML-fil med XSL-formatmallar

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

<!-- app.name --> <!-- command.usage -->

### `xml-file`

Sökväg till XML-fil som ska omformas
- Obligatoriskt

   <!-- argument -->

### `processor`

Sökväg till XSL-formatmall som ska användas i XML-filen
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--overwrite`, `-o`



Skriv över XML-fil
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `downloadable:domains:add`

Lägg till domäner i vitlistan över nedladdningsbara domäner

```bash
bin/magento downloadable:domains:add [<domains>...]
```

<!-- app.name --> <!-- command.usage -->

### `domains`

Domännamn

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `downloadable:domains:remove`

Ta bort domäner från vitlistan över nedladdningsbara domäner

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

<!-- app.name --> <!-- command.usage -->

### `domains`

Domännamn

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `downloadable:domains:show`

Visa lista över nedladdningsbara domäner

```bash
bin/magento downloadable:domains:show
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `encryption:payment-data:update`

Återkrypterar krypterade kreditkortsdata med det senaste krypteringschiffret.

```bash
bin/magento encryption:payment-data:update
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `i18n:collect-phrases`

Upptäcker fraser i kodbasen

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

<!-- app.name --> <!-- command.usage -->

### `directory`

Katalogsökväg som ska tolkas. Behövs inte om flaggan —magento är inställd
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--output`, `-o`



Sökväg (inklusive filnamn) till en utdatafil. Om ingen fil har angetts är standardinställningen stdout.
- Kräver ett värde



### `--magento`, `-m`



Använd parametern —magento för att tolka den aktuella Magento-kodbasen. Utelämna parametern om en katalog anges.
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `i18n:pack`

Sparar språkpaket

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

<!-- app.name --> <!-- command.usage -->

### `source`

Sökväg till källordsfil med översättningar
- Obligatoriskt

   <!-- argument -->

### `locale`

Målspråk för ordlista, till exempel &quot;de_DE&quot;
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--mode`, `-m`



Spara läge för ordlista -&quot;ersätt&quot; - ersätt språkpaket med nytt -&quot;sammanfoga&quot; - sammanfoga språkpaket, som standard&quot;ersätt&quot;
- Standard: `replace`
- Kräver ett värde



### `--allow-duplicates`, `-d`



Använd parametern —allow-duplicates för att tillåta att dubbletter av translate sparas. Annars utelämnar du parametern.
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `i18n:uninstall`

Avinstallerar språkpaket

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

<!-- app.name --> <!-- command.usage -->

### `package`

Språkpaketets namn

- Standard: `[]`
- Obligatoriskt

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--backup-code`, `-b`



Säkerhetskopiera kod och konfigurationsfiler (förutom temporära filer)
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `indexer:info`

Visar tillåtna indexerare

```bash
bin/magento indexer:info
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `indexer:reindex`

Indexerar om data

```bash
bin/magento indexer:reindex [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `indexer:reset`

Återställer indexerarstatus till ogiltig

```bash
bin/magento indexer:reset [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `indexer:set-dimensions-mode`

Ange indexeringsläge för Dimensioner

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

<!-- app.name --> <!-- command.usage -->

### `indexer`

Indexerarnamn [catalog_product_price]
<!-- argument -->

### `mode`

Indexeringens dimensionslägen catalog_product_price none,website,customer_group,website_and_customer_group
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `indexer:set-mode`

Anger typ av indexläge

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

<!-- app.name --> <!-- command.usage -->

### `mode`

Typ av indexeringsläge [realtid|schema]
<!-- argument -->

### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `indexer:show-dimensions-mode`

Visar indexerarens Dimension

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

<!-- app.name --> <!-- command.usage -->

### `indexer`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index (catalog_product_price)

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `indexer:show-mode`

Visar indexläge

```bash
bin/magento indexer:show-mode [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `indexer:status`

Visar indexerarens status

```bash
bin/magento indexer:status [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Blankstegsavgränsad lista med indextyper eller utelämna detta för alla index.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `info:adminuri`

Visar Magento Admin URI

```bash
bin/magento info:adminuri
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `info:backups:list`

Skriver ut lista över tillgängliga säkerhetskopior

```bash
bin/magento info:backups:list
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `info:currency:list`

Visar listan över tillgängliga valutor

```bash
bin/magento info:currency:list
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `info:dependencies:show-framework`

Visar antalet beroenden till Magento-ramverket

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



Rapportfilnamn
- Standard: `framework-dependencies.csv`
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `info:dependencies:show-modules`

Visar antalet beroenden mellan moduler

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



Rapportfilnamn
- Standard: `modules-dependencies.csv`
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `info:dependencies:show-modules-circular`

Visar antalet cirkulära beroenden mellan moduler

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



Rapportfilnamn
- Standard: `modules-circular-dependencies.csv`
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `info:language:list`

Visar en lista över tillgängliga språkområden

```bash
bin/magento info:language:list
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `info:timezone:list`

Visar listan över tillgängliga tidszoner

```bash
bin/magento info:timezone:list
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `inventory:reservation:create-compensations`

Skapa reservationer med angivna kompensationsargument

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

<!-- app.name --> <!-- command.usage -->

### `compensations`

Lista över ersättningsargument i formatet&lt;order_increment_id>:&lt;sku>:&lt;quantity>:&lt;stock-id>&quot;

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--raw`, `-r`



Råutdata
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `inventory:reservation:list-inconsistencies`

Visa alla order och produkter med inkonsekvenser i försäljningsbar kvantitet

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `inventory-geonames:import`

Hämta och importera geonamn för källvalsalgoritm

```bash
bin/magento inventory-geonames:import <countries>...
```

<!-- app.name --> <!-- command.usage -->

### `countries`

Lista över landskoder som ska importeras

- Standard: `[]`
- Obligatoriskt

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `maintenance:allow-ips`

Anger undantagna IP-adresser i underhållsläge

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

<!-- app.name --> <!-- command.usage -->

### `ip`

Tillåtna IP-adresser

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `maintenance:disable`

Inaktiverar underhållsläge

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--ip`

Tillåtna IP-adresser (använd &#39;none&#39; för att rensa tillåten IP-lista)
- Standard: `[]`
- Kräver ett värde


### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `maintenance:enable`

Aktiverar underhållsläge

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--ip`

Tillåtna IP-adresser (använd &#39;none&#39; för att rensa tillåten IP-lista)
- Standard: `[]`
- Kräver ett värde


### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `maintenance:status`

Visar status för underhållsläge

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `media-content:sync`

Synkronisera innehåll med resurser

```bash
bin/magento media-content:sync
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `media-gallery:sync`

Synkronisera medielagring och medieresurser i databasen

```bash
bin/magento media-gallery:sync
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `module:config:status`

Kontrollerar modulkonfigurationen i filen app/etc/config.php och rapporterar om den är uppdaterad eller inte

```bash
bin/magento module:config:status
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `module:disable`

Inaktiverar angivna moduler

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

<!-- app.name --> <!-- command.usage -->

### `module`

Namn på modulen

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `module:enable`

Aktiverar angivna moduler

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

<!-- app.name --> <!-- command.usage -->

### `module`

Namn på modulen

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `module:status`

Visar status för moduler

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

<!-- app.name --> <!-- command.usage -->

### `module-names`

Namn på valfri modul

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `module:uninstall`

Avinstallerar moduler som installerats av disposition

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

<!-- app.name --> <!-- command.usage -->

### `module`

Namn på modulen

- Standard: `[]`
- Obligatoriskt

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `newrelic:create:deploy-marker`

Kontrollera om det finns poster i distributionskön och skapa en lämplig distributionsmarkör.

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

<!-- app.name --> <!-- command.usage -->

### `message`

Vill du distribuera meddelandet?
- Obligatoriskt

   <!-- argument -->

### `change_log`

Ändra logg?
- Obligatoriskt

   <!-- argument -->

### `user`

Distributionsanvändare
<!-- argument -->

### `revision`

Revision
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `queue:consumers:list`

Lista över MessageQueue-användare

```bash
bin/magento queue:consumers:list
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `queue:consumers:start`

Starta MessageQueue-konsument

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

<!-- app.name --> <!-- command.usage -->

### `consumer`

Namnet på den konsument som ska startas.
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



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

Antalet processer per konsument.
- Accepterar ett värde


### `--pid-file-path`

Filsökvägen för att spara PID (det här alternativet är föråldrat, använd —single-thread i stället)
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `remote-storage:sync`

Synkronisera mediefiler med fjärrlagring.

```bash
bin/magento remote-storage:sync
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `sampledata:deploy`

Distribuera exempeldatamoduler för dispositionsbaserade Magento-installationer

```bash
bin/magento sampledata:deploy [--no-update]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-update`

Uppdatera Composer.json utan att köra Composer-uppdatering
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `sampledata:remove`

Ta bort alla exempeldatapaket från Composer.json

```bash
bin/magento sampledata:remove [--no-update]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-update`

Uppdatera Composer.json utan att köra Composer-uppdatering
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `sampledata:reset`

Återställ alla exempeldatamoduler för ominstallation

```bash
bin/magento sampledata:reset
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `security:recaptcha:disable-for-user-forgot-password`

Inaktivera reCAPTCHA för administratörsanvändaren har glömt lösenordsformuläret

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `security:recaptcha:disable-for-user-login`

Inaktivera reCAPTCHA för inloggningsformulär för administratörer

```bash
bin/magento security:recaptcha:disable-for-user-login
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `security:tfa:google:set-secret`

Ange hemligheten som används för generering av engångslösenord i Google.

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

<!-- app.name --> <!-- command.usage -->

### `user`

Användarnamn
- Obligatoriskt

   <!-- argument -->

### `secret`

Hemlighet
- Obligatoriskt

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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `security:tfa:providers`

Visa alla tillgängliga leverantörer

```bash
bin/magento security:tfa:providers
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `security:tfa:reset`

Återställ konfigurationen för en användare

```bash
bin/magento security:tfa:reset <user> <provider>
```

<!-- app.name --> <!-- command.usage -->

### `user`

Användarnamn
- Obligatoriskt

   <!-- argument -->

### `provider`

Providerkod
- Obligatoriskt

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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:backup`

Säkerhetskopierar Magento programkodbas, media och databas

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:config:set`

Skapar eller ändrar distributionskonfigurationen

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--backend-frontname`

Förnamn för serverdel (genereras automatiskt om det saknas)
- Kräver ett värde


### `--enable-debug-logging`

Aktivera felsökningsloggning
- Kräver ett värde


### `--enable-syslog-logging`

Aktivera syslog-loggning
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

Redis loggnivå. Värden: 0 (minst utförlig) till 7 (mest utförlig)
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

Redis Sentinel överordnad
- Kräver ett värde


### `--session-save-redis-sentinel-servers`

Redis Sentinel-servrar, kommaseparerade
- Kräver ett värde


### `--session-save-redis-sentinel-verify-master`

Redis Sentinel bekräftar överordnad. Värden: false (standard), true
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

Komprimeringslib som ska användas [snappy,lzf,l4z,zstd,gzip] (lämna tomt för att bestämma automatiskt)
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

Värd och port för anslutning till Zookeeper-klustret. Till exempel: 127.0.0.1:2181
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


### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:db-data:upgrade`

Installerar och uppgraderar data i databasen

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:db-declaration:generate-patch`

Generera en patch och placera den i en specifik mapp.

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

<!-- app.name --> <!-- command.usage -->

### `module`

Modulnamn
- Obligatoriskt

   <!-- argument -->

### `patch`

Namn på korrigering
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--revertable`

Kontrollera om korrigeringen kan ångras eller inte.
- Standard: `false`
- Accepterar ett värde


### `--type`

Ta reda på vilken typ av korrigering som ska skapas. Tillgängliga värden: `data`, `schema`.
- Standard: `data`
- Accepterar ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:db-declaration:generate-whitelist`

Generera vitlista över tabeller och kolumner som kan redigeras av deklarationsinstallationsprogrammet

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--module-name`

Namn på modulen där vitlistan ska genereras
- Standard: `all`
- Accepterar ett värde



### `--help`, `-h`



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:db-schema:upgrade`

Installerar och uppgraderar databasschemat

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--convert-old-scripts`

Tillåter konvertering av gamla skript (InstallSchema, UpgradeSchema) till formatet db_schema.xml
- Standard: `false`
- Accepterar ett värde


### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:db:status`

Kontrollerar om databasschemat eller data kräver uppgradering

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:di:compile`

Genererar DI-konfiguration och alla saknade klasser som kan genereras automatiskt

```bash
bin/magento setup:di:compile
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:install`

Installerar programmet Magento

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--backend-frontname`

Förnamn för serverdel (genereras automatiskt om det saknas)
- Kräver ett värde


### `--enable-debug-logging`

Aktivera felsökningsloggning
- Kräver ett värde


### `--enable-syslog-logging`

Aktivera syslog-loggning
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

Redis loggnivå. Värden: 0 (minst utförlig) till 7 (mest utförlig)
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

Redis Sentinel överordnad
- Kräver ett värde


### `--session-save-redis-sentinel-servers`

Redis Sentinel-servrar, kommaseparerade
- Kräver ett värde


### `--session-save-redis-sentinel-verify-master`

Redis Sentinel bekräftar överordnad. Värden: false (standard), true
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

Komprimeringslib som ska användas [snappy,lzf,l4z,zstd,gzip] (lämna tomt för att bestämma automatiskt)
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

Värd och port för anslutning till Zookeeper-klustret. Till exempel: 127.0.0.1:2181
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

Om en säkerhetsnyckel ska användas i Magento Admin-URL:er och -formulär. Inaktuell, använd config:set med sökvägsadministratör/säkerhet/use_form_key
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

Sökmotor. Värden: elasticsearch5, elasticsearch6, elasticsearch7
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

Installationen av Magento körs i torrt läge
- Standard: `false`
- Accepterar ett värde


### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:performance:generate-fixtures`

Skapar korrigeringar

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

<!-- app.name --> <!-- command.usage -->

### `profile`

Sökväg till profilkonfigurationsfil
- Obligatoriskt

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--skip-reindex`, `-s`



Hoppa över omindexering
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:rollback`

Återställer Magento-programkodbas, media och databas

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:static-content:deploy`

Distribuerar statiska vyfiler

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

<!-- app.name --> <!-- command.usage -->

### `languages`

Blankstegsavgränsad lista med ISO-639-språkkoder som statiska vyfiler ska skrivas ut för.

- Standard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




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

Om du bara uppdaterar versionen av statiskt innehåll kan du uppdatera statiskt innehåll i webbläsarens cacheminne och CDN-cacheminne.
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



Visa det här hjälpmeddelandet
- Standard: `false`
- Accepterar inte ett värde



### `--quiet`, `-q`



Skriv inget meddelande
- Standard: `false`
- Accepterar inte ett värde



### `--verbose`, `-v|-vv|-vvv`



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:store-config:set`

Installerar butikskonfigurationen. Borttagen sedan 2.2.0. Använd config:set i stället

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



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

Om en säkerhetsnyckel ska användas i Magento Admin-URL:er och -formulär. Inaktuell, använd config:set med sökvägsadministratör/säkerhet/use_form_key
- Kräver ett värde


### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:uninstall`

Avinstallerar programmet Magento

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `setup:upgrade`

Uppgraderar Magento-programmet, DB-data och schema

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



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

Installationen av Magento körs i torrt läge
- Standard: `false`
- Accepterar ett värde


### `--magento-init-params`

Lägg till i valfritt kommando för att anpassa initieringsparametrar för Magento, till exempel: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[bas][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `store:list`

Visar listan över butiker

```bash
bin/magento store:list
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `store:website:list`

Visar listan över webbplatser

```bash
bin/magento store:website:list
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `theme:uninstall`

Avinstallerar tema

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

<!-- app.name --> <!-- command.usage -->

### `theme`

Sökväg till temat. Temasökvägen ska anges som fullständig sökväg, vilket är område/leverantör/namn. Till exempel front/Magento/blank

- Standard: `[]`
- Obligatoriskt

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--backup-code`

Säkerhetskopiera kod (förutom tillfälliga filer)
- Standard: `false`
- Accepterar inte ett värde



### `--clear-static-content`, `-c`



Rensa genererade statiska vyfiler.
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size -->

## `varnish:vcl:generate`

Skapar lack VCL och lägger det på kommandoraden

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



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
- Standard: `4`
- Kräver ett värde


### `--grace-period`

Behåll programmet i sekunder
- Standard: `300`
- Kräver ett värde


### `--output-file`

Sökväg till filen som ska skrivas vcl
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



Öka meddelandenas exakthet: 1 för normal utskrift, 2 för mer utförlig utskrift och 3 för felsökning
- Standard: `false`
- Accepterar inte ett värde



### `--version`, `-V`



Visa den här programversionen
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



### `--no-interaction`, `-n`



Ställ inga interaktiva frågor
- Standard: `false`
- Accepterar inte ett värde <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->