---
title: Konfigurera överordnad databaser automatiskt
description: Mer information om hur du konfigurerar den delade databaslösningen automatiskt.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 1%

---


# Konfigurera överordnad databaser automatiskt

{#ee-only}

{{deprecate-split-db}}

I det här avsnittet beskrivs hur du kommer igång med den delade databaslösningen genom att:

1. Installera Adobe Commerce med en enda överordnad databas (namngiven `magento`)
1. Skapa ytterligare två överordnad databaser för [utcheckning](https://glossary.magento.com/checkout) och OMS (namngivna `magento_quote` och `magento_sales`)
1. Konfigurera Adobe Commerce för att använda utchecknings- och säljdatabaser

>[!INFO]
>
>I den här guiden antas att alla tre databaserna finns på samma värd som Commerce-programmet och att de har ett namn `magento`, `magento_quote`och `magento_sales`. Det är dock upp till dig att välja var databaserna ska hittas och vad de ska namnges. Vi hoppas att våra exempel gör instruktionerna enklare att följa.

## Installera Adobe Commerce

Du kan när som helst aktivera delade databaser efter att du har installerat Adobe Commerce. Med andra ord kan du lägga till delade databaser i ett Adobe Commerce-system som redan har utchecknings- och orderdata. Använd instruktionerna i Adobe Commerce README eller [installationsguide](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html) för att installera Adobe Commerce-programmet med en enda överordnad databas.

## Ställ in ytterligare överordnad databaser

Skapa utchecknings- och OMS-överordnad databaser enligt följande:

1. Logga in på databasservern som vilken användare som helst.
1. Ange följande kommando för att komma till en MySQL-kommandotolk:

   ```bash
   mysql -u root -p
   ```

1. Ange MySQL `root` användarens lösenord när du uppmanas till det.
1. Ange följande kommandon i den ordning som visas för att skapa databasinstanser med namnet `magento_quote` och `magento_sales` med samma användarnamn och lösenord:

   ```shell
   create database magento_quote;
   ```

   ```shell
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   ```

   ```shell
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Retur `exit` för att avsluta kommandotolken.

1. Verifiera databaserna, en åt gången:

   Utcheckningsdatabas:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   Orderhanteringssystemdatabas:

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Om MySQL-övervakaren visas har du skapat databasen på rätt sätt. Om ett fel visas upprepar du de föregående kommandona.

## Konfigurera Commerce för att använda de överordnad databaserna

När du har konfigurerat totalt tre överordnad databaser använder du kommandoraden för att konfigurera Commerce att använda dem. (Kommandot ställer in databasanslutningar och distribuerar tabeller mellan överordnad databaser.)

### Första steget

Se [Kör kommandon](../cli/config-cli.md#running-commands) för att logga in och köra CLI-kommandon.

### Konfigurera utcheckningsdatabasen

Kommandosyntax:

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Exempel:

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

Följande meddelande visas för att bekräfta att installationen lyckades:

```terminal
Migration has been finished successfully!
```

### Konfigurera OMS-databasen

Kommandosyntax:

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Exempel:

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

Följande meddelande visas för att bekräfta att installationen lyckades:

```terminal
Migration has been finished successfully!
```
