---
title: Uppgradera databasschemat och data
description: Följ de här stegen för att uppgradera ditt databasschema för Adobe Commerce.
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Uppgradera databasschemat och data

Innan du använder det här kommandot måste du [installera programmet](../advanced.md).

## Uppgradera databasschemat och data

När du utför en åtgärd som gör att databasschemat eller data ändras, måste du uppdatera dem genom att köra det kommando som beskrivs i det här avsnittet. En partiell förteckning över orsaker följer:

* Du uppgraderade programmet med kommandoraden
* Du installerade eller uppdaterade en komponent med kommandoraden
* Du har aktiverat eller inaktiverat en komponent med kommandoraden

>[!NOTE]
>
>En *komponent* kan vara en modul, ett tema eller ett språkpaket. Det spelar ingen roll om komponenten kommer från Commerce Marketplace eller inte.

1. Starta uppgraderingen:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Där `--keep-generated` är ett valfritt argument som inte uppdaterar [statiska vyfiler](../../configuration/cli/static-view-file-deployment.md). Det här valfria argumentet får användas *endast* under begränsade omständigheter av erfarna systemintegratörer. Den ska användas *endast* i [produktionsläget](../../configuration/bootstrap/application-modes.md#production-mode). Det ska *inte* användas i [utvecklarläge](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Rensa cachen:

   ```bash
   bin/magento cache:clean
   ```
