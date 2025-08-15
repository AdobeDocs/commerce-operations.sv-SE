---
title: Aktuell sökmotor stöds inte
description: Felsök Adobe Commerce-uppgraderingen efter att ha upptäckt ett fel om en sökmotor som inte stöds.
feature: Upgrade, Search
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Aktuell sökmotor stöds inte

Följande felmeddelande anger att den Adobe Commerce-version du uppgraderar från är konfigurerad att använda en katalogsökmotor som inte stöds i den version du uppgraderar till:

```
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Detta fel innebär att ett av följande villkor gäller för äldre versioner av Adobe Commerce:

- Sökmotorn är inställd på MySQL.
- Sökmotorn är inställd på en version av Elasticsearch som inte längre stöds.

Använd följande kommando för att kontrollera den aktuella sökmotorn:

```bash
bin/magento config:show catalog/search/engine
```

Felet inträffar om det returnerade värdet är `mysql`, `elasticsearch` eller `elasticsearch6`.

>[!WARNING]
>
>Om du har fått det här felet är installationen i ett inkonsekvent tillstånd och du kan inte komma åt administratören. Vi rekommenderar att du återgår till den tidigare versionen medan du åtgärdar det här felet. Om du vill göra det kör du något av följande kommandon:
>
>```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>Där `<version>` är den version av Magento som du körde **före** uppgraderingen. Exempel: `2.3.5`.

Följ riktlinjerna som beskrivs i följande avsnitt för att återställa efter ett inkonsekvent tillstånd.

## Om sökmotorn är `mysql`

Före 2.4 var MySQL standardkatalogsökmotorn, men MySQL stöds inte längre i den här kapaciteten. Nu måste du installera och konfigurera Elasticsearch eller OpenSearch som sökmotor innan du uppgraderar till version 2.4.

Använd följande resurser för att hjälpa dig igenom den här processen:

- [Installera och konfigurera sökmotorn](../../configuration/search/overview-search.md)
- [Sökmotorkonfiguration](../../configuration/search/configure-search-engine.md)

När du har konfigurerat sökmotorn och indexerat om är du redo att uppgradera till 2.4.

## Om sökmotorn är `elasticsearch`

Elasticsearch 6 och tidigare stöds inte längre.

Värdet `elasticsearch` anger att din äldre version av Adobe Commerce är konfigurerad att använda Elasticsearch 2.x. Den här versionen av Elasticsearch stöds inte längre.

Du måste utföra följande åtgärder innan du uppgraderar till 2.4:

1. Uppdatera till en version av Elasticsearch som stöds av Commerce. Se [Uppgradera Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) för fullständiga instruktioner om hur du säkerhetskopierar data, identifierar potentiella migreringsproblem och testar uppgraderingar innan du distribuerar till produktionen. Beroende på vilken version av Elasticsearch du har behöver du kanske starta om hela klustret eller inte.

   >[!NOTE]
   >
   >Elasticsearch kräver JDK 1.8 eller senare. Se [Installera Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) för att kontrollera vilken version av JDK som är installerad.

1. [Konfigurera Elasticsearch](../../configuration/search/configure-search-engine.md) och indexera om.

När du har konfigurerat sökmotorn och indexerat om är du redo att uppgradera till 2.4.
