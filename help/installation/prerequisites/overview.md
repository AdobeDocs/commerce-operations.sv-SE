---
title: Lokala installationskrav
description: Läs mer om vilka programvaruberoenden som krävs för lokala installationer av Adobe Commerce och Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 1%

---


# Lokala installationskrav

Innan du installerar Adobe Commerce eller Magento Open Source måste du göra följande:

* Konfigurera en eller flera värdar som uppfyller [systemkrav](../system-requirements.md).
* Om du konfigurerar mer än en webbnod med belastningsutjämning konfigurerar och testar du den delen av systemet _före_ du installerar programmet.
* Se till att du kan säkerhetskopiera hela systemet vid olika tillfällen under installationen, så att du kan återställa det om det uppstår problem.

>[!NOTE]
>
>Vi antar att du installerar Adobe Commerce eller Magento Open Source i en **utvecklingsmiljö** som du har rotanvändaråtkomst till datorn, **och** att maskinen inte behöver vara mycket säker. Om du konfigurerar en säkrare dator bör du kontakta en nätverksadministratör för att få mer hjälp.

Vi rekommenderar starkt att du uppdaterar och uppgraderar ditt operativsystem. Dessa uppgraderingar kan ge säkerhets- och programfixar som kan förhindra framtida problem. Vet du inte vad det innebär? Kolla in vår [installationsöversikt](../overview.md).

Ange följande kommandon som en användare med `root` behörighet:

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

Adobe Commerce och Magento Open Source stöder Apache version 2.4 enligt följande:

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Information om hur du installerar eller uppgraderar Apache finns i [Apache](web-server/apache.md).

### PHP

Se [systemkrav](../system-requirements.md) för de versioner av PHP som stöds och [PHP] för PHP-krav.

### MySQL

```bash
mysql -u <database root user or database owner name> -p
```

Exempel:

```bash
mysql -u magento -p
```

Kontrollera att du har rätt version av MySQL för den version av Adobe Commerce eller Magento Open Source som du installerar ([här för att se vilka versioner som stöds](../system-requirements.md). Följande resultat anger vilken version du kör.)

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

Typ `help` eller `\h` om du behöver hjälp. Typ `\c` för att rensa den aktuella inmatningssatsen.

Retur `exit` på `mysql>` fråga om du vill avsluta.

Information om hur du installerar eller uppgraderar MySQL finns i [MySQL](database/mysql.md).

### Elasticsearch eller OpenSearch

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

Exempel:

```bash
curl -XGET 'localhost:9200'
```

```terminal
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
