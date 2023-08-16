---
title: Kronjobb
description: Lär dig mer om cron-grupper och hur du skapar ett anpassat cron-jobb.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Kronjobb

Här beskrivs hur du ställer in ett anpassat cron-jobb och eventuellt en anpassad cron-grupp. Om ditt Commerce-tillägg kräver att schemalagda aktiviteter körs regelbundet kan du använda de här avsnitten för att konfigurera ett cron _jobb_ (den schemalagda aktiviteten) och eventuellt ett cron _grupp_, som kör anpassade uppgifter samtidigt.

Om du använder en Commerce-tillhandahållen cron-grupp behöver du inte definiera en anpassad cron-grupp, men om du vill att dina cron-jobb ska köras enligt ett annat schema eller om du vill att alla ska köras tillsammans, bör du definiera en cron-grupp

I Commerce-programmet finns följande cron-grupper:

- `default`, som innehåller de flesta cron-jobb
- `index`som uppdateras [indexerare](../cli/manage-indexers.md)
- `consumers`, som kör meddelandekön [konsumenter](../cli/start-message-queues.md)
- Dessa ämnen finns endast i Adobe Commerce
   - `staging`som körs [Mellanlagringsrelaterade](https://docs.magento.com/user-guide/cms/content-staging.html) uppgifter
   - `catalog_event`, som kör uppgifter för mål- och kundvagnsregler
