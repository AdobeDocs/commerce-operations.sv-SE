---
title: Hantera meddelandeköer
description: Lär dig hur du hanterar meddelandeköer från kommandoraden för Adobe Commerce.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Hantera meddelandeköer

Du kan hantera meddelandeköer från kommandoraden med hjälp av cron-jobb eller en extern processhanterare för att se till att konsumenterna hämtar meddelanden.

## Processhantering

Kronjobb är standardmekanismen för att återstarta konsumenter. Processer som startats av `cron` förbruka det angivna antalet meddelanden och avsluta sedan. Körs om `cron` startar om konsumenten.

I följande exempel visas `crontab` konfiguration för konsumenter:

> /app/code/Magento/MessageQueue/etc/crontab.xml

```xml
...
<job name="consumers_runner" instance="Magento\MessageQueue\Model\Cron\ConsumersRunner" method="run">
    <schedule>* * * * *</schedule>
</job>
...
```

>[!INFO]
>
>Hur ofta du kontrollerar meddelandeköer kan bero på din affärslogik och tillgängliga systemresurser. I allmänhet kanske du vill söka efter nya kunder och skicka välkomstmeddelanden oftare än med en mer resurskrävande process, som att uppdatera katalogen. Du bör definiera `cron` scheman efter företagets behov.
>
>Den kan konfigureras i Admin Stores > Settings > Configuration > Advanced > System > Cron configuration options for group: konsumenter.
>
>Se [Konfigurera och kör cron](../cli/configure-cron-jobs.md) för mer information om hur du använder `cron` med Commerce.

Du kan också använda en processhanterare som [Supervisor](http://supervisord.org/index.html) för att övervaka processernas status. Hanteraren kan använda kommandoraden för att starta om processerna efter behov.

## Konfiguration

### Beteende som standard

- Kronjobb `consumers_runner` är aktiverat
- Kronjobb `consumers_runner` kör alla definierade konsumenter
- Varje konsument bearbetar 10000 meddelanden och avslutas sedan

>[!INFO]
>
>Om din Adobe Commerce-butik finns på molnplattformen använder du [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) för att konfigurera `consumers_runner` cron-jobb.

### Specifik konfiguration

Redigera `/app/etc/env.php` fil för att konfigurera cron-jobbet `consumers_runner`.

```php
...
    'cron_consumers_runner' => [
        'cron_run' => false,
        'max_messages' => 20000,
        'consumers' => [
            'consumer1',
            'consumer2',
        ],
        'multiple_processes' => [
            'consumer1' => 4
        ]
    ],
...
```

- `cron_run` - Ett booleskt värde som aktiverar eller inaktiverar `consumers_runner` cron-jobb (standard = `true`).
- `max_messages` - Det maximala antalet meddelanden som varje konsument måste behandla innan de avbryter (standard = `10000`). Även om vi inte rekommenderar det kan du använda 0 för att hindra konsumenten från att säga upp sig. Se [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) för att konfigurera hur konsumenter ska bearbeta meddelanden från meddelandekön.
- `consumers` - en array med strängar som anger vilka konsumenter som ska köras. En tom array körs *alla* konsumenter.
- `multiple_processes` - en array med nyckelvärdepar som anger vilken konsument som ska köras i hur många processer.

   >[!INFO]
   >
   >Du bör inte köra flera användare på en MySQL-styrd kö. Se [Ändra meddelandekö från MySQL till AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) för mer information.

   >[!INFO]
   >
   >Om din Adobe Commerce-butik finns på molnplattformen använder du [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages) för att konfigurera hur konsumenter ska bearbeta meddelanden från meddelandekön.

Se [Starta användare i meddelandekön](../cli/start-message-queues.md).
