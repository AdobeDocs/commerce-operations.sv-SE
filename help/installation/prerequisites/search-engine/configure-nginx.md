---
title: Konfigurera Nginx för sökmotorn
description: Följ de här stegen för att konfigurera en sökmotor med Nginx-webbservern för lokala installationer av Adobe Commerce och Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---


# Konfigurera Nginx för sökmotorn

{{$include /help/_includes/web-server-communication.md}}

## Konfigurera en proxy

>[!NOTE]
>
>Stöd för OpenSearch lades till i 2.4.4. OpenSearch är en kompatibel gaffel för Elasticsearch. Se [Migrera Elasticsearch till OpenSearch](../../../upgrade/prepare/opensearch-migration.md) för mer information.

I det här avsnittet beskrivs hur du konfigurerar index som *osäker* så att Adobe Commerce kan använda en sökmotor som körs på den här servern. I det här avsnittet behandlas inte konfiguration av grundläggande HTTP-autentisering. som diskuteras i [Säker kommunikation med nginx](#secure-communication-with-nginx).

>[!NOTE]
>
>Orsaken till att proxyn inte skyddas i det här exemplet är att det är enklare att konfigurera och verifiera. Du kan använda TLS med denna proxy om du vill; Om du vill göra det måste du lägga till proxyinformationen i den säkra serverblockkonfigurationen.

### Ange ytterligare konfigurationsfiler i den globala konfigurationen

Se till att din globala `/etc/nginx/nginx.conf` innehåller följande rad så att de andra konfigurationsfilerna som beskrivs i följande avsnitt läses in:

```conf
include /etc/nginx/conf.d/*.conf;
```

### Konfigurera nginx som proxy

I det här avsnittet beskrivs hur du anger vilka som ska få åtkomst till Nginx-servern.

1. Skapa en fil med en textredigerare `/etc/nginx/conf.d/magento_es_auth.conf` med följande innehåll:

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. Starta om nginx:

   ```bash
   service nginx restart
   ```

1. Kontrollera att proxyn fungerar genom att ange följande kommando:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Om din proxy till exempel använder port 8080:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   Meddelanden som liknar följande för att visa om det lyckades:

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Säker kommunikation med nginx

I det här avsnittet beskrivs hur du konfigurerar [Grundläggande HTTP-autentisering](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) med din säkra proxy. Användning av TLS och HTTP Basic-autentisering tillsammans förhindrar alla från att kommunicera med Elasticsearch eller OpenSearch eller med programservern.

Eftersom ursprungligt stöd för HTTP Basic-autentisering rekommenderas det, till exempel, över [Sammanfattad autentisering](https://www.nginx.com/resources/wiki/modules/auth_digest/)som inte rekommenderas i produktionen.

Ytterligare resurser:

* [Ställa in lösenordsautentisering med Nginx på Ubuntu 14.04 (Digital Ocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Grundläggande HTTP-autentisering med Nginx (THTOForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Exempel på Nginx-konfigurationer för Elasticsearch](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

Mer information finns i följande avsnitt:

* [Skapa lösenord](#create-a-password)
* [Konfigurera åtkomst till nginx](#set-up-access-to-nginx)
* [Konfigurera en begränsad kontext för sökmotorn](#set-up-a-restricted-context-for-the-search-engine)
* [Verifiera att kommunikationen är säker](#secure-communication-with-nginx)

### Skapa ett lösenord

Vi rekommenderar att du använder Apache `htpasswd` för att koda lösenord för en användare med åtkomst till Elasticsearch eller OpenSearch (namngivna `magento_elasticsearch` i det här exemplet).

Så här skapar du ett lösenord:

1. Ange följande kommando för att avgöra om `htpasswd` är redan installerat:

   ```bash
   which htpasswd
   ```

   Om en sökväg visas är den installerad; om kommandot inte returnerar några utdata, `htpasswd` är inte installerat.

1. Installera vid behov `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. Skapa en `/etc/nginx/passwd` katalog där lösenord ska lagras:

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >Av säkerhetsskäl `<filename>` bör döljas, måste alltså börja med en punkt.

1. *(Valfritt).* Om du vill lägga till en annan användare i lösenordsfilen anger du samma kommando utan `-c` (skapa) alternativ:

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. Verifiera att innehållet i `/etc/nginx/passwd` stämmer.

### Konfigurera åtkomst till nginx

I det här avsnittet beskrivs hur du anger vilka som ska få åtkomst till Nginx-servern.

>[!WARNING]
>
>Exemplet som visas är för *osäker* proxy. Om du vill använda en säker proxy lägger du till följande innehåll (förutom lyssningsporten) i det säkra serverblocket.

Använd en textredigerare för att ändra `/etc/nginx/conf.d/magento_es_auth.conf` (osäkert) eller ditt säkra serverblock med följande innehåll:

```conf
server {
  listen 8080;
  server_name 127.0.0.1;

  location / {
   limit_except HEAD {
      auth_basic "Restricted";
      auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   }
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  location /_aliases {
   auth_basic "Restricted";
   auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  include /etc/nginx/auth/*.conf;
}
```

>[!NOTE]
>
>Sökmotorns avlyssningsport som visas i föregående exempel är endast exempel. Av säkerhetsskäl rekommenderar vi att du använder en lyssningsport som inte är standard.

### Konfigurera en begränsad kontext för sökmotorn

I det här avsnittet beskrivs hur du anger vilka som får åtkomst till sökmotorservern.

1. Ange följande kommando för att skapa en katalog där autentiseringskonfigurationen ska lagras:

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. Skapa en fil med en textredigerare `/etc/nginx/auth/magento_elasticsearch.conf` med följande innehåll:

   ```conf
   location /elasticsearch {
   auth_basic "Restricted - elasticsearch";
   auth_basic_user_file /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   }
   ```

1. Om du konfigurerar en säker proxy tar du bort `/etc/nginx/conf.d/magento_es_auth.conf`.
1. Starta om nästa och fortsätt med nästa avsnitt:

   ```bash
   service nginx restart
   ```

#### Verifiera

{{$include /help/_includes/verify-secure-communication.md}}
