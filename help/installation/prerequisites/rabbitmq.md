---
title: Message Broker
description: Följ de här stegen för att installera och konfigurera nödvändig meddelandehanterare (till exempel  [!DNL RabbitMQ]) för lokala installationer av Adobe Commerce.
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Message Broker

Adobe Commerce använder meddelandehanteraren [!DNL RabbitMQ] med öppen källkod. Det erbjuder ett tillförlitligt, skalbart och portabelt meddelandesystem med hög tillgänglighet.

Meddelandeköer är en asynkron kommunikationsmekanism där avsändaren och mottagaren av ett meddelande inte kontaktar varandra. De behöver inte heller kommunicera med meddelandekön samtidigt. När en avsändare placerar ett meddelande i en kö lagras det tills mottagaren tar emot det.

Meddelandekösystemet måste upprättas innan du kan installera Adobe Commerce. Grundordningen är:

1. Installera [!DNL RabbitMQ] och eventuella krav.
1. Anslut [!DNL RabbitMQ] till Adobe Commerce.

>[!NOTE]
>
>Du kan använda MySQL eller [!DNL RabbitMQ] för meddelandeköbearbetning. Mer information om hur du konfigurerar meddelandekösystemet finns i [Översikt över meddelandeköer](https://developer.adobe.com/commerce/php/development/components/message-queues/). Om du använder API:t för massutskick med Adobe Commerce används [!DNL RabbitMQ] som meddelandehanterare i meddelandekösystemets konfiguration. Mer information finns i [Starta meddelandekökonsumenter](../../configuration/cli/start-message-queues.md).

## Installera [!DNL RabbitMQ] på Ubuntu

Om du vill installera [!DNL RabbitMQ] på Ubuntu 16 anger du följande kommando:

```bash
sudo apt install -y rabbitmq-server
```

Det här kommandot installerar även de nödvändiga Erlang-paketen.

Om du har en äldre version av Ubuntu rekommenderar [!DNL RabbitMQ] att du installerar paketet från deras webbplats.

1. Hämta .deb-paketet från [kanitmq-server](https://www.rabbitmq.com/download.html).
1. Installera paketet med `dpkg`.

Mer information finns i [Installera på Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html).

## Installera [!DNL RabbitMQ] på CentOS

### Install Erlang

[!DNL RabbitMQ] skrevs med programmeringsspråket Erlang, som måste installeras på samma system som [!DNL RabbitMQ].

Mer information finns i [Manuell installation](https://www.erlang-solutions.com/downloads/).

Se versionsmatrisen [[!DNL RabbitMQ] för ](https://www.rabbitmq.com/which-erlang.html)/Erlang för att installera rätt version.

### Installera [!DNL RabbitMQ]

Servern [!DNL RabbitMQ] ingår i CentOS, men versionen är ofta gammal. [!DNL RabbitMQ] rekommenderar att du installerar paketet från deras webbplats.

Gå till installationssidan för [!DNL RabbitMQ] om du vill ha den senaste versionen som stöds. Stöd för Adobe Commerce 2.3 och 2.4 [!DNL RabbitMQ] 3.8.x.

Mer information finns i [Installera på RPM-baserade Linux](https://www.rabbitmq.com/install-rpm.html).

## Konfigurera [!DNL RabbitMQ]

Granska den officiella [!DNL RabbitMQ]-dokumentationen för att konfigurera och hantera [!DNL RabbitMQ]. Observera följande:

* Miljövariabler
* Portåtkomst
* Standardanvändarkonton
* Starta och stoppa mäklaren
* Systembegränsningar

## Installera med [!DNL RabbitMQ] och anslut

Om du installerar Adobe Commerce _efter_ att du har installerat [!DNL RabbitMQ] lägger du till följande kommandoradsparametrar under installationen:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Var:

| Parameter | Beskrivning |
|--- |--- |
| `--amqp-host` | Värdnamnet där [!DNL RabbitMQ] är installerat. |
| `--amqp-port` | Den port som ska användas för att ansluta till [!DNL RabbitMQ]. Standardvärdet är `5672`. |
| `--amqp-user` | Användarnamnet för anslutning till [!DNL RabbitMQ]. Använd inte standardanvändaren `guest`. |
| `--amqp-password` | Lösenordet för att ansluta till [!DNL RabbitMQ]. Använd inte standardlösenordet `guest`. |
| `--amqp-virtualhost` | Det virtuella värdsystemet för anslutning till [!DNL RabbitMQ]. Standardvärdet är `/`. |
| `--amqp-ssl` | Anger om anslutningen till [!DNL RabbitMQ] ska upprättas. Standardvärdet är `false`. Om du anger värdet som true kan du läsa mer i Konfigurera SSL. |

## Anslut [!DNL RabbitMQ]

Om du redan har installerat Adobe Commerce och vill ansluta det till [!DNL RabbitMQ] lägger du till ett `queue` -avsnitt i `<install_directory>/app/etc/env.php`-filen så att det liknar följande:

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

Du kan också ange [!DNL RabbitMQ]-konfigurationsvärden med kommandot `bin/magento setup:config:set`:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

När du har kört kommandot eller uppdaterat filen `<install_directory>/app/etc/env.php` med AMQP-konfigurationsvärden kör du `bin/magento setup:upgrade` för att tillämpa ändringarna och skapa de nödvändiga köerna och utbytena i [!DNL RabbitMQ].

## Konfigurera SSL

Om du vill konfigurera stöd för SSL redigerar du parametrarna `ssl` och `ssl_options` i filen `<install_directory>/app/etc/env.php` så att de liknar följande:

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

När du har anslutit Adobe Commerce och [!DNL RabbitMQ] måste du starta meddelandets kunder. Mer information finns i [Konfigurera meddelandeköer](../../configuration/cli/start-message-queues.md).
