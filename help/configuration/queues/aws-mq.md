---
title: Konfigurera Amazon Message Queue
description: Lär dig hur du konfigurerar Commerce att använda tjänsten AWS MQ.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Konfigurera Amazon Message Queue

Från och med Commerce 2.4.3 är Amazon Message Queue (MQ) tillgängligt som en molnklar ersättning för lokala meddelandeköinstanser.

Information om hur du skapar en meddelandekö på AWS finns i [Konfigurera Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) i _AWS-dokumentationen_.

## Konfigurera Commerce för AWS MQ

Om du vill ansluta till AWS MQ-tjänsten konfigurerar du objektet `queue.amqp` i filen `env.php`.
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

- `host` - URL:en för AMQP-slutpunkten, som du kommer åt genom att klicka på mäklarnamnet i AWS (ta bort&quot;https://&quot; och det efterföljande portnumret)
- `user` - Det användarnamn som angavs när AWS MQ-mäklaren skapades
- `password` - Lösenordsvärdet som angavs när AWS MQ-mäklaren skapades

>[!INFO]
>
>Amazon MQ har bara stöd för TLS-anslutningar. Peer-verifiering stöds inte.

När du har redigerat filen `env.php` kör du följande kommando för att slutföra installationen:

```bash
bin/magento setup:upgrade
```

## Hur Commerce använder AWS MQ

Meddelandekökonsumenten `async.operations.all` använder AMQP-anslutningen.

Den här konsumenten skickar alla ämnesnamn som har prefixats med `async` via AWS MQ-anslutningen.

I `InventoryCatalog` finns till exempel:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

Standardkonfigurationen för `InventoryCatalog` publicerar inte meddelanden till [!DNL RabbitMQ]. Standardbeteendet är att utföra åtgärden i samma användartråd. Aktivera `cataloginventory/bulk_operations/async` om du vill att `InventoryCatalog` ska publicera meddelanden. Gå till **Lager** > Konfiguration > **Katalog** > **Inventering** > Admin - gruppåtgärder och ange `Run asynchronously` till **Ja** från administratören.

## Testar meddelandekön

Så här testar du meddelanden som skickas från Commerce till [!DNL RabbitMQ]:

1. Logga in på webbkonsolen [!DNL RabbitMQ] i AWS för att övervaka köer.
1. Skapa en produkt i Admin.
1. Skapa en lagerkälla.
1. Aktivera **Lagrar** > Konfiguration > **Katalog** > **Lager** > Admin - gruppåtgärder > Kör asynkront.
1. Gå till **Katalog** > Produkter. Markera den produkt som skapats ovan i rutnätet och klicka på **Tilldela lager-Source**.
1. Klicka på **Spara och stäng** för att slutföra processen.

   Du bör nu se meddelanden i webbkonsolen [!DNL RabbitMQ].

1. Starta meddelandekökonsumenten `async.operations.all`.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Du bör nu se meddelandet som står i kö bearbetas i webbkonsolen [!DNL RabbitMQ].
Kontrollera att lagerkällor har ändrats i produkten i Admin.
