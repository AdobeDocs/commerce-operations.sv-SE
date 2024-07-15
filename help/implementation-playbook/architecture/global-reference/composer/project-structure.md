---
title: Struktur för Composer-projekt
description: Lär dig hur du konfigurerar och underhåller alternativet för separata paket som beskrivs i exemplen på global referensarkitektur.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 8757d5b8-8309-452f-bfb3-1188a816d14f
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Struktur för Composer-projekt

I den här guiden beskrivs hur du konfigurerar och underhåller det [separata paketalternativet](../examples.md#option-1-separate-packages) som beskrivs i GRA-exemplen (Global Reference Architecture).

## Förutsättningar

Kontrollera följande innan du börjar:

- Du har en Git-databas
- Du har en Composer-databas (det här avsnittet innehåller information om privata paket)
- Du har konfigurerat din Composer-databas så att den speglar databaserna `repo.magento.com` och `packagist.org`

## Huvudsaklig Git-projektdatabas

Den huvudsakliga Git-projektdatabasen ska bara innehålla ett Composer-projekt. Du kan hantera allt annat med Composer-paket. Huvudprojektet får aldrig innehålla något annat än följande filstruktur eftersom Composer installerar alla andra paket via beroenden:

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

Lägg till följande innehåll i filen `.gitignore`:

```tree
/*
!/composer.json
!/composer.lock
```

## Initiera huvudprojektet

1. Skapa en Git-databas med namnet `project-<region/country/brand>`.

1. Skapa `composer.json`- och `composer.lock`-filer:

   ```bash
   composer create-project --no-install --repository-url=https://repo.magento.com/ magento/project-enterprise-edition project-<region/country/brand>
   cd <install-directory-name>
   printf '/*\n!/composer.json\n!/composer.lock\n!/.gitignore' > .gitignore
   composer config --unset version
   composer config name '<client>/project-<region/country/brand>'
   composer config description '<client> <region/country/brand> main composer project'
   composer config repositories.private-packagist composer https://repo.packagist.com/<client>/
   composer config repositories.packagist.org false
   composer config --unset repositories.0
   composer install
   git init
   git add --all
   git commit -m 'initialize project'
   git remote add origin git@bitbucket.org:<client>/project-<region/country/brand>.git
   git push -u origin master
   ```

## Spara filer som inte är moduler

1. Lägg till filen `app/etc/config.xml` i Git-databasen.

   Du kan använda modulen som du ska skapa för att installera andra regioner eller varumärkesspecifika filer, som `.htaccess`, Google- eller Bing-autentiseringstextfiler, körbara filer eller andra statiska filer som inte hanteras av Adobe Commerce-moduler.

   Använd `magento2-component`-typpaket för att skapa en filmappning för att kopiera filer till Git-huvuddatabasen under `composer install`- och `composer update`-åtgärder.

1. Skapa en Git-databas som följer namnkonventionen `component-environment-<region/country/brand>`:

   ```bash
   bin/magento module:enable --all
   cd ../
   mkdir component-environment-<region/country/brand>
   cd component-environment-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/component-environment-<region/country/brand>' \
    --description='<client> <region/country/brand> environment files' \
    --type=magento2-component \
    --require="magento/magento-composer-installer:*"
   mkdir -p app/etc
   cp ../project-<region/country/brand>/app/etc/config.php app/etc/
   composer config -e
   ```

1. Lägg till filen `app/etc/config.php` som en mappning i attributet `extra.map` i filen `composer.json`:

   ```json
   {
       "name": "example-client/component-environment-emea",
       "description": "Example client EMEA environment files",
       "type": "magento2-component",
       "require": {
           "magento/magento-composer-installer": "*"
       },
       "extra": {
           "map": [
               [
                   "app/etc/config.php",
                   "app/etc/config.php"
               ]
           ]
       }
   }
   ```

1. Verifiera din `composer.json`-fil och implementera den i Git-databasen:

   ```bash
   composer validate
   git init
   git add --all
   git commit -m 'initialize component'
   git remote add origin git@bitbucket.org:<client>/component-environment-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

## Konfigurera metapaket

1. Skapa följande Git-databaser:

   - `meta-gra`
   - `meta-<region/country/brand>`

1. Ställ in följande beroendeträd:

   ```tree
   client/project-<region/country/brand>
   └─ requires -> client/meta-<region/country/brand>
                  ├─ requires -> client/component-environment-<region/country/brand>
                  └─ requires -> client/meta-gra
                                 └─ requires -> magento/product-enterprise-edition
   ```

1. Skapa GRA-metapaketet:

   ```bash
   cd ..
   mkdir meta-gra
   cd meta-gra
   composer init --no-interaction \
    --name='<client>/meta-gra' \
    --description='<client> GRA meta package' \
    --type=metapackage \
    --require="magento/product-enterprise-edition:<exact.required.version>"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-gra.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Skapa varumärkets metapaket:

   ```bash
   cd ..
   mkdir meta-<region/country/brand>
   cd meta-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/meta-<region/country/brand>' \
    --description='<client> <region/country/brand> meta package' \
    --type=metapackage \
    --require="<client>/component-environment-<region/country/brand>:~0.1" \
    --require="<client>/meta-gra:~0.1"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Kräv samlingen via beroendehantering i huvudprojektet:

   ```bash
   cd ../project-<region/country/brand>
   rm app/etc/config.php
   composer remove --no-update magento/product-enterprise-edition
   composer require --no-update "<client>/meta-<region/country/brand>:~0.1"
   composer config minimum-stability alpha
   composer config prefer-stable true
   composer update
   git add --all
   git commit -m 'set up GRA dependency tree'
   git push origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Kontrollera att Composer kopierade filen `app/etc/config.php` från `<client>/component-environment-<region/country/brand>`.

## Distribuera kod

På webbservern kan du distribuera kod med Composer, men du kan inte uppdatera huvudprojektet. Installera om projektet med Composer för varje ny distribution, vilket eliminerar behovet av att produktions- och testservrarna har tillgång till Git.

## Lägga till andra instanser och paket

Varje instans (region, varumärke eller på annat sätt unik Adobe Commerce-installation) ska hämta sin egen **huvudprojektinstans**, **specifika metapaket** och **miljökomponentpaket**. **GRA-metapaketet** ska vara **delat** i alla instanser.

Funktionspaket (t.ex. Adobe Commerce-moduler, teman, språkpaket och bibliotek) och tredjepartspaket ska krävas av antingen

- **GRA-metapaket** - För installation på _alla_ instanser
- **instansspecifikt metapaket** - För installation på ett enskilt varumärke eller en enskild region

>[!IMPORTANT]
>
>Kräv inte paket i huvudprojektets `composer.json`-fil i grenarna `main` eller `release`.

## Förbered för utveckling

Installera `develop` versioner av alla moduler som du underhåller för utveckling.

Beroende på din förgreningsstrategi kan du ha grenarna `develop`, `qa`, `uat` och `main`. Varje gren finns i Composer med prefixet `dev-`. `develop`-grenen kan därför krävas via Composer som version `dev-develop`.

1. Skapa `develop` grenar i alla moduler och projektdatabaser.

   ```bash
   cd ../component-environment-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../meta-<region/country/brand>
   git checkout master
   git checkout -b develop
   
   git push -u origin develop
   
   
   cd ../meta-gra
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../project-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   composer require \
   "magento-services/meta-fantasy-corp:dev-develop as 0.999" \
   "magento-services/meta-gra:dev-develop as 0.999" \
   "magento-services/component-environment-fantasy-corp:dev-develop as 0.999"
   ```

   I föregående steg genereras följande rader i din `composer.json`-fil:

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**Sammanfoga inte** de här `composer.json` filändringarna i din produktionsgren. Installera endast stabila versioner av paket på `release`- och `main`-grenar. Du kan definiera dessa beroenden för `qa` grenar och andra icke-huvudgrenar.
