---
title: The [!UICONTROL Elasticsearch] tab
description: Läs mer om [!UICONTROL Elasticsearch] flik för [!DNL Observation for Adobe Commerce].
exl-id: e98d351d-b3b1-47bc-bc0d-f96ba9ec2b80
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# The [!UICONTROL Elasticsearch] tab

## [!UICONTROL Cluster Status Summary]:

![Sammanfattning av klusterstatus](../../assets/tools/cluster-status-summary.jpg)

Under den valda tidsramen visas **[!UICONTROL Cluster Status Summary]** bildrutan visar de färglägen som [!DNL Elasticsearch] klustret har gått igenom. I det här exemplet hade klustret en gång i tiden status grönt under den valda tidsramen och hade en gult status en gång under den valda tidsramen.

## [!UICONTROL Active Primary Shards]

![Aktiva primära kort](../../assets/tools/active-primary-shards.jpg)

The **[!UICONTROL Active Primary Shards]** bildrutan visar de olika numren beroende på antalet aktiva primära kort för det valda kontots [!DNL Elasticsearch] service.

Från [!DNL Elasticsearch]: Den definitiva guiden [2.x]:

&quot;I [Dynamiskt uppdateringsbara index](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html), förklarar vi att ett delområde är ett Lucene-index och att [!DNL Elasticsearch] index är en samling skärmar. Programmet kommunicerar med ett index och [!DNL Elasticsearch] dirigerar dina förfrågningar till lämpliga fragment. Ett delsystem är skalenheten. Det minsta indexvärdet du kan ha är ett med en enda delning. Detta kan vara mer än tillräckligt för dina behov - en enda delmängd kan innehålla mycket data - men det begränsar din möjlighet att skala.&quot;

När ett index skapas, skapas flera skuggor med det indexet. Som standard tilldelas fem primära delningar till varje nytt index, vilket innebär att ett index kan spridas över fem noder (en delning per nod). Det finns också replikskevningar. Dessa är främst till för failover. Replikdelningar kan hantera läsbegäranden.

## [!UICONTROL Active Shards in Cluster]

![Aktiva skuggningar i kluster](../../assets/tools/active-shards-in-cluster.jpg)

The **[!UICONTROL Active Shards in Cluster]** bildrutan visar det totala antalet primära och replikerade delningar i en [!DNL Elasticsearch] kluster.

## [!UICONTROL Index health - this will show the index name and color status]

![Indexhälsa](../../assets/tools/index-health.jpg)

I den här bildrutan visas indexnamnet och antalet indexfärger. Om du bläddrar nedåt i tabellen ser du samma indexnamn med gula och röda färglägen. Siffran som följer efter 27 indexnamn är antalet statusfärger. Om det är noll fanns det inga instanser av indexet med den färgstatusen under de valda tidsbildrutorna.

## [!UICONTROL Elasticsearch Status by node information]

![Status för Elasticsearch](../../assets/tools/elasticsearch-status-by-node.jpg)

The **[!UICONTROL Elasticsearch Status by node information]** bildrutan visar [!DNL Elasticsearch] klusterstatus efter färg och nod. Detta hjälper till att indikera vilken nod i [!DNL Elasticsearch] kluster returnerar vilken status under den valda tidsramen.

## [!UICONTROL Elasticsearch index information]

![Elasticsearch indexinformation](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

The **[!UICONTROL Elasticsearch index information]** tabellen visar indexnamnet, vilken nod det är på, antalet indexerade dokument, indexhälsan och indexstorleken i MB vid en viss tidpunkt.

## [!UICONTROL Elasticsearch process CPU %]

![Processorn Elasticsearch](../../assets/tools/elasticsearch-process-cpu.jpg)

The **[!UICONTROL Elasticsearch process CPU %]** processorn visas i procent av [!DNL Elasticsearch] bearbeta den markerade tidsramen.

## [!UICONTROL Elasticsearch Memory garbage collection]

![Elasticsearch Memory skräp](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] är en Java-process. Om det inte finns tillräckligt med tilldelat minne initieras skräpinsamlingen för att frigöra minne. Om skräpinsamlingen är vanlig är det en indikation på att det kan finnas för många index eller kort för det tilldelade minnet. Det kan finnas en möjlighet att städa upp index och skevningar eller [!DNL Elasticsearch] kan behöva mer minne.

## [!UICONTROL Elasticsearch Index information]

![Elasticsearch-indexinformation](../../assets/tools/elasticsearch-index-information-2.jpg)

När index skapas och uppdateras kan indexets hälsa ändras.

## [!UICONTROL Elasticsearch Index Size]

![Indexstorlek för Elasticsearch](../../assets/tools/elasticsearch-index-size.jpg)

The **[!UICONTROL Elasticsearch Index Size]** bildrutan anger indexnamnet och storleken för den markerade tidsramen. Det kan tyda på problem med hur en webbplats indexeras.

## [!UICONTROL Elasticsearch Errors]

![Elasticsearch-fel](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

The **[!UICONTROL Elasticsearch Errors]** bildrutan visar fel med [!DNL Elasticsearch] som att det börjar ta slut på utrymme, växla från gula till röda, när alla kort inte fungerar, när det finns parameterproblem med sökningar, versionsfel och när alla noder inte är tillgängliga.

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Elasticsearch ej tilldelade kort](../../assets/tools/elasticsearch-unassigned-shards.jpg)

Ej tilldelade kort gör att ett kluster går från grönt till gult.
