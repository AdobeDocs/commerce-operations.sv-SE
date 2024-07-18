---
title: Krav för sökmotor
description: Följ de här stegen för att installera och konfigurera sökmotorprogram som stöds för lokala installationer av Adobe Commerce.
feature: Install, Search
exl-id: 44ea638a-7200-4269-be1b-b0851de2c4f4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Krav för sökmotor

Från och med Adobe Commerce 2.4 måste alla installationer vara konfigurerade att använda [Elasticsearch](https://www.elastic.co) eller [OpenSearch](https://opensearch.org/) som katalogsökningslösning.

>[!NOTE]
>
>Stöd för OpenSearch lades till i 2.4.4. OpenSearch är en kompatibel gaffel för Elasticsearch. Alla instruktioner för att konfigurera Elasticsearch 7 gäller för OpenSearch. [Migrera från Elasticsearch till OpenSearch](../../../upgrade/prepare/opensearch-migration.md) ger vägledning om hur du går över till OpenSearch.

## Version som stöds

Du måste installera och konfigurera antingen Elasticsearch eller OpenSearch innan du installerar Adobe Commerce 2.4.4 och senare.

Se [Systemkraven](../../system-requirements.md) för specifik versionsinformation.

## Rekommenderad konfiguration

Vi rekommenderar följande:

* [Konfigurera nginx för sökmotorn](configure-nginx.md)
* [Konfigurera Apache för sökmotorn](configure-apache.md)

## Installationsplats

Följande uppgifter förutsätter att du har konfigurerat systemet enligt följande diagram:

![Sökmotordiagram](../../../assets/installation/search-engine-config.svg)

I bilden ovan visas:

* Commerce-programmet och sökmotorn installeras på olika värdar.

  Körning på separata värdar kräver att proxering fungerar. (Att klustra sökmotorn ligger utanför den här handbokens omfång, men du hittar mer information i [Elasticsearch klusterdokumentationen](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).)

* Varje värd har en egen webbserver. Webbservrarna behöver inte vara samma.

  Commerce kan till exempel köra Apache och sökmotorn kan köra nginx.

* Båda webbservrarna använder TLS (Transport Layer Security).

  Att konfigurera TLS ligger utanför vår dokumentation.

Sökbegäranden behandlas på följande sätt:

1. En sökbegäran från en användare tas emot av Commerce webbserver som vidarebefordrar den till sökmotorservern.

   Du konfigurerar sökmotorn så att den ansluter till proxyns värd och port. Vi rekommenderar webbserverns SSL-port (som standard 443).

1. Sökmotorns webbserver (lyssnar på port 443) proxyskickar begäran till sökmotorservern (som standard avlyssnar den port 9200).

1. Åtkomsten till sökmotorn skyddas ytterligare av grundläggande HTTP-autentisering. För att en begäran ska kunna nå sökmotorn måste den resa över SSL *och* ange ett giltigt användarnamn och lösenord.

1. Sökmotorn bearbetar begäran.

1. Kommunikationen returneras längs samma väg, och webbservern Elasticsearch fungerar som en säker omvänd proxy.

## Förutsättningar

De uppgifter som behandlas i detta avsnitt kräver följande:

* [Brandvägg och SELinux](#firewall-and-selinux)
* [Installera Java Software Development Kit (JDK)](#install-the-java-software-development-kit)
* [Installera sökmotorn](#install-the-search-engine)
* [Uppgraderar Elasticsearch](#upgrading-elasticsearch)

### Brandvägg och SELinux

Säkerhetsrelaterad programvara (iptables, SELinux, AppArmor) kan som standard konfigureras för att blockera kommunikation mellan delsystem. Det kan vara en bra idé att kontrollera dem om det finns problem.

#### Ställ in regler för iptables och SELinux

Om du vill konfigurera regler för att tillåta kommunikation med brandväggen eller SELinux aktiverat kan du läsa följande resurser:

* [iptables how-to](https://help.ubuntu.com/community/IptablesHowTo)
* [Så här redigerar du iptables-regler (fedora-projekt)](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [Introduktion till SELinux (CentOS.org)](https://www.centos.org)
* [SELinux How-To Wiki (CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### Installera Java Software Development Kit

Ange följande kommando för att avgöra om Java redan är installerat:

```bash
java -version
```

Om meddelandet `java: command not found` visas måste du installera Java SDK enligt beskrivningen i nästa avsnitt.

Se något av följande avsnitt:

* [Installera den senaste JDK-versionen på CentOS](#install-the-jdk-on-centos)
* [Installera den senaste JDK-filen på Ubuntu](#install-the-jdk-on-ubuntu)

#### Installera JDK i CentOS

Se den här [självstudiekursen om digitala oceaner](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

Installera JDK och *inte* JRE.

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Java version 8 kanske inte är tillgänglig för alla operativsystem. Du kan till exempel [söka i listan över tillgängliga paket för Ubuntu](https://packages.ubuntu.com/).

#### Installera JDK på Ubuntu

Om du vill installera JDK 1.8 i Ubuntu anger du följande kommandon som en användare med `root`-behörighet:

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

Andra alternativ finns i [Oraclets dokumentation](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### Installera sökmotorn

Följ [Installera Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) eller [Installera och konfigurera OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) för de plattformsspecifika stegen.

Kontrollera att Elasticsearch fungerar genom att ange följande kommando på den server som programmet körs på:

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

Ett meddelande som liknar följande visas:

```
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

Kontrollera att OpenSearch fungerar genom att ange följande kommandon:

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## Uppgraderar Elasticsearch

Mer information om hur du säkerhetskopierar data, identifierar potentiella migreringsproblem och testar uppgraderingar innan du distribuerar till produktionen finns i [Uppgraderar Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Beroende på vilken version av Elasticsearch du använder behöver du kanske inte starta om hela klustret.

Elasticsearch kräver JDK 1.8 eller senare. Se [Installera Java Software Development Kit](#install-the-java-software-development-kit) för att kontrollera vilken version av JDK som är installerad.

## Ytterligare resurser

Se dokumentationen för [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) eller [OpenSearch](https://opensearch.org/docs/latest/).
