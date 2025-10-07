---
title: Starta användare i meddelandekön
description: Lär dig hur du startar användare av meddelandeköer för asynkrona Adobe Commerce-åtgärder. Upptäck konsumenthantering och konfiguration av B2B-funktioner.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Starta användare i meddelandekön

{{file-system-owner}}

Du måste starta en [meddelandekökonsument](../queues/consumers.md) om du vill aktivera asynkrona åtgärder som t.ex. Inventory management massåtgärder och REST bulk och asynkrona slutpunkter. Om du vill aktivera B2B-funktioner måste du starta flera konsumenter. Tredjepartsmoduler kan också kräva att du startar en anpassad konsument.

Så här visar du en lista över alla konsumenter:

```bash
bin/magento queue:consumers:list
```

Så här startar du användare i meddelandekön:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

När alla tillgängliga meddelanden har förbrukats avslutas kommandot. Du kan köra kommandot igen manuellt eller med ett cron-jobb. Du kan också köra flera instanser av kommandot `magento queue:consumers:start` för att bearbeta stora meddelandeköer. Du kan till exempel lägga till `&` i kommandot för att köra det i bakgrunden, återgå till en fråga och fortsätta köra kommandon:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Mer information om kommandoalternativ, parametrar och värden finns i [`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart) i avsnittet Commerce i _Referens för kommandoradsverktyg_ .

>[!INFO]
>
>Alternativet `--multi-process` finns i kommandot `queue:consumers:start`, men om du vill köra användare med parallella processer konfigurerar du alternativet [`multiple_processes`](../queues/manage-message-queues.md#configuration) i `/app/etc/env.php`. Om `queue:consumers:start` anropas med alternativet `--multi-process` fungerar det annars bara på en tråd.
