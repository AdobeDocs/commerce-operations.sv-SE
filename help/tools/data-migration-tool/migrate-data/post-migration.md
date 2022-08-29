---
title: Steg efter datamigrering
description: Lär dig hur du gör när du har använt [!DNL Data Migration Tool] för att migrera data från Magento 1 till Magento 2.
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# Steg efter datamigrering

Utför följande uppgifter när du är klar med migreringen och har testat din nya Magento 2-plats noggrant:

* Placera Magento 1 i underhållsläge och stoppa alla permanent [Administratör](https://glossary.magento.com/admin) verksamhet

* Starta Magento 2 cron-jobb

* [Rensa alla cachetyper för Magento 2](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-cache.html#clean-and-flush-cache-types)

* [Indexera om alla Magento 2-index](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#reindex)

* Ändra DNS och belastningsutjämnare så att de pekar på produktionsmaskinvaran för Magento 2
