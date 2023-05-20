---
title: Steg efter datamigrering
description: Lär dig hur du gör när du har använt [!DNL Data Migration Tool] för att migrera data från Magento 1 till Magento 2.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
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
