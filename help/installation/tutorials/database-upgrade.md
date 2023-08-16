---
title: Uppgradera databasschemat och data
description: Följ de här stegen för att uppgradera databasschemat för Adobe Commerce eller Magento Open Source.
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Uppgradera databasschemat och data

Innan du använder kommandot måste du [installera programmet](../advanced.md).

## Uppgradera databasschemat och data

När du utför en åtgärd som gör att databasschemat eller data ändras, måste du uppdatera dem genom att köra det kommando som beskrivs i det här avsnittet. En partiell förteckning över orsaker följer:

* Du uppgraderade programmet med kommandoraden
* Du installerade eller uppdaterade en komponent med kommandoraden
* Du har aktiverat eller inaktiverat en komponent med kommandoraden

>[!NOTE]
>
>A *komponent* kan vara en modul, ett tema eller ett språkpaket. Det spelar ingen roll om komponenten kommer från Commerce Marketplace eller inte.

1. Starta uppgraderingen:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Plats `--keep-generated` är ett valfritt argument som inte uppdateras [statiska vyfiler](../../configuration/cli/static-view-file-deployment.md). Det här valfria argumentet används *endast* under begränsade omständigheter av erfarna systemintegratörer. Det ska användas *endast* in [produktionsläge](../../configuration/bootstrap/application-modes.md#production-mode). Det borde *not* används i [utvecklarläge](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Rensa cachen:

   ```bash
   bin/magento cache:clean
   ```
