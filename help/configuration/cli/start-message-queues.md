---
title: Starta användare i meddelandekön
description: Lär dig hur du startar en användare i en meddelandekö.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Starta användare i meddelandekön

{{file-system-owner}}

Du måste starta en [meddelandekökonsument](../queues/consumers.md) för att aktivera asynkrona åtgärder som Inventory management massåtgärder och REST bulk- och asynkrona slutpunkter. Om du vill aktivera B2B-funktioner måste du starta flera konsumenter. Tredjepartsmoduler kan också kräva att du startar en anpassad konsument.

Så här visar du en lista över alla konsumenter:

```bash
bin/magento queue:consumers:list
```

Så här startar du användare i meddelandekön:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

När alla tillgängliga meddelanden har förbrukats avslutas kommandot. Du kan köra kommandot igen manuellt eller med ett cron-jobb. Du kan också köra flera instanser av `magento queue:consumers:start` för att bearbeta stora meddelandeköer. Du kan till exempel lägga till `&` till kommandot för att köra det i bakgrunden, återgå till en uppmaning och fortsätta köra kommandon:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Se [kö:consumers:start](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) i Commerce-delen av _Referens för kommandoradsverktyg_ om du vill ha information om kommandoalternativ, parametrar och värden.

>[!INFO]
>
>The `--multi-process` finns i `queue:consumers:start` men för att köra användare med parallella processer konfigurerar du [`multiple_processes`](../queues/manage-message-queues.md#configuration) alternativ i `/app/etc/env.php`. Annars, om `queue:consumers:start` anropas med `--multi-process` fungerar det bara på en tråd.
