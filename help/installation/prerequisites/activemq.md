---
title: Message Broker (ActiveMQ Artemis)
description: Följ de här stegen för att installera och konfigurera Apache ActiveMQ Artemis meddelandebroker för lokala installationer av Adobe Commerce.
source-git-commit: aee02c258acaeb7a248e10b867017ef8f72b544d
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Message Broker (ActiveMQ Artemis)

Adobe Commerce stöder även ActiveMQ Artemis-meddelandehanterare med öppen källkod via STOMP (Simple Text Oriented Messaging Protocol). Det är ett tillförlitligt och skalbart meddelandesystem som ger flexibilitet för STOMP-baserade integreringar.


>[!NOTE]
>
>ActiveMQ Artemis introducerades i Adobe Commerce 2.4.6 och senare. Mer information om hur du installerar ActiveMQ-artemis i Adobe Commerce i molninfrastrukturprojekt finns i [Konfigurera ActiveMQ-tjänsten](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/activemq) i *Commerce on Cloud Guide*.

Meddelandeköer är en asynkron kommunikationsmekanism där avsändaren och mottagaren av ett meddelande inte kontaktar varandra. De behöver inte heller kommunicera med meddelandekön samtidigt. När en avsändare placerar ett meddelande i en kö lagras det tills mottagaren tar emot det.

Meddelandekösystemet måste upprättas innan du kan installera Adobe Commerce. Grundordningen är:

1. Installera Apache ActiveMQ Artemis och eventuella krav.
1. Anslut ActiveMQ till Adobe Commerce.

>[!NOTE]
>
>Du kan använda MySQL, ActiveMQ eller [!DNL RabbitMQ] för meddelandeköbearbetning. Mer information om hur du konfigurerar meddelandekösystemet finns i [Översikt över meddelandeköer](https://developer.adobe.com/commerce/php/development/components/message-queues/). Om du använder API:t för massutskick med Adobe Commerce används [!DNL RabbitMQ] som meddelandehanterare i meddelandekösystemets konfiguration. Mer information finns i [Starta meddelandekökonsumenter](../../configuration/cli/start-message-queues.md).

>[!TIP]
>
>Kontrollera alltid [hämtningssidan för Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/download/) för den senaste stabila versionen innan installationen. Exemplen i det här dokumentet använder version 2.42.0, som var den senaste stabila versionen från september 2025.


## Installera ActiveMQ-objekt för Apache

Du kan installera ActiveMQ Artemis med Docker (rekommenderas för utveckling) eller manuell installation (rekommenderas för produktion).

### Alternativ 1: Dockerinstallation (rekommenderas för utveckling)

#### Förutsättningar

Kontrollera att Docker är installerat och körs på datorn.

>[!TIP]
>
>Mer information om den officiella ActiveMQ Artemis Docker-bilden finns på [Apache ActiveMQ Artemis Docker Hub](https://hub.docker.com/r/apache/activemq-artemis).

#### Installationssteg

1. Kör ActiveMQ Artemis med den officiella Docker-bilden:

   ```bash
   # Run with default configuration
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     apache/activemq-artemis:2.42.0
   ```

1. Kör med anpassade autentiseringsuppgifter:

   ```bash
   # Run with custom username/password
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     --env ARTEMIS_USER=magento \
     --env ARTEMIS_PASSWORD=magento \
     apache/activemq-artemis:2.42.0
   ```

#### Dockningshanteringskommandon

```bash
# Check container status
docker ps | grep artemis

# View logs
docker logs artemis

# Stop the container
docker stop artemis

# Start the container
docker start artemis

# Remove the container
docker rm artemis
```

#### Åtkomst till tjänster

När Docker-behållaren är igång kan du komma åt:

- **Webbkonsol**: http://localhost:8161/console (default credentials: artemis/artemis)
- **STOMP-port**: localhost:61613 (för Adobe Commerce-anslutning)

>[!NOTE]
>
>Docker-installationen rekommenderas för utveckling och testning. För produktion bör du överväga att använda manuell installation med rätt säkerhetskonfigurationer.

### Alternativ 2: Manuell installation på Ubuntu/CentOS

#### Förutsättningar

Kontrollera att Java 17 eller senare är installerat (krävs för ActiveMQ Artemis 2.42.0+).

### Installationssteg

1. Hämta och installera den senaste versionen från [Apache ActiveMQ Artemis-webbplatsen](https://activemq.apache.org/components/artemis/download/). Från och med september 2025 är den senaste stabila versionen 2.42.0:

   ```bash
   sudo mkdir -p /opt/artemis
   cd /opt/artemis
   sudo curl -O https://downloads.apache.org/activemq/activemq-artemis/2.42.0/apache-artemis-2.42.0-bin.tar.gz
   sudo tar -xzf apache-artemis-2.42.0-bin.tar.gz --strip-components=1
   sudo rm apache-artemis-2.42.0-bin.tar.gz
   ```

1. Skapa användaren `artemis` och ange ägarskap:

   ```bash
   # Create artemis user and set ownership
   sudo useradd -r -s /bin/false artemis 2>/dev/null || true
   sudo chown -R artemis:artemis /opt/artemis
   ```

1. Skapa en mäklarinstans:

   ```bash
   sudo /opt/artemis/bin/artemis create /var/lib/artemis-instance --user artemis --password artemis --allow-anonymous
   sudo chown -R artemis:artemis /var/lib/artemis-instance
   ```

1. Starta mäklaren:

   ```bash
   # Start in foreground (for testing)
   sudo /var/lib/artemis-instance/bin/artemis run
   
   # Start as background service
   sudo /var/lib/artemis-instance/bin/artemis-service start
   
   # Stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service stop
   
   # Restart the broker
   sudo /var/lib/artemis-instance/bin/artemis-service restart
   
   # Force stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service force-stop
   
   # Check broker status
   sudo /var/lib/artemis-instance/bin/artemis-service status
   ```

## Konfigurera ActiveMQ-objekt

Läs den officiella ActiveMQ Artemis-dokumentationen för att konfigurera och hantera mäklaren. Observera följande:

- Miljövariabler
- Portåtkomst (STOMP-protokoll)
- Standardanvändarkonton och autentiseringsuppgifter
- Starta och stoppa mäklaren
- Systembegränsningar och resursjustering

### Nyckelkonfigurationsfiler

- `/var/lib/artemis-instance/etc/broker.xml` - Huvudmäklarkonfiguration
- `/var/lib/artemis-instance/etc/artemis-users.properties` - Användarautentisering
- `/var/lib/artemis-instance/etc/artemis-roles.properties` - Användarroller
- `/var/lib/artemis-instance/etc/bootstrap.xml` - Bootstrap-konfiguration

### Aktivera STOMP-protokoll

Kontrollera `/var/lib/artemis-instance/etc/broker.xml` för att kontrollera att STOMP-godkännare har konfigurerats:

```xml
<acceptors>
   <acceptor name="artemis">tcp://0.0.0.0:61616?tcpSendBufferSize=1048576;tcpReceiveBufferSize=1048576;amqpMinLargeMessageSize=102400;protocols=CORE,AMQP,STOMP,HORNETQ,MQTT,OPENWIRE;useEpoll=true;amqpCredits=1000;amqpLowCredits=300;amqpDuplicateDetection=true</acceptor>
   <acceptor name="stomp">tcp://0.0.0.0:61613?protocols=STOMP</acceptor>
   <acceptor name="stomp-ssl">tcp://0.0.0.0:61617?protocols=STOMP;sslEnabled=true;keyStorePath=/path/to/keystore.jks;keyStorePassword=password</acceptor>
</acceptors>
```

Om du vill aktivera SSL på STOMP måste du lägga till `stomp-ssl`-godkännaren explicit.

## Installera med ActiveMQ Artemis och anslut

Om du installerar Adobe Commerce _efter_ att du har installerat ActiveMQ Artemis lägger du till följande kommandoradsparametrar under installationen:

```bash
--stomp-host="<hostname>" --stomp-port="61613" --stomp-user="<user_name>" --stomp-password="<password>"
```

Var:

| Parameter | Beskrivning |
|--- |--- |
| `--stomp-host` | Värdnamnet där ActiveMQ är installerat. |
| `--stomp-port` | Den port som ska användas för att ansluta till ActiveMQ. Standardvärdet är `61613`. |
| `--stomp-user` | Användarnamnet för anslutning till ActiveMQ. Använd inte standardanvändaren `artemis`. |
| `--stomp-password` | Lösenordet för anslutning till ActiveMQ. Använd inte standardlösenordet `artemis`. |
| `--stomp-ssl` | Anger om ActiveMQ ska anslutas. Standardvärdet är `false`. Om du anger värdet som true kan du läsa mer i Konfigurera SSL. |

## Connect ActiveMQ Artemis

Om du redan har en Adobe Commerce-instans med konfigurationen RabbitMQ (AMQP) i filen `<install_directory>/app/etc/env.php` och du vill ansluta den till ActiveMQ ersätter du avsnittet `queue` med STOMP så att det liknar följande:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

Du kan också ange ActiveMQ-konfigurationsvärden med kommandot `bin/magento setup:config:set` (ta bort AMQP-konfigurationen om den finns i filen `app/etc/env.php`):

```bash
bin/magento setup:config:set --stomp-host="activemq.example.com" --stomp-port="61613" --stomp-user="magento" --stomp-password="magento"
```

När du har kört kommandot eller uppdaterat filen `<install_directory>/app/etc/env.php` med STOMP-konfigurationsvärden kör du `bin/magento setup:upgrade` för att tillämpa ändringarna och skapa de nödvändiga köerna i ActiveMQ.

## Konfigurera SSL

Om du vill konfigurera stöd för SSL redigerar du parametrarna `ssl` och `ssl_options` i filen `<install_directory>/app/etc/env.php` så att de liknar följande:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61617',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' => '/etc/pki/tls/certs/DigiCertCA.crt',
            'local_cert' => '/path/to/magento/app/etc/ssl/test-activemq.crt', // Optional: Client certificate for mutual SSL
            'local_pk' => '/path/to/magento/app/etc/ssl/test-activemq.key', // Optional: Client private key for mutual SSL
            'passphrase' => 'client_key_password', // Optional: Passphrase for client private key
            'verify_peer' => true,
            'verify_peer_name' => true,
            'allow_self_signed' => false
       ],
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

### SSL-konfigurationsalternativ

| Alternativ | Beskrivning | Standard |
|--- |--- |--- |
| `verify_peer` | Verifiera mäklarens SSL-certifikat | `true` |
| `verify_peer_name` | Kontrollera att mäklarens värdnamn matchar certifikatet | `true` |
| `allow_self_signed` | Tillåt självsignerade certifikat | `false` |
| `cafile` | Sökväg till certifikatutfärdarcertifikatfil för mäklarverifiering | Krävs för SSL |
| `certfile` | Sökväg till klientcertifikatfil (för gemensam SSL) | Valfritt |
| `keyfile` | Sökväg till klientens privata nyckelfil (för gemensam SSL) | Valfritt |
| `passphrase` | Lösenfras för klientens privata nyckel | Valfritt |

### SSL-konfiguration för utveckling

I utvecklingsmiljöer kan du använda avspända SSL-inställningar:

```php
'ssl_options' => [
    'verify_peer' => false,
    'verify_peer_name' => false,
    'allow_self_signed' => true
]
```

## Prestandajustering

ActiveMQ Artemis har flera alternativ för prestandajustering:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',
      'user' => 'artemis',
      'password' => 'artemis',
      // Performance options
      'heartbeat_send' => 10000,      // Send heartbeat every 10 seconds
      'heartbeat_receive' => 10000,   // Expect heartbeat every 10 seconds
      'read_timeout' => 250000,       // 250ms read timeout
     ),
  ),
```

## Övervakning och hantering

### Webbkonsol

ActiveMQ Artemis har en webbaserad hanteringskonsol som är tillgänglig på:
- URL: `http://localhost:8161/console`
- Standardautentiseringsuppgifter: `artemis/artemis`

## Felsökning

### Vanliga problem

1. **Anslutningen nekades**: Kontrollera att ActiveMQ-artemis körs och att STOMP-accepteraren har konfigurerats.
1. **Autentiseringen misslyckades**: Kontrollera användarnamn/lösenord i både Service Broker-konfigurationen och `env.php`-filen.
1. **SSL-handskakning misslyckades**: Verifiera SSL-certifikat och konfiguration.




### Verifiera STOMP-anslutning

Testa STOMP-anslutning med telnet:

```bash
telnet localhost 61613
```

En anslutning bör upprättas. Så här testar du med ett STOMP-kommando:

```bash
# Test basic STOMP connection
echo -e "CONNECT\nhost:localhost\n\n\x00" | telnet localhost 61613
```

Förväntade utdata ska visa upprättad anslutning och STOMP-protokollsvar.

## Starta meddelandekökonsumenterna

När du har anslutit Adobe Commerce och ActiveMQ Artemis måste du starta meddelandets kunder. Mer information finns i [Konfigurera meddelandeköer](../../configuration/cli/start-message-queues.md).

