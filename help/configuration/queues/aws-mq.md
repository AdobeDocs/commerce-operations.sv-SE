---
title: Konfigurera Amazon Message Queue
description: Lär dig hur du konfigurerar Commerce att använda AWS MQ-tjänsten.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Konfigurera Amazon Message Queue

Från och med Commerce 2.4.3 är Amazon Message Queue (MQ) tillgängligt som en molnklar ersättning för lokala meddelandeköinstanser.

Information om hur du skapar en meddelandekö på AWS finns i [Konfigurera Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) i _AWS-dokumentation_.

## Konfigurera handel för AWS MQ

För att ansluta till AWS MQ-tjänsten konfigurerar du `queue.amqp` objekt i `env.php` -fil.
AWS Message Queue kräver en SSL/TLS-anslutning.

```php
'queue' => [
    'amqp' => [
        'host' => '[host]', //example: c-bf4kk1c5-5gcc-4b43-9b9e-8f5b54d234.mq.us-west-3.amazonaws.com
        'port' => 5671,
        'user' => 'yourusername',
        'password' => 'yourpassword',
        'virtualhost' => '/',

        // AWS fields to add
        'ssl' => 'true'
    ]
],
```

Var:

- `host`- URL:en för AMQP-slutpunkten; genom att klicka på mäklarens namn i AWS (ta bort&quot;https://&quot; och det efterföljande portnumret)
- `user`—Det användarnamn som angavs när AWS MQ-mäklaren skapades
- `password`—Lösenordsvärdet som angavs när AWS MQ-mäklaren skapades

>[!INFO]
>
>Amazon MQ har bara stöd för TLS-anslutningar. Peer-verifiering stöds inte.

Efter redigering av `env.php` kör du följande kommando för att slutföra installationen:

```bash
bin/magento setup:upgrade
```

## Hur Commerce använder AWS MQ-tjänsten

The `async.operations.all` som använder AMQP-anslutningen.

Den här konsumenten skickar alla ämnesnamn som har prefixats med `async` via AWS MQ-anslutningen.

I `InventoryCatalog` det finns:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

Standardkonfigurationen för `InventoryCatalog` publicerar inte meddelanden till [!DNL RabbitMQ]; standardbeteendet är att utföra åtgärden i samma användartråd. Att berätta `InventoryCatalog` för att publicera meddelanden, aktivera `cataloginventory/bulk_operations/async`. Gå till **Lager** > Konfiguration > **Katalog** > **Lager** > Administrera gruppåtgärder och ange  `Run asynchronously`till **Ja**.

## Testar meddelandekön

Så här testar du meddelanden som skickas från Commerce till [!DNL RabbitMQ]:

1. Logga in på [!DNL RabbitMQ] webbkonsol i AWS för att övervaka köer.
1. Skapa en produkt i Admin.
1. Skapa en lagerkälla.
1. Aktivera **Lager** > Konfiguration > **Katalog** > **Lager** > Admin - gruppåtgärder > Kör asynkront.
1. Gå till **Katalog** > Produkter. Välj den produkt som skapats ovan i rutnätet och klicka på **Tilldela lagerkälla**.
1. Klicka **Spara och stäng** för att slutföra processen.

   Nu bör meddelanden visas i [!DNL RabbitMQ] webbkonsol.

1. Starta `async.operations.all` meddelandekökonsument.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Du bör nu se meddelandet som står i kö bearbetas i [!DNL RabbitMQ] webbkonsol.
Kontrollera att lagerkällor har ändrats i produkten i Admin.
