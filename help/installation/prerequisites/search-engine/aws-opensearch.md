---
title: AWS OpenSearch
description: Följ de här stegen för att konfigurera webbtjänsten AWS OpenSearch för lokala installationer av Adobe Commerce.
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# AWS OpenSearch

Adobe Commerce 2.4.5 stöder användning av Amazon OpenSearch-tjänstkluster. Tjänsten efterträder Amazon Elasticsearch. I det här avsnittet beskrivs hur du konfigurerar Commerce att använda AWS OpenSearch och hur du migrerar data från en lokal Elasticsearch- eller OpenSearch-instans till ett AWS OpenSearch-kluster.

## Skapa en AWS OpenSearch-tjänstdomän

Du måste först skapa en OpenSearch-instans i AWS.
Läs [Skapa och hantera Amazon OpenSearch-tjänstdomäner](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) för detaljerade anvisningar.

## Hämta data till AWS OpenSearch

När allt är klart för AWS är det dags att fylla i det med data.

För mindre installationer rekommenderar vi att du skapar index direkt på AWS-instansen av följande skäl:

* Det går snabbt att återskapa indexen.
* Versionsinkompatibiliteter kan förekomma mellan den gamla instansen och AWS-instansen, och dessa kan undvikas genom att man bygger direkt på AWS-instansen.

Större installationer kan överväga att migrera sina dataindex från den befintliga instansen till AWS. Även om detta kan minska driftstoppen finns det fortfarande en liten risk för inkompatibilitetsproblem på grund av olika versioner mellan den gamla Elasticsearch-servern och AWS.

Index behöver inte migreras eftersom de enkelt kan återskapas på AWS-instansen.
När du migrerar dataindex måste du dock se till att versionerna av Elasticsearch/OpenSearch är kompatibla.

Mer information finns i Amazon [Migrering till Amazon OpenSearch-tjänsten](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) .

### Konfigurera Commerce för OpenSearch

Steg för konfiguration av OpenSearch beskrivs i avsnittet [Avancerad installation](../../advanced.md).

Testa OpenSearch-slutpunkten direkt om du vill testa att den nya konfigurationen fungerar:

1. Skapa en produkt i Admin (till exempel: sku=&quot;testproduct1&quot;).
1. Indexera om via administratören.
1. Fråga OpenSearch-slutpunkten (finns i AWS UI):

   Om du vill hämta index lägger du till: `/_cat/indices/*?v=true` i URL:en:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Om du vill hämta produkter från indexet lägger du till: `/magento2docker_product_1/_search?q=*` i URL:en:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Ytterligare resurser

Mer information finns i [OpenSearch AWS-dokumentationen](https://docs.aws.amazon.com/opensearch-service/index.html).
