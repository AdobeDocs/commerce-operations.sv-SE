---
title: Uppgradera en Git-baserad installation
description: Uppgradera en Adobe Commerce-installation som du klonat från en Git-databas.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Uppgradera en Git-baserad installation

I det här avsnittet beskrivs hur en utvecklare som bidrar till att uppdatera Adobe Commerce utan att installera om det. Om du inte är en bidragsgivare kan du se [Uppgradera](../implementation/perform-upgrade.md).

Så här uppgraderar du om du är en bidragsgivare:

{{$include /help/_includes/server-login.md}}

1. Spara ändringar som du har gjort i `composer.json` eftersom nästa steg skriver över den.

1. Skapa en säkerhetskopia av `composer.json` -fil.

   ```bash
   cp composer.json composer.json.old
   ```

1. Uppdatera din lokala databas för att få den senaste koden:

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >If `git pull origin develop` misslyckas, se [felsökning](https://support.magento.com/hc/en-us/articles/360034229872).

1. Skilj och sammanfoga dina `composer.json.old` filen med `composer.json` -fil.

1. Lös beroenden och skriv exakta versioner till `composer.lock` -fil.

   ```bash
   composer update
   ```

1. Uppdatera databasen:

   ```bash
   bin/magento setup:upgrade
   ```

1. Rensa cachen:

   ```bash
   bin/magento cache:clean
   ```
