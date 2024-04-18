---
title: Hantera moduler och tillägg (utvecklare)
description: Hantera Adobe Commerce-moduler och tillägg med kommandoradsgränssnittet och Composer-pakethanteraren.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 3%

---

# Hantera moduler och tillägg

Uppgradera moduler och tillägg för utvecklare genom att ange deras versioner i Adobe Commerce `composer.json` -fil. Om du inte är en bidragsgivare kan du se [Uppgradera](../implementation/perform-upgrade.md).

Du kan antingen lägga till en `require` till `composer.json` eller så kan du använda `composer require` enligt följande:

{{$include /help/_includes/server-login.md}}

Du har följande alternativ:

## Hämta tillgängliga modulversioner

Kommandoanvändning:

```bash
composer show --all <vendor>/<name>
```

Exempel:

```bash
composer show --all example/module
```

## Använd `composer require` kommando

Kommandoanvändning:

```bash
composer require <vendor>/<name>:<version>
```

Exempel:

```bash
composer require example/module:1.0.0
```

Vänta medan Composer uppdaterar beroenden och installerar modulen.

## Lägg till en `require` till filen Composer.json

1. Öppna `composer.json` i en textredigerare.

1. Lägg till en `require` -avsnitt.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Spara ändringarna i `composer.json` och avsluta textredigeraren.

1. Lös beroenden och skriv exakta versioner till `composer.lock` -fil.

   ```bash
   composer update
   ```
