---
title: Steg efter datamigrering
description: Lär dig hur du gör efter att du har använt  [!DNL Data Migration Tool]  för att migrera data från Magento 1 till Magento 2.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# Steg efter datamigrering

Utför följande uppgifter när du är klar med migreringen och har testat din nya Magento 2-webbplats noggrant:

* Placera Magento 1 i underhållsläge och stoppa alla administratörsaktiviteter permanent

* Starta Magento 2 cron-jobb

* [Rensa alla cachetyper för Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Indexera om alla Magento 2-index](../../../configuration/cli/manage-indexers.md#reindex)

* Ändra DNS och belastningsutjämnare så att de pekar på produktionsmaskinvaran för Magento 2
