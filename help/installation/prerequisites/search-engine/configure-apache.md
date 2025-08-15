---
title: Konfigurera Apache för sökmotorn
description: Följ de här stegen för att konfigurera en sökmotor med webbservern Apache för lokala installationer av Adobe Commerce.
feature: Install, Search
exl-id: b35c95a7-0c00-48e5-b37d-7c9e17feebec
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Konfigurera Apache för sökmotorn

{{$include /help/_includes/web-server-communication.md}}

## Konfigurera en proxy

>[!NOTE]
>
>Stöd för OpenSearch lades till i 2.4.4. OpenSearch är en kompatibel del av Elasticsearch. Mer information finns i [Migrera Elasticsearch till OpenSearch](../../../upgrade/prepare/opensearch-migration.md).

I det här avsnittet beskrivs hur du konfigurerar Apache som en *osäker* -proxy så att Adobe Commerce kan använda en sökmotor som körs på den här servern. I det här avsnittet beskrivs inte konfigurering av grundläggande HTTP-autentisering. Det beskrivs i [Säker kommunikation med Apache](#secure-communication-with-apache).

>[!NOTE]
>
>Orsaken till att proxyn inte skyddas i det här exemplet är att det är enklare att konfigurera och verifiera. Du kan använda TLS med den här proxyn. Om du vill göra det måste du lägga till proxyinformationen i den säkra virtuella värdkonfigurationen.

### Konfigurera en proxy för Apache 2.4

I det här avsnittet beskrivs hur du konfigurerar en proxy med hjälp av ett virtuellt värdsystem.

1. Aktivera `mod_proxy` enligt följande:

   ```bash
   a2enmod proxy_http
   ```

1. Öppna `/etc/apache2/sites-available/000-default.conf` med en textredigerare
1. Lägg till följande direktiv högst upp i filen:

   ```conf
   Listen 8080
   ```

1. Lägg till följande längst ned i filen:

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. Starta om Apache:

   ```bash
   service apache2 restart
   ```

1. Kontrollera att proxyn fungerar genom att ange följande kommando:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Om du till exempel använder Elasticsearch och din proxy använder port 8080:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   Meddelanden som liknar följande för att visa om det lyckades:

   ```
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Säker kommunikation med Apache

I det här avsnittet beskrivs hur du skyddar kommunikationen mellan Apache och sökmotorn med hjälp av [HTTP Basic](https://datatracker.ietf.org/doc/html/rfc2617) -autentisering med Apache. Mer information finns i följande resurser:

* [Autentiserings- och auktoriseringsjälvstudiekurs för Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

Se något av följande avsnitt:

* [Skapa en lösenordsfil](#create-a-password)
* [Konfigurera din säkra virtuella värd](#secure-communication-with-apache)

### Skapa ett lösenord

Av säkerhetsskäl kan du hitta lösenordsfilen var som helst, förutom webbserverns dokumentmapp. I det här exemplet visas hur du sparar lösenordsfilen i en ny katalog.

#### Installera htpassword om det behövs

Kontrollera först om du har Apache `htpasswd`-verktyget installerat enligt följande:

1. Ange följande kommando för att avgöra om `htpasswd` redan är installerat:

   ```bash
   which htpasswd
   ```

   Om en sökväg visas installeras den. Om kommandot inte returnerar några utdata installeras inte `htpasswd`.

1. Installera `htpasswd` om det behövs:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### Skapa en lösenordsfil

Ange följande kommandon som en användare med behörigheten `root`:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

Plats

* `<username>` kan vara:

   * Konfigurera cron: webbserveranvändaren eller en annan användare.

  I det här exemplet använder vi webbserveranvändaren, men det är upp till dig att välja användare.

   * Konfigurera Elasticsearch: användaren har namnet `magento_elasticsearch` i det här exemplet

* `<password file name>` måste vara en dold fil (börjar med `.`) och ska återspegla användarens namn. Mer information finns i exemplen senare i det här avsnittet.

Följ instruktionerna på skärmen för att skapa ett lösenord för användaren.

#### Exempel

**Exempel 1: cron**
Du måste konfigurera autentisering för endast en användare för cron. I det här exemplet använder vi webbserveranvändaren. Om du vill skapa en lösenordsfil för webbserveranvändaren anger du följande kommandon:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**Exempel 2: Elasticsearch**
Du måste konfigurera autentisering för två användare: en med åtkomst till nginx och en med åtkomst till Elasticsearch. Om du vill skapa lösenordsfiler för dessa användare anger du följande kommandon:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### Lägg till ytterligare användare

Om du vill lägga till en annan användare i lösenordsfilen anger du följande kommando som en användare med `root`-behörighet:

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Säker kommunikation med Apache

I det här avsnittet beskrivs hur du konfigurerar [grundläggande HTTP-autentisering](https://httpd.apache.org/docs/2.2/howto/auth.html). Användning av TLS och HTTP Basic-autentisering tillsammans förhindrar alla från att kommunicera med Elasticsearch eller OpenSearch eller med programservern.

I det här avsnittet beskrivs hur du anger vilka som får åtkomst till Apache-servern.

1. Använd en textredigerare för att lägga till följande innehåll i det säkra virtuella värdsystemet.

   * Apache 2.4: Redigera `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elasticsearch Server" # or OpenSearch Server
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. Om du har lagt till föregående till din säkra virtuella värd tar du bort `Listen 8080` och de `<VirtualHost *:8080>`-direktiv som du har lagt till tidigare till din osäkra virtuella värd.

1. Spara ändringarna, avsluta textredigeraren och starta om Apache:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

#### Verifiera

{{$include /help/_includes/verify-secure-communication.md}}
