---
title: Steg efter datamigrering
description: Lär dig hur du gör när du har använt [!DNL Data Migration Tool] för att migrera data från Magento 1 till Magento 2.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# Steg efter datamigrering

Utför följande uppgifter när du är klar med migreringen och har testat din nya Magento 2-plats noggrant:

* Placera Magento 1 i underhållsläge och stoppa alla administratörsaktiviteter permanent

* Starta Magento 2 cron-jobb

* [Rensa alla cachetyper för Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Indexera om alla Magento 2-index](../../../configuration/cli/manage-indexers.md#reindex)

* Ändra DNS och belastningsutjämnare så att de pekar på produktionsmaskinvaran för Magento 2
