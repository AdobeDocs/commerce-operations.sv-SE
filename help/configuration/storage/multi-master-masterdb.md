---
title: Konfigurera huvuddatabaser automatiskt
description: Mer information om hur du konfigurerar den delade databaslösningen automatiskt.
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Konfigurera huvuddatabaser automatiskt

{{ee-only}}

{{deprecate-split-db}}

I det här avsnittet beskrivs hur du kommer igång med den delade databaslösningen:

1. Installera Adobe Commerce med en enda huvuddatabas (med namnet `magento`)
1. Skapar ytterligare två huvuddatabaser för utcheckning och OMS (med namnen `magento_quote` och `magento_sales`)
1. Konfigurera Adobe Commerce för att använda utchecknings- och säljdatabaser

>[!INFO]
>
>Den här guiden förutsätter att alla tre databaserna finns på samma värd som Commerce-programmet och att de har namnen `magento`, `magento_quote` och `magento_sales`. Det är dock upp till dig att välja var databaserna ska hittas och vad de ska namnges. Vi hoppas att våra exempel gör instruktionerna enklare att följa.

## Installera Adobe Commerce

Du kan aktivera delade databaser när som helst efter att du har installerat Adobe Commerce. Med andra ord kan du lägga till delade databaser i ett Adobe Commerce-system som redan har utchecknings- och orderdata. Använd instruktionerna i Adobe Commerce README eller [installationsguiden](../../installation/overview.md) för att installera Adobe Commerce-programmet med en enda huvuddatabas.

## Ställ in ytterligare huvuddatabaser

Skapa utchecknings- och OMS-huvuddatabaser enligt följande:

1. Logga in på databasservern som vilken användare som helst.
1. Ange följande kommando för att komma till en MySQL-kommandotolk:

   ```bash
   mysql -u root -p
   ```

1. Ange användarens lösenord för MySQL `root` när du uppmanas till det.
1. Ange följande kommandon i den ordning som visas för att skapa databasinstanser med namnen `magento_quote` och `magento_sales` med samma användarnamn och lösenord:

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

1. Ange `exit` för att avsluta kommandotolken.

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

## Konfigurera Commerce att använda masterdatabaserna

När du har konfigurerat totalt tre huvuddatabaser använder du kommandoraden för att konfigurera Commerce att använda dem. (Kommandot ställer in databasanslutningar och distribuerar tabeller mellan huvuddatabaserna.)

### Första steget

Se [Köra kommandon](../cli/config-cli.md#running-commands) för att logga in och köra CLI-kommandon.

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

```
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

```bash
bin/magento setup:upgrade
```

Följande meddelande visas för att bekräfta att installationen lyckades:

```
Migration has been finished successfully!
```
