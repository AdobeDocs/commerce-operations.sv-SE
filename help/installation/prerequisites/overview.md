---
title: Lokala installationskrav
description: Läs mer om vilka programvaruberoenden som krävs för lokala installationer av Adobe Commerce.
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 1%

---

# Lokala installationskrav

Innan du installerar Adobe Commerce måste du göra följande:

* Konfigurera en eller flera värdar som uppfyller [systemkraven](../system-requirements.md).
* Om du konfigurerar mer än en webbnod med belastningsutjämning konfigurerar och testar du den delen av systemet _innan_ du installerar programmet.
* Se till att du kan säkerhetskopiera hela systemet vid olika tillfällen under installationen, så att du kan återställa det om det uppstår problem.

>[!NOTE]
>
>Vi antar att du installerar Adobe Commerce i en **utvecklingsmiljö**, att du har rotanvändaråtkomst till datorn, **och** att datorn inte behöver vara mycket säker. Om du konfigurerar en säkrare dator bör du kontakta en nätverksadministratör för att få mer hjälp.

Vi rekommenderar starkt att du uppdaterar och uppgraderar ditt operativsystem. Dessa uppgraderingar kan ge säkerhets- och programfixar som kan förhindra framtida problem. Vet du inte vad det här betyder? Se vår [installationsöversikt](../overview.md).

Ange följande kommandon som en användare med behörigheten `root`:

* Ubuntu

  ```bash
  apt-get update
  ```

  ```bash
  apt-get upgrade
  ```

* CentOS

  ```bash
  yum -y update
  ```

  ```bash
  yum -y upgrade
  ```

## Kravkontroll

Ange följande kommandon om du vill kontrollera systemkraven:

### Apache

CentOS: `httpd -v`

Ubuntu: `apache2 -v`

Adobe Commerce har stöd för Apache version 2.4 enligt följande:

```
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Mer information om hur du installerar eller uppgraderar Apache finns i [Apache](web-server/apache.md).

### PHP

Se [systemkraven](../system-requirements.md) för de versioner av PHP som stöds och [PHP](../system-requirements.md#php-settings) för PHP-kraven.

### MySQL

Kontrollera att du har en kompatibel version av MySQL för den version av Adobe Commerce som du installerar. Mer information om vilka versioner som stöds finns i [Systemkrav](../system-requirements.md).

```bash
mysql -u <database root user or database owner name> -p
```

Exempel:

```bash
mysql -u magento -p
```

Följande resultat anger vilken version du kör.

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

Skriv `help` eller `\h` om du vill ha hjälp. Skriv `\c` för att rensa den aktuella indatasatsen.

Ange `exit` vid `mysql>`-prompten för att avsluta.

Mer information om hur du installerar eller uppgraderar MySQL finns i [MySQL](database/mysql.md).

### Sökmotor

Så här verifierar du OpenSearch-installationen:

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

Så här verifierar du installationen av Elasticsearch:

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

Exempel:

```bash
curl -XGET 'localhost:9200'
```

```
{
  "name" : "Z0S2B05",
  "cluster_name" : "elasticsearch_myname",
  "cluster_uuid" : "V-kpikRJQHudN-Wzdt-IrQ",
  "version" : {
    "number" : "6.8.7",
    "build_flavor" : "oss",
    "build_type" : "tar",
    "build_hash" : "c63e621",
    "build_date" : "2020-02-26T14:38:01.193138Z",
    "build_snapshot" : false,
    "lucene_version" : "7.7.2",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
```
