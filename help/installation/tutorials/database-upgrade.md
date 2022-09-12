---
title: Uppgradera databasschemat och data
description: Följ de här stegen för att uppgradera databasschemat för Adobe Commerce eller Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Uppgradera databasschemat och data

Innan du använder kommandot måste du [installera programmet](../advanced.md).

## Uppgradera databasschemat och data

När som helst utför du en åtgärd som orsakar [databasschema](https://glossary.magento.com/database-schema) För data som ska ändras måste du uppdatera dem genom att köra det kommando som beskrivs i det här avsnittet. En partiell förteckning över orsaker följer:

* Du uppgraderade programmet med kommandoraden
* Du installerade eller uppdaterade en komponent med kommandoraden
* Du har aktiverat eller inaktiverat en komponent med kommandoraden

>[!NOTE]
>
>A *komponent* kan vara en modul, ett tema eller ett språkpaket, det spelar ingen roll om komponenten kommer från Commerce Marketplace eller inte.

1. Starta uppgraderingen:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Plats `--keep-generated` är ett valfritt argument som inte uppdateras [statiska vyfiler](../../configuration/cli/static-view-file-deployment.md). Det här valfria argumentet används *endast* under begränsade omständigheter av erfarna systemintegratörer. Det ska användas *endast* in [produktionsläge](../../configuration/bootstrap/application-modes.md#production-mode). Det borde *not* används i [utvecklarläge](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Rensa cacheminnet:

   ```bash
   bin/magento cache:clean
   ```
