---
title: Message Broker
description: Följ de här stegen för att installera och konfigurera nödvändig meddelandehanterare (till exempel RabbitMQ) för lokala installationer av Adobe Commerce och Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---


# Message Broker

Adobe Commerce använder den öppna meddelandehanteraren RabbitMQ. Det erbjuder ett tillförlitligt, skalbart och portabelt meddelandesystem med hög tillgänglighet.

Meddelandeköer är en asynkron kommunikationsmekanism där avsändaren och mottagaren av ett meddelande inte kontaktar varandra. De behöver inte heller kommunicera med meddelandekön samtidigt. När en avsändare placerar ett meddelande i en kö lagras det tills mottagaren tar emot det.

Meddelandekösystemet måste upprättas innan du kan installera Adobe Commerce eller Magento Open Source. Den grundläggande sekvensen är:

1. Installera RabbitMQ och eventuella krav.
1. Anslut RabbitMQ till Adobe Commerce eller Magento Open Source.

>[!NOTE]
>
>Du kan använda MySQL eller RabbitMQ för meddelandeköbearbetning. Mer information om hur du konfigurerar meddelandekösystemet finns i [Översikt över meddelandeköer](https://developer.adobe.com/commerce/php/development/components/message-queues/). Om du använder API:t för massutskick med Adobe Commerce används som standard systemets konfiguration för meddelandekön med RabbitMQ som meddelandehanterare. Se [Starta användare i meddelandekön](../../configuration/cli/start-message-queues.md) för mer information.

## Installera RabbitMQ på Ubuntu

Om du vill installera RabbitMQ i Ubuntu 16 anger du följande kommando:

```bash
sudo apt install -y rabbitmq-server
```

Det här kommandot installerar även de nödvändiga Erlang-paketen.

Om du har en äldre version av Ubuntu rekommenderar RabbitMQ att du installerar paketet från deras webbplats.

1. Hämta .deb-paketet från [kanitmq-server](https://www.rabbitmq.com/download.html).
1. Installera paketet med `dpkg`.

Se [Installera på Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) för mer information.

## Installera RabbitMQ i CentOS

### Install Erlang

RabbitMQ skrevs med programmeringsspråket Erlang, som måste vara installerat på samma system som RabbitMQ.

Se [Manuell installation](https://www.erlang-solutions.com/downloads/) för mer information.

Se [Versionsmatris för RabbitMQ/Erlang](https://www.rabbitmq.com/which-erlang.html) för att installera rätt version.

### Installera RabbitMQ

RabbitMQ-servern ingår i CentOS, men versionen är ofta gammal. RabbitMQ rekommenderar att paketet installeras från deras webbplats.

Se installationssidan för RabbitMQ för att få den senaste versionen som stöds. Adobe Commerce och Magento Open Source 2.3 och 2.4 har stöd för RabbitMQ 3.8.x.

Se [Installera på RPM-baserade Linux](https://www.rabbitmq.com/install-rpm.html) för mer information.

## Konfigurera RabbitMQ

Granska den officiella dokumentationen för RabbitMQ för att konfigurera och hantera RabbitMQ. Observera följande:

* Miljövariabler
* Portåtkomst
* Standardanvändarkonton
* Starta och stoppa mäklaren
* Systembegränsningar

## Installera med RabbitMQ och anslut

Om du installerar Adobe Commerce eller Magento Open Source _efter_ Om du installerar RabbitMQ lägger du till följande kommandoradsparametrar under installationen:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Var:

| Parameter | Beskrivning |
|--- |--- |
| `--amqp-host` | Värdnamnet där RabbitMQ är installerat. |
| `--amqp-port` | Den port som ska användas för att ansluta till RabbitMQ. Standardvärdet är `5672`. |
| `--amqp-user` | Användarnamnet för anslutning till RabbitMQ. Använd inte standardanvändaren `guest`. |
| `--amqp-password` | Lösenordet för att ansluta till RabbitMQ. Använd inte standardlösenordet `guest`. |
| `--amqp-virtualhost` | Det virtuella värdsystemet för anslutning till RabbitMQ. Standardvärdet är `/`. |
| `--amqp-ssl` | Anger om anslutning till RabbitMQ ska ske. Standardvärdet är `false`. Om du anger värdet som true kan du läsa mer i Konfigurera SSL. |

## Connect RabbitMQ

Om du redan har installerat Adobe Commerce eller Magento Open Source och vill ansluta det till RabbitMQ lägger du till en `queue` i `<install_directory>/app/etc/env.php` så att den liknar följande:

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

Du kan också ange konfigurationsvärden för RabbitMQ med `bin/magento setup:config:set` kommando:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

När kommandot har körts eller uppdaterats `<install_directory>/app/etc/env.php` fil med AMQP-konfigurationsvärden, kör `bin/magento setup:upgrade` för att tillämpa ändringarna och skapa de köer och utbyten som behövs i RabbitMQ.

## Konfigurera SSL

Om du vill konfigurera stöd för SSL redigerar du `ssl` och `ssl_options` parametrar i `<install_directory>/app/etc/env.php` så att de liknar följande:

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

När du har anslutit Adobe Commerce och RabbitMQ måste du starta meddelandets kunder. Se [Konfigurera meddelandeköer](../../configuration/cli/start-message-queues.md) för mer information.
