---
title: Hantera meddelandeköer
description: Lär dig hur du hanterar meddelandeköer från kommandoraden för Adobe Commerce.
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 8dce1f1e961ec02d7783a7423a51a7d4567dce79
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Hantera meddelandeköer

Du kan hantera meddelandeköer från kommandoraden med hjälp av cron-jobb eller en extern processhanterare för att se till att konsumenterna hämtar meddelanden.

## Processhantering

Kronjobb är standardmekanismen för att återstarta konsumenter. Processer som har startats av `cron` förbrukar det angivna antalet meddelanden och avslutar sedan. Om `cron` startas om startas konsumenten om.

I följande exempel visas `crontab`-konfigurationen för konsumenter som kör:

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
>Hur ofta du kontrollerar meddelandeköer kan bero på din affärslogik och tillgängliga systemresurser. I allmänhet kanske du vill söka efter nya kunder och skicka välkomstmeddelanden oftare än med en mer resurskrävande process, som att uppdatera katalogen. Du bör definiera `cron`-scheman efter dina affärsbehov.
>
>Den kan konfigureras i Admin Stores > Settings > Configuration > Advanced > System > Cron configuration options for group: customers.
>
>Mer information om hur du använder [ med Commerce finns i ](../cli/configure-cron-jobs.md)Konfigurera och kör cron`cron`.

Du kan också använda en processhanterare som [Supervisor](https://supervisord.readthedocs.io/en/latest/) för att övervaka processernas status. Hanteraren kan använda kommandoraden för att starta om processerna efter behov.

## Konfiguration

### Som standard

- Kronijobbet `consumers_runner` är aktiverat
- Kronijobbet `consumers_runner` kör alla definierade konsumenter
- Varje konsument bearbetar 10000 meddelanden och avslutas sedan

>[!INFO]
>
>Om din Adobe Commerce-butik finns på molnplattformen använder du [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=sv-SE#cron_consumers_runner) för att konfigurera `consumers_runner` cron-jobbet.

### Specifik konfiguration

Redigera filen `/app/etc/env.php` om du vill konfigurera cron-jobbet `consumers_runner`.

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

- `cron_run` - Ett booleskt värde som aktiverar eller inaktiverar `consumers_runner` cron-jobbet (standard = `true`).
- `max_messages` - Det maximala antalet meddelanden som varje konsument måste bearbeta innan de avbryts (standard = `10000`). Även om vi inte rekommenderar det kan du använda 0 för att hindra konsumenten från att säga upp sig. Se [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) om du vill konfigurera hur konsumenter bearbetar meddelanden från meddelandekön.
- `consumers` - en matris med strängar som anger vilka konsumenter som ska köras. En tom array kör *alla* konsumenter.
- `multiple_processes` - en matris med nyckelvärdepar som anger vilken konsument som ska köras i hur många processer. Stöds i Commerce 2.4.4 eller senare.

  >[!INFO]
  >
  >Du bör inte köra flera användare på en MySQL-styrd kö. Mer information finns i [Ändra meddelandekö från MySQL till AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp).

  >[!INFO]
  >
  >Om din Adobe Commerce-butik finns på molnplattformen använder du [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=sv-SE#consumers_wait_for_max_messages) för att konfigurera hur konsumenter ska bearbeta meddelanden från meddelandekön.

Se [Starta meddelandekökonsumenter](../cli/start-message-queues.md).
