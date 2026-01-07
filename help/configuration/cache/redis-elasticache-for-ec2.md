---
title: Konfigurera Redis med AWS ElastiCache
description: Läs om hur du använder AWS ElastiCache i stället för en lokal Redis-instans för Commerce-instanser som finns på EC2. Upptäck kommandoradskonfiguration, konfigurationsalternativ och valideringstekniker.
feature: Configuration, Cache
source-git-commit: 908796587e78b80d699354c0506ca948d0f37518
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# Konfigurera Redis med AWS ElastiCache

Från och med Commerce 2.4.3 kan instanser som finns på Amazon EC2 använda en AWS ElastiCache i stället för en lokal Redis-instans.

>[!WARNING]
>
>Detta avsnitt gäller endast för Commerce-instanser som körs på Amazon EC2 VPC. Det fungerar inte för lokala anläggningar.

## Förutsättningar

- **Skapa ett serverlöst Redis OSS-cacheminne** - Skapa Redis-cacheminnet i samma region och VPC för EC2-instansen från AWS Management Console. Instruktioner finns i [dokumentationen för AWS Elasticache]&#x200B;(https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html.

- **Verifiera anslutningen till din EC2 Commerce-instans**

   - Öppna en SSH-anslutning till din EC2-instans
   - Installera Redis-klienten på EC2-instansen:

     ```bash
     sudo apt-get install redis
     ```

   - Lägg till en inkommande regel i EC2-säkerhetsgruppen: Typ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Lägg till en inkommande regel i säkerhetsgruppen för kluster i ElastiCache: typ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Anslut till Redis CLI:

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Konfigurera Commerce att använda klustret

Commerce har stöd för flera typer av cachelagringskonfigurationer. Vanligtvis är cachelagringskonfigurationerna uppdelade mellan klientdel och serverdel. Cachelagring för klientdel klassificeras som `default`, som används för alla cachetyper. Du kan anpassa eller dela upp i cacheminnen på lägre nivå för att få bättre prestanda. En vanlig Redis-konfiguration separerar standardcachen och sidcachen till sin egen Redis-databas (RDB).

Kör `setup`-kommandon för att ange Redis-slutpunkter.

Så här konfigurerar du Commerce för Redis som standardcachelagring:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Så här konfigurerar du Commerce för Redis-sidcache:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Så här konfigurerar du Commerce att använda Redis för sessionslagring:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## Verifiera anslutningen

**Så här verifierar du att Commerce pratar med ElastiCache**:

1. Öppna en SSH-anslutning till Commerce EC2-instansen.
1. Starta Redis-skärmen.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Öppna en sida i användargränssnittet för Commerce.
1. Verifiera [cacheutdata](#verify-the-redis-connection) i terminalen.
