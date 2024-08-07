---
title: Exempel på global referensarkitektur
description: Se exempel på hur du hanterar kod för storskaliga Adobe Commerce-projekt.
role: Developer, Architect
level: Experienced
hide: true
hidefromtoc: true
exl-id: 2a85b9bf-e547-4a2a-9234-210865f55609
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# Exempel på global referensarkitektur

I det här avsnittet beskrivs vanliga sätt att organisera en [global referensarkitektur (GRA)](overview.md)-kodbas. Även om alternativet [separata paket](#option-1-separate-packages) är att föredra, krävs ett av de andra alternativen som beskrivs nedan för vissa situationer.

## Definitioner

{{$include /help/_includes/gra-definitions.md}}

## Alternativ 1: Separata paket

Mer information om hur du konfigurerar den här metoden finns i [Projektstruktur för disposition](composer/project-structure.md).

![Diagram som illustrerar det separata paketalternativet för global referensarkitektur](../../../assets/playbooks/gra-separate-packages.png)

Det mest flexibla sättet att hantera GRA Composer-paket är genom metapaket. Metapaket innehåller endast en `composer.json`-fil, som definierar andra paketberoenden. Skapa metapaket med [privata Packagist](https://packagist.com/)-databaser.

### Huvudprojekt `composer.json`

```json
{
    "name": "example-client/region-1",
    "description": "Example Client Region 1",
    "type": "project",
    "require": {
        "magento/product-enterprise-edition": "2.3.5",
        "example-client/meta-region-1": "~1.0"
    },
    "minimum-stability": "dev",
    "prefer-stable": true,
    "repositories": [
        {"type": "composer", "url": "https://repo.packagist.com/example-client/"},
        {"packagist.org": false}
    ]
}
```

### `example-client/meta-region-1 composer.json`

```json
{
    "name": "example-client/meta-region-1",
    "description": "Region 1 meta package",
    "type": "metapackage",
    "require": {
        "example-client/meta-gra": "~1.0",
        "example-client/theme-frontend-region1",
        "example-client/language-es-es",
        "ingenico/ogone-client"
    }
}
```

### `example-client/meta-gra composer.json`

```json
{
    "name": "example-client/meta-gra",
    "description": "GRA meta package",
    "type": "metapackage",
    "require": {
        "geoip2/geoip2": "~2.0",
        "magento-services/module-stackify-logger": "~1.1",
        "example-client/sap-connector",
        "example-client/service-chat",
        "example-client/store-locator"
    }
}
```

Varje modul, språkpaket, tema och bibliotek har en egen Git-databas. Varje Git-databas synkroniseras automatiskt med den privata paketeringsdatabasen och genererar ett paket där så länge det finns en `composer.json`-fil i Git-databasens rot.

## Alternativ 2: Paket i grupp

Nedan visas ett exempel på flera moduler i ett enda Composer-paket.

Ett grupppaket kan bara innehålla paket av samma typ. Om du till exempel har flera paket för Adobe Commerce-moduler, teman, språkpaket och bibliotek måste du skapa separata grupppaket för varje typ.

Filstrukturen i leverantörskatalogen ska se ut som i följande exempel. Titta dock i ditt projekt för att se vad som ska ingå i din Git-databas):

```tree
.
└── example-client/
    └── gra/
        └── src/
            ├── SapConnector/
            │   ├── etc/
            │   └── registration.php
            ├── ServiceChat/
            │   ├── etc/
            │   └── registration.php
            ├── StoreLocator/
            │   ├── etc/
            │   └── registration.php
            └── composer.json
```

Filen `composer.json` ska se ut så här:

```json
{
    "name": "example-client/gra",
    "description": "GRA Modules",
    "require": {
        "magento/magento-composer-installer": "*"
    },
    "type": "magento2-module",
    "autoload": {
        "files": [
            "src/SapConnector/registration.php",
            "src/ServiceChat/registration.php",
            "src/StoreLocator/registration.php"
        ],
        "psr-4": {
            "ExampleClient\\SapConnector\\": "src/SapConnector",
            "ExampleClient\\ServiceChat\\": "src/ServiceChat",
            "ExampleClient\\StoreLocator\\": "src/StoreLocator"
        }
    }
}
```

## Alternativ 3: Delad Git

Den här arkitekturen använder fyra Git-databaser för att lagra kod:

- `core`: Innehåller kärninstallationen för Adobe Commerce. Används för att uppgradera Adobe Commerce-versioner.
- `GRA`: Innehåller GRA-kod. Alla GRA-moduler, språkpaket, vita etikettteman och bibliotek.
- `brand/region`: Varje varumärke eller region har en egen databas med endast varumärkes- eller regionspecifik kod.
- `release`: Alla ovanstående sammanfogas i den här Git-databasen. Endast sammanslagningsimplementeringar tillåts här.

![Diagram som illustrerar det delade Git-alternativet för global referensarkitektur](../../../assets/playbooks/gra-split-git.png)

Så här konfigurerar du det här alternativet:

1. Skapa de fyra databastyperna i Git. Skapa `core`- och `GRA`-databaserna endast en gång. Skapa en `brand/region`- och en `release`-databas för varje varumärke.

   Föreslagna databasnamn:

   - `m2-core`
   - `m2-gra`
   - `m2-region-x`/`m2-brand-x` (till exempel `m2-emea`/`m2-adobe`)
   - `m2-release-region-x`/`m2-release-brand-x` (till exempel `m2-release-emea`/`m2-release-adobe`)

1. Skapa en `release/`-katalog och kör följande för att skapa en delad Git-historik för alla rapporter.

   ```bash
   git init
   git remote add origin git@github.com:example-client/m2-release-brand-x.git
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   touch .gitkeep
   git add .gitkeep
   git commit -m 'initialize repository'
   git push -u origin master
   git push core master
   git push gra master
   git push region-x master
   ```

1. Klona varje databas, förutom `core`, i en annan katalog på datorn.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   git clone git@github.com:example-client/m2-region-x.git
   git clone git@github.com:example-client/m2-gra.git
   ```

1. [Installera Adobe Commerce med Composer](../../../installation/composer.md). Ta bort filen `.gitignore`, lägg till fjärrkontrollen `core`, lägg till och implementera koden och tryck på.

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition m2-core
   cd m2-core
   git init
   rm .gitignore
   git remote add origin git@github.com:example-client/m2-core.git
   git fetch
   git checkout .gitkeep
   git add --all
   git commit -m 'install Adobe Commerce'
   git push
   ```

1. Skapa följande kataloger i databasen `GRA`:

   - `app/code/`
   - `app/design/`
   - `app/i18n/`
   - `lib/`

1. Lägg till kod. Ta bort filen `.gitignore`, lägg till och implementera koden, lägg till fjärrfilen och tryck på.

1. I databasen `brand/region`. Gör samma sak som i `GRA`-databasen och tänk på att filerna måste vara unika. Du kan inte inkludera samma fil i både den här databasen och `GRA`-databasen.

1. Använd sammanfogningen i databasen `release`.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   cd m2-release-brand-x
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

1. Ta bort filen `.gitkeep`.

1. Distribuera `release`-databasen till produktions-, test-, QA- och utvecklingsservrarna. Det är lika enkelt att uppgradera `core`-, `GRA`- och `brand`-kod som att köra följande kommandon:

   ```bash
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

## Alternativ 4: Monorepo (rekommenderas)

Denna strategi liknar i hög grad hur Magento Open Source Git-databasen fungerar.

All kod utvecklas och testas i en enda databas. Automatisering destillerar paket från denna enda databas, som kan installeras på UAT- och produktionsmiljöer med Composer.

![Diagram som illustrerar monorepo-alternativet för global referensarkitektur](../../../assets/playbooks/gra-monorepo1.png)

Med monorepo-alternativet kan du enkelt arbeta i en enda databas, samtidigt som du får flexibiliteten att komponera instanser med paket.

Versionshantering och paketering sker genom automatisering med GitHub-åtgärder eller GitLab-åtgärder.

![Diagram som illustrerar monorepo-alternativet för global referensarkitektur](../../../assets/playbooks/gra-monorepo2.png)

Mer information om den här automatiseringen finns i följande resurser:

- [https://github.com/symplify/monorepo-builder](https://github.com/symplify/monorepo-builder)
- [https://github.com/danharrin/monorepo-split-github-action](https://github.com/danharrin/monorepo-split-github-action)

>[!TIP]
>
>Installation av ett monorepo är avancerat, men ger den flexibilitet som ger lägst overheadkostnad.

## Blanda inte strategier

Det är inte tillrådligt att använda en kombinerad metod med Composer för GRA-paket och katalogen `app/` för varumärkes- eller regionpaket.

Du får inte bara alla _fördelar_ utan även alla _nackdelar_ för båda metoderna. Du bör välja det ena eller det andra (Git eller Composer) för att arbeta optimalt.

## Lösningar att undvika

- **Konventioner för modulnamngivning för att beteckna GRA eller varumärke**

  Namngivningsmoduler för att beteckna GRA eller varumärke leder till bristande flexibilitet. Använd i stället Composer-metapaket för att avgöra vilken grupp en modul tillhör. Paketet `vf/meta-gra` innehåller till exempel referenser till alla GRA-paket för kund-VF och kan installeras med kommandot `composer require vf/meta-gra`. Paketet `vf/meta-kipling` innehåller referenser till alla Kipling-specifika paket och till paketet `vf/meta-gra`. Modulerna har till exempel namnen `vf/module-sales` och `vf/module-sap`. Den här namnkonventionen gör att du kan flytta paket mellan varumärket och GRA-status, med låg påverkan.

- **Adobe Commerce Core Upgrades per instance**

  Schemalägg Adobe Commerce-uppgraderingar, inklusive korrigeringsuppgraderingar, för olika varumärken eller regioner som ska exekveras så nära ihop som möjligt. Stöd för flera Adobe Commerce-versioner för delade moduler leder till att moduler måste kopplas ihop på grund av kompatibilitetsbegränsningar och mer än fördubblar underhållsarbetet. Förhindra detta genom att se till att alla instanser körs på samma Adobe Commerce-version innan du fortsätter med den regelbundna utvecklingen.
