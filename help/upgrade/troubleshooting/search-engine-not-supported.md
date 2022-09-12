---
title: Aktuell sökmotor stöds inte
description: Felsök uppgraderingen av Adobe Commerce eller Magento Open Source efter att ha upptäckt ett fel om en sökmotor som inte stöds.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---


# Aktuell sökmotor stöds inte

Följande felmeddelande anger att den version av Adobe Commerce eller Magento Open Source som du uppgraderar från är konfigurerad att använda en katalogsökmotor som inte stöds i den version som du uppgraderar till:

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Detta fel innebär att ett av följande villkor gäller för äldre versioner av Adobe Commerce eller Magento Open Source:

- Sökmotorn är inställd på MySQL.
- Sökmotorn är inställd på en version av Elasticsearch som inte längre stöds.

Använd följande kommando för att kontrollera den aktuella sökmotorn:

```bash
bin/magento config:show catalog/search/engine
```

Felet inträffar om det returnerade värdet är `mysql` eller `elasticsearch`.

>[!WARNING]
>
>Om du har fått det här felet är installationen i ett inkonsekvent tillstånd och du kan inte komma åt administratören. Vi rekommenderar att du återgår till den tidigare versionen medan du åtgärdar det här felet. Om du vill göra det kör du något av följande kommandon:
>
>
```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>
```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>Plats `<version>` är den version av Magento som du körde **före** uppgraderingen. Exempel, `2.3.5`.

Följ riktlinjerna som beskrivs i följande avsnitt för att återställa efter ett inkonsekvent tillstånd.

## Om sökmotorn är `mysql`

Före 2.4 var MySQL standardkatalogsökmotorn, men MySQL stöds inte längre i den här kapaciteten. Nu måste du installera och konfigurera Elasticsearch eller OpenSearch som sökmotor innan du uppgraderar till 2.4.

Använd följande resurser för att hjälpa dig igenom den här processen:

- [Installera och konfigurera Elasticsearch](../../configuration/search/overview-search.md)
- [Installerar Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Konfigurera Elasticsearch för att arbeta med [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) eller [Apache](../../installation/prerequisites/search-engine/configure-apache.md)
- [Konfigurera Elasticsearch](../../configuration/search/configure-search-engine.md)

När du har konfigurerat sökmotorn och indexerat om är du redo att uppgradera till 2.4.

## Om sökmotorn är `elasticsearch`

Värdet för `elasticsearch` visar att din äldre version av Adobe Commerce eller Magento Open Source är konfigurerad att använda Elasticsearch 2.x. Den här versionen av Elasticsearch stöds inte längre.

Du måste utföra följande åtgärder innan du uppgraderar till 2.4:

1. Uppdatera till en version av Elasticsearch som stöds av Commerce. Se [Uppgraderar Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) om du vill ha fullständiga anvisningar om hur du säkerhetskopierar data, upptäcker potentiella migreringsproblem och testar uppgraderingar innan du distribuerar till produktionen. Beroende på vilken version av Elasticsearch du använder behöver du kanske inte starta om hela klustret.

   >[!NOTE]
   >
   >Elasticsearch kräver JDK 1.8 eller senare. Se [Installera Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) för att kontrollera vilken version av JDK som är installerad.

1. [Konfigurera Elasticsearch](../../configuration/search/configure-search-engine.md) och indexera om.

När du har konfigurerat sökmotorn och indexerat om är du redo att uppgradera till 2.4.
