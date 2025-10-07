---
title: Kronjobb
description: Lär dig mer om cron-grupper och hur du skapar anpassade cron-jobb i Adobe Commerce. Upptäck schemalagda aktivitetsinställningar och konfiguration av kundgrupp.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Kronjobb

Här beskrivs hur du ställer in ett anpassat cron-jobb och eventuellt en anpassad cron-grupp. Om ditt Commerce-tillägg kräver att schemalagda aktiviteter körs regelbundet, kan du använda de här avsnitten för att ställa in ett cron _job_ (den schemalagda aktiviteten) och eventuellt en cron _group_ som kör anpassade aktiviteter samtidigt.

Om du använder en krongrupp som tillhandahålls av Commerce behöver du inte definiera en anpassad cron-grupp. Om du vill att dina kronijobb ska köras enligt ett annat schema eller om du vill att alla ska köras tillsammans, bör du definiera en cron-grupp

Commerce-programmet innehåller följande cron-grupper:

- `default`, som innehåller de flesta cron-jobb
- `index`, som uppdaterar [indexerare](../cli/manage-indexers.md)
- `consumers`, som kör meddelandekön [containers](../cli/start-message-queues.md)
- Dessa ämnen finns endast i Adobe Commerce
   - `staging`, som kör [Mellanlagringsrelaterade](https://experienceleague.adobe.com/sv/docs/commerce-admin/content-design/staging/content-staging) uppgifter
   - `catalog_event`, som kör aktiviteter för mål- och kundvagnsregler
