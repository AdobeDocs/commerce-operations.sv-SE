---
title: Utveckling av disposition
description: Lär dig hur du utvecklar Composer-moduler på plats i katalogen "vendor/".
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 7664ffb5-2e46-49c3-b2e6-c133c35d2f6b
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Utveckling av disposition

I det här avsnittet beskrivs det rekommenderade sättet att utveckla Composer-moduler på plats (som Git-databaser i katalogen `vendor/`) och lägga till dessa moduler i ditt Git-huvudprojekt.

>[!NOTE]
>
>Dessa riktlinjer gäller främst för [GRA ](../overview.md)-projekt (Global Reference Architecture).

## Förbereda en utvecklingsgren

1. Skapa eller checka ut utvecklingsgrenen i din huvudGit-databas.
1. Kräv utvecklingsversioner för varje modul som du underhåller.

   I det här exemplet representerar varje gren i din Git-huvuddatabas en Composer-paketversion. Den rekommenderade namnkonventionen för Composer-versioner i det här scenariot är `dev-` följt av förgreningsnamnet. Exempel:

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. Om ett annat Composer-paket kräver en specifik version av en modul (till exempel `client/module-example 1.0.12`) installerar du det med ett alias:

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   Ersätt `dev-develop` med `dev-qa` för grenen `qa`.

## Konvertera paket till Git-databaser

Paketen innehåller som standard ingen `.git/`-katalog. Composer kan checka ut paket från Git i stället för att använda de färdigbyggda Composer-paketen. Fördelen med detta är att du enkelt kan ändra paketen under utvecklingen.

1. Ta bort modulen från katalogen `vendor/`.

   ```bash
   rm -rf vendor/client/module-example
   ```

1. Installera om modulen med den [angivna Git-källan](#prepare-a-development-branch).

   ```bash
   composer install --prefer-source
   ```

1. Kontrollera att Composer-paketet nu är en Git-databas:

   ```bash
   cd vendor/client/module-example
   git remote -v
   ```

1. Så här gruppkonverterar du flera moduler till Git-databaser (till exempel&quot;klientmoduler&quot;):

   ```bash
   rm -rf vendor/client
   composer install --prefer-source
   ```

## Påbörja utveckling

1. Skapa eller checka ut en funktion/arbetsgren. I följande exempel visas en gren med samma namn som en Jira-biljett.

   ```bash
   cd vendor/client/module-example
   git checkout master
   git checkout -b JIRA-1200
   ```

1. När du har ändrat grenar i en modul kan du se ändringarna genom att tömma Adobe Commerce-cachen och statiskt innehåll.

   ```bash
   bin/magento cache:flush
   bin/magento module:enable --all --clear-static-content
   ```

## Uppdatera huvudprojektet med din utveckling

Uppdatera din Git-huvuddatabas genom att ändra `composer.lock`-filen. Aktivera modulen om den är ny.

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
