---
title: Message Broker
description: Följ de här stegen för att installera och konfigurera nödvändig programvara för meddelandehantering (till exempel [!DNL RabbitMQ]) för lokala installationer av Adobe Commerce.
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---

# Message Broker

Adobe Commerce använder [!DNL RabbitMQ] meddelandeansvarig med öppen källkod. Det erbjuder ett tillförlitligt, skalbart och portabelt meddelandesystem med hög tillgänglighet.

Meddelandeköer är en asynkron kommunikationsmekanism där avsändaren och mottagaren av ett meddelande inte kontaktar varandra. De behöver inte heller kommunicera med meddelandekön samtidigt. När en avsändare placerar ett meddelande i en kö lagras det tills mottagaren tar emot det.

Meddelandekösystemet måste upprättas innan du kan installera Adobe Commerce eller Magento Open Source. Grundordningen är:

1. Installera [!DNL RabbitMQ] och alla krav.
1. Anslut [!DNL RabbitMQ] till Adobe Commerce eller Magento Open Source.

>[!NOTE]
>
>Du kan använda MySQL eller [!DNL RabbitMQ] för meddelandeköbearbetning. Mer information om hur du konfigurerar meddelandekösystemet finns i [Översikt över meddelandeköer](https://developer.adobe.com/commerce/php/development/components/message-queues/). Om du använder API:t för massutskick med Adobe Commerce används som standard systemkonfigurationen för meddelandekön med [!DNL RabbitMQ] som meddelandeförmedlare. Se [Starta användare i meddelandekön](../../configuration/cli/start-message-queues.md) för mer information.

## Installera [!DNL RabbitMQ] på Ubuntu

Installera [!DNL RabbitMQ] I Ubuntu 16 anger du följande kommando:

```bash
sudo apt install -y rabbitmq-server
```

Det här kommandot installerar även de nödvändiga Erlang-paketen.

Om du har en äldre version av Ubuntu [!DNL RabbitMQ] rekommenderar att paketet installeras från deras webbplats.

1. Hämta .deb-paketet från [kanitmq-server](https://www.rabbitmq.com/download.html).
1. Installera paketet med `dpkg`.

Se [Installera på Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) för mer information.

## Installera [!DNL RabbitMQ] i CentOS

### Install Erlang

[!DNL RabbitMQ] har skrivits med språkversionen av Erlang, som måste vara installerad i samma system som [!DNL RabbitMQ].

Se [Manuell installation](https://www.erlang-solutions.com/downloads/) för mer information.

Se [[!DNL RabbitMQ]/Erlang version matrix](https://www.rabbitmq.com/which-erlang.html) för att installera rätt version.

### Installera [!DNL RabbitMQ]

The [!DNL RabbitMQ] -servern ingår i CentOS, men versionen är ofta gammal. [!DNL RabbitMQ] rekommenderar att paketet installeras från deras webbplats.

Se [!DNL RabbitMQ] installationssidan för att hämta den senaste versionen som stöds. Stöd för Adobe Commerce 2.3 och 2.4 [!DNL RabbitMQ] 3.8.x

Se [Installera på RPM-baserade Linux](https://www.rabbitmq.com/install-rpm.html) för mer information.

## Konfigurera [!DNL RabbitMQ]

Granska tjänstemannen [!DNL RabbitMQ] dokumentation för att konfigurera och hantera [!DNL RabbitMQ]. Observera följande:

* Miljövariabler
* Portåtkomst
* Standardanvändarkonton
* Starta och stoppa mäklaren
* Systembegränsningar

## Installera med [!DNL RabbitMQ] och ansluta

Om du installerar Adobe Commerce eller Magento Open Source _efter_ du installerar [!DNL RabbitMQ]lägger du till följande kommandoradsparametrar under installationen:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Var:

| Parameter | Beskrivning |
|--- |--- |
| `--amqp-host` | Värdnamnet där [!DNL RabbitMQ] är installerat. |
| `--amqp-port` | Porten som ska användas för att ansluta till [!DNL RabbitMQ]. Standardvärdet är `5672`. |
| `--amqp-user` | Användarnamn för anslutning till [!DNL RabbitMQ]. Använd inte standardanvändaren `guest`. |
| `--amqp-password` | Lösenordet för att ansluta till [!DNL RabbitMQ]. Använd inte standardlösenordet `guest`. |
| `--amqp-virtualhost` | Det virtuella värdsystemet för anslutning till [!DNL RabbitMQ]. Standardvärdet är `/`. |
| `--amqp-ssl` | Anger om anslutning ska ske till [!DNL RabbitMQ]. Standardvärdet är `false`. Om du anger värdet som true kan du läsa mer i Konfigurera SSL. |

## Anslut [!DNL RabbitMQ]

Om du redan har Adobe Commerce eller Magento Open Source installerat och vill ansluta det till [!DNL RabbitMQ], lägga till en `queue` i `<install_directory>/app/etc/env.php` så att den liknar följande:

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/'
     ),
  ),
```

Du kan också ange [!DNL RabbitMQ] konfigurationsvärden med `bin/magento setup:config:set` kommando:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

När kommandot har körts eller uppdaterats `<install_directory>/app/etc/env.php` fil med AMQP-konfigurationsvärden, kör `bin/magento setup:upgrade` för att tillämpa ändringarna och skapa de köer och utbyten som krävs i [!DNL RabbitMQ].

## Konfigurera SSL

Om du vill konfigurera stöd för SSL redigerar du `ssl` och `ssl_options` parametrarna i `<install_directory>/app/etc/env.php` så att de liknar följande:

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' =>  '/etc/pki/tls/certs/DigiCertCA.crt',
            'certfile' => '/path/to/magento/app/etc/ssl/test-rabbit.crt',
            'keyfile' => '/path/to/magento/app/etc/ssl/test-rabbit.key'
       ],
     ),
  ),
```

## Starta meddelandekökonsumenterna

När du har anslutit Adobe Commerce och [!DNL RabbitMQ]måste du starta meddelandekökonsumenterna. Se [Konfigurera meddelandeköer](../../configuration/cli/start-message-queues.md) för mer information.
