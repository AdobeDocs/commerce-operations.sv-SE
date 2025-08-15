---
title: Avancerade inställningar
description: Granska vedertagna rutiner och rekommendationer för stora företagssystem som utformats för att bearbeta stora datavolymer.
exl-id: eb9ca9fa-b099-4e77-ab33-16cd0f382ffe
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 0%

---

# Avancerad konfiguration

[!DNL Commerce] är en mycket flexibel och skalbar produkt som innehåller lösningar för handlare av alla storlekar. I det här avsnittet beskrivs god praxis och rekommendationer för hur [!DNL Commerce] konfigureras för att fungera med stora mängder data, extrem belastning och andra företagsärenden.

## Kalibrera indexprestanda

Vid hantering av stora mängder data kan omindexering bli ett problem. [!DNL Commerce]-teamet valde de mest inlästa indexen och aktiverade batchindexering, vilket gör att du kan ange en del data som ska bearbetas för varje iteration. På så sätt kan användaren justera batchstorlekar baserat på datatypen och datastorleken i databasen.

Om du vill hantera den här inställningen redigerar du parametern `batchRowsCount` i filen `di.xml` i motsvarande modul. Följande index stöder den här funktionen:

* Kategoriproduktindex (katalogmodul)
* Prisindex (katalogmodul)
* EAV-index (katalogmodul)
* Stock Index (modulen CatalogInventory)

Du kan justera indexeringsprestanda genom att justera variablerna för gruppstorlek för index. Detta styr hur många enheter som bearbetas samtidigt av indexeraren. I vissa situationer har indexeringstiden minskat avsevärt.

Om du till exempel kör en profil som liknar B2B Medium kan du åsidosätta konfigurationsvärdet `batchRowsCount` i `app/code/Magento/catalog/etc/di.xml` och åsidosätta standardvärdet `5000` till `1000`. Detta minskar den fullständiga indexeringstiden från 4 timmar till 2 timmar med en standardkonfiguration för [!DNL MySQL].

>[!NOTE]
>
>Vi har inte aktiverat gruppbearbetning för katalogregelindexeraren. Handlare med ett stort antal katalogregler måste justera sin [!DNL MySQL]-konfiguration för att optimera indexeringstiden. Om du i det här fallet redigerar [!DNL MySQL]-konfigurationsfilen och tilldelar mer minne till konfigurationsvärdena TMP_TABLE_SIZE och MAX_HEAP_TABLE_SIZE (standardvärdet är 16 MB för båda), förbättras prestandan för den här indexeraren, men det leder till att [!DNL MySQL] förbrukar mer RAM-minne.

### Begränsa kundgrupper och delade kataloger per webbplats

Ett stort antal SKU:er, webbplatser, kundgrupper eller delade kataloger påverkar körtiden för indexerarna för produktpris och katalogregel. Detta beror på att som standard tilldelas alla webbplatser till alla kundgrupper (delade kataloger).

Om du vill minska indexeringstiden kan du [utesluta vissa webbplatser från kundgrupper (delade kataloger)](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites).

## Konfigurera Redis

Ibland räcker det inte med en Redis-instans för att hantera inkommande begäranden. Det finns flera lösningar som vi kan rekommendera för att ta itu med den här situationen.

För det första kan du i [!DNL Commerce] konfigurera separat cachelagring för varje cachetyp. På så sätt kan du installera så många separata Redis-instanser som antalet cachetyper som är registrerade i Magento. I realiteten kanske du vill att Redis-instanser ska användas för de mest använda cacheminnen, till exempel konfiguration, layout och block.

En annan lösning kan vara att placera konfigurationscachen i filsystemet och flytta de andra cacherna till Redis-servern. Med den här lösningen behöver du ett separat verktyg för centraliserad ogiltigförklaring av konfigurationscachen på alla dina webbnoder.

Du kan också använda ett Redis-kluster som utför parallella läs-/skrivåtgärder med ett automatiskt ökande antal noder. [!DNL Commerce] tillhandahåller ingen konfiguration för det här ärendet, men det kan startas med mindre anpassningar.

## Konfigurera [!DNL RabbitMQ]

Adobe Commerce stöder meddelandeköer som implementerats via [!DNL RabbitMQ]. [!DNL Commerce] använder den här tjänsten för att köra flera asynkrona åtgärder, inklusive B2B-katalogåtgärder och asynkrona Stock-uppdateringar. Alla gränssnitt för att lägga till fler jobb till jobbservern distribueras med produkten och är tillgängliga för anpassad asynkron logikimplementering i omfattningen av tredjepartstillägg. Precis som med andra integreringar tillhandahåller [!DNL Commerce] en exempelkonfigurationsfil för [!DNL RabbitMQ] som innehåller alla rekommenderade inställningar och är helt klar för produktionsanvändning.

## Dela databasen

>[!WARNING]
>
>Den delade databasfunktionen var [inaktuell](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) i version 2.4.2 av Adobe Commerce. Se [Återgå från en delad databas till en enskild databas](../configuration/storage/revert-split-database.md).

Med Adobe Commerce kan du konfigurera skalbar databaslagring så att den uppfyller behoven i ett växande företag. Du kan skapa tre separata huvuddatabaser som hanterar specifika domäner:

* Huvuddatabas (katalog)
* Utcheckningsdatabas
* Order Management System-databas (OMS)

Om du vill konfigurera ytterligare databaser måste du skapa en tom databas och köra något av följande kommandon:

För Checkout Master DB

```bash
bin/magento setup:db-schema:split-quote
```

För OMS Master DB

```bash
bin/magento setup:db-schema:split-sales
```

Dessa kommandon migrerar specifika domäntabeller från huvuddatabasen till en domändatabas. De ändrar även konfigurationen [!DNL Commerce] så att motsvarande anslutningsmöjligheter och begränsningar kan bearbetas.

Genom att ha separata databaser för utcheckning och Order Management kan du distribuera belastningen mellan databasservrarna. Du kan göra fler utcheckningar och bearbeta fler beställningar per sekund utan att det påverkar tillgängligheten för katalogen och andra åtgärder. Vi rekommenderar att du delar databaser för perioder av blixt eller aktiv försäljning, eller använder dem permanent för naturligt högbelastade projekt. Migrering av befintliga data mellan databaser ska utföras under överinseende av systemadministratören.  Dela inte databaser i produktionsläge.

Förutom huvuddatabaser kan du med [!DNL Commerce] konfigurera ett antal slavdatabaser (en för varje dataresurs som deklarerats i systemet). En slavdatabas fungerar som en fullständig replik av huvuddatabasen eller en av domänens huvuddatabaser. Den utfärdas för läsåtgärder på en specifik resurs.

Du kan lägga till en slavdatabas genom att köra följande kommando:

```bash
bin/magento setup:db-schema:add-slave
```

Det här kommandot utför konfigurationsändringar men konfigurerar inte själva replikeringen. Detta bör göras manuellt.

När huvuddatabasen har delats upp och slave-databaser har ställts in, reglerar [!DNL Commerce] automatiskt anslutningar till en viss databas och fattar beslut baserat på typen av begäran (POST, PUT, GET osv.) och dataresursen. Om [!DNL Commerce] eller dess tillägg utför skrivåtgärder på en GET-begäran växlar systemet automatiskt anslutningen från slav till huvuddatabasen. Det fungerar på samma sätt med masterdatabaser: så snart du arbetar med en utcheckningsrelaterad tabell dirigeras alla frågor om till en viss databas. Under tiden kommer alla katalogrelaterade frågor att gå till huvuddatabasen.

Mer information om konfiguration och fördelarna med flera masterkonfigurationer/slavkonfigurationer finns i
[Lösningen för delad databasprestanda](../configuration/storage/multi-master.md).

## Hantera mediematerial

Magento erbjuder ingen specifik integrering för att leverera mediematerial. Alla vanliga metoder kan användas tillsammans i Magento.

Det enklaste sättet att visa mediainnehåll är att leverera och cachelagra det på en [!DNL Varnish]-server. Det här tillvägagångssättet förutsätter antingen ett delat filsystem för lagring av mediainnehåll eller en dedikerad server som pekar på [!DNL Varnish].

För medelstora och högbelastade miljöer rekommenderar vi att du använder CDN-tjänster som Fastly, Akamai med flera. När [!DNL Commerce] arbetar med de här tjänsterna används den klassiska pull-metoden för innehållsuppdateringar. Du måste konfigurera [!DNL Commerce] URL:er så att de fungerar med motsvarande CDN-tjänst. Genom att flytta medieinnehåll till ett CDN-nätverk minskar du belastningen på dina instanser avsevärt.

## Konfigurera logglagring

Lagringen av loggar och deras påverkan på andra diskåtgärder påverkar tillgängligheten för dina webbnoder, särskilt i högbelastade situationer. Vi rekommenderar att du minimerar loggningen om du inte behöver den. Du kan också konfigurera loggning så att den skrivs på ett separat lagringssystem som har hög åtkomsthastighet. Observera att alla flaskhalsar vid åtkomst av logglagring kan direkt påverka bearbetningen av inkommande begäranden som loggar skriv- eller läsåtgärder som en del av deras flöde.
