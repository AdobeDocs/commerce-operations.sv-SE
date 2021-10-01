---
title: Prestandaoptimering - Recommendations
description: Optimera resultatet av implementeringen av Adobe Commerce genom att följa dessa rekommendationer.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 0%

---


# Granskning av prestandaoptimering

Även om prestandaoptimering kan komma från många olika aspekter, finns det vissa allmänna rekommendationer som bör beaktas för de flesta scenarier. Detta inkluderar konfigurationsoptimering för infrastrukturelement, backend-konfiguration för Adobe Commerce och skalbarhetsplanering för arkitektur.

## Infrastruktur

I följande avsnitt beskrivs rekommendationerna för infrastrukturoptimeringar.

### DNS-sökningar

DNS-sökning är processen att hitta den IP-adress som domännamnet tillhör. Webbläsaren måste vänta tills DNS-sökningen har slutförts innan den kan hämta något för varje begäran. Det är viktigt att minska antalet DNS-sökningar för att förbättra den totala sidinläsningstiden.

### CDN (Content Delivery Network)

Använd ett CDN för att optimera resurshämtningsprestanda. Adobe Commerce använder snabbt. Om du har en lokal implementering av Adobe Commerce bör du också överväga att lägga till ett CDN-lager.

### Webbfördröjning

Platsen för datacentret påverkar webblatensen för användare i klientgruppen.

### Nätverksbandbredd

Tillräcklig bandbredd är ett av de viktigaste kraven för datautbyte mellan webbnoder, databaser, cachnings-/sessionsservrar och andra tjänster.

Eftersom Adobe Commerce effektivt utnyttjar cachelagring för höga prestanda kan ditt system aktivt utbyta data med cachningsservrar som Redis. Om Redis finns på en fjärrserver måste du tillhandahålla en tillräcklig nätverkskanal mellan webbnoderna och cachningsservern för att förhindra flaskhalsar vid läs-/skrivåtgärder.

### Operativsystem (OS)

Operativsystemskonfigurationer och optimeringar liknar dem för Adobe Commerce jämfört med andra högbelastade webbapplikationer. När antalet samtidiga anslutningar som hanteras av servern ökar kan antalet tillgängliga socketar allokeras helt.

### CPU för webnoder

En CPU-kärna kan hantera cirka 2-4 Adobe Commerce-begäranden utan cache effektivt. Använd följande ekvation för att avgöra hur många webbnoder/kärnor som behövs för att bearbeta alla inkommande begäranden utan att placera dem i kö:

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### Inställningar för PHP-FPM

Optimering av de här inställningarna beror på prestandatestresultaten för olika projekt.

- **ByteCode** - För att få ut så mycket tid som möjligt från Adobe Commerce med PHP 7 måste du aktivera  `opcache` modulen och konfigurera den på rätt sätt.

- **APCU** - Vi rekommenderar att du aktiverar PHP APCu-tillägget och konfigurerar Composer för optimering för maximala prestanda. Det här tillägget cachelagrar filplatser för öppnade filer, vilket ökar prestanda för serveranrop från Adobe Commerce, inklusive sidor, Ajax-anrop och slutpunkter.

- **Realpath_cacheConfiguration** - Optimering  `realpath_cache` gör att PHP-processer kan cachelagra sökvägar till filer i stället för att leta upp dem varje gång en sida läses in.

### Webbserver

Endast en liten omkonfiguration behövs för att använda nginx som webbserver. nginx-webbservern ger bättre prestanda och är enkel att konfigurera med exempelkonfigurationsfilen från Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)).

- Konfigurera PHP-FPM med TCP korrekt

- Aktivera HTTP/2 och Gzip

- Optimera anslutningar för arbetare

### Databas

Det här dokumentet innehåller inga detaljerade MySQL-justeringsanvisningar eftersom varje butik och miljö är olika, men vi kan göra några allmänna rekommendationer.

Adobe Commerce-databasen (och alla andra databaser) är känslig för mängden tillgängligt minne för lagring av data och index. För att utnyttja MySQL-dataindexeringen effektivt bör mängden tillgängligt minne vara minst hälften så stor som storleken på de data som lagras i databasen.

Optimera `innodb_buffer_pool_instances`-inställningen för att undvika problem med flera trådar som försöker få åtkomst till samma instans. Värdet för parametern `max_connections` ska korrelera med det totala antalet PHP-trådar som konfigurerats i programservern. Använd följande formel för att beräkna det bästa värdet för `innodb-thread-concurrency`:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Sessionscachning

Sessionscachning är en bra kandidat att konfigurera för en separat instans av Redis. Minneskonfigurationen för den här cachetypen bör ta hänsyn till webbplatsens strategi för att överge kundvagnen och hur länge en session förväntas finnas kvar i cachen.

Redis bör ha tillräckligt med minne för att rymma alla andra cacheminnen för optimala prestanda. Blockcachen är nyckelfaktorn när det gäller att fastställa mängden minne som ska konfigureras. Blockcachen ökar i förhållande till antalet sidor på en plats (antal SKU × antalet butiksvyer).

### Cachelagring av sidor

Vi rekommenderar att du använder lack för helsidescache i din Adobe Commerce Store. Modulen `PageCache` finns fortfarande i kodbasen, men den bör bara användas i utvecklingssyfte.

Installera lack på en separat server framför webbskiktet. Den ska acceptera alla inkommande begäranden och tillhandahålla cachelagrade sidkopior. För att Varnish ska kunna arbeta effektivt med skyddade sidor kan en SSL-termineringsproxy placeras framför Varnish. Nginx kan användas för detta ändamål.

Även om det är effektivt att ogiltigförklara helsidescacheminnet för lack rekommenderar vi att du tilldelar tillräckligt med minne till Varnish för de mest populära sidorna i minnet.

### Meddelandeköer

MQF (Message Queue Framework) är ett system som gör att en modul kan publicera meddelanden till köer. Det definierar också de konsumenter som tar emot meddelandena asynkront. Adobe Commerce stöder RabbitMQ som meddelandeförmedlare, som tillhandahåller en skalbar plattform för att skicka och ta emot meddelanden.

### Prestandatestning och övervakning

Prestandatestning före varje produktionsrelease rekommenderas alltid för att få en uppskattning av kapaciteten hos er e-handelsplattform. Övervaka efter lanseringen och få en skalbarhet och en säkerhetskopieringsplan för hantering av trafiktoppar.

>[!NOTE]
>
> Adobe Commerce on cloud Infrastructure tillämpar redan alla de ovanstående optimeringarna av infrastruktur och arkitektur, förutom DNS-sökningen eftersom den ligger utanför räckvidden.

### Sök

Elasticsearch krävs från och med Adobe Commerce version 2.4, men det är också en god vana att aktivera det för versioner före 2.4.

## Operativmodeller

Förutom de tidigare nämnda rekommendationerna om optimering av den gemensamma infrastrukturen finns det också metoder för att förbättra prestandan för specifika affärslägen och skalor. Det här dokumentet innehåller inga detaljerade justeringsinstruktioner för alla eftersom varje scenario är olika, men vi kan tillhandahålla några alternativ på hög nivå för din referens.

### Headless-arkitektur

Vi har ett separat avsnitt som beskriver vad [headless](../../architecture/headless/adobe-commerce.md) är och olika alternativ. Sammanfattningsvis separerar den butikslagret från själva plattformen. Det är fortfarande samma serverdel, men Adobe Commerce hanterar inte längre begäranden direkt och stöder i stället bara anpassade butiker via GraphQL API.

### Behåll Adobe Commerce uppdaterad

Adobe Commerce har alltid bättre prestanda när den senaste versionen körs. Även om det inte är möjligt att hålla Adobe Commerce uppdaterad efter att varje ny version släppts rekommenderas det fortfarande att uppgradera när Adobe Commerce inför betydande prestandaoptimeringar.

År 2020 lanserade Adobe t.ex. en optimering av Redis-lagret, som åtgärdade en hel del ineffektivitet, anslutningsproblem och onödig dataöverföring mellan Redis och Adobe Commerce. Den övergripande prestandan mellan 2.3 och 2.4 är natt och dag och vi har sett avsevärda förbättringar vad gäller kundvagn, utcheckning, samtidiga användare, bara på grund av Redis-optimeringen.

### Optimera datamodell

Många problem har sitt ursprung i data, bland annat dåliga datamodeller, data som inte är korrekt strukturerade och data som saknar ett index.

Det ser bra ut om du testar några anslutningar, men ser bra ut i produktionen när den verkliga trafiken träffar och det är här som långsamhet kommer in. Det är mycket viktigt att systemintegratörer vet hur man utformar en datamodell (särskilt för produktattribut), undviker att lägga till onödiga attribut och behåller obligatoriska attribut som påverkar affärslogiken (t.ex. prissättning, tillgänglighet och sökning).

För de attribut som inte påverkar affärslogiken men som måste finnas på butiken kan du kombinera dem till ett fåtal attribut (till exempel JSON-format).

För att optimera plattformsprestanda behöver man inte lägga till det attributet i Adobe Commerce om det inte krävs någon affärslogik i butiken från data eller attribut som hämtats från en PIM eller en ERP.

### Design för skalbarhet

Detta är viktigt för företag som kör kampanjer och ofta ställs inför höga tidpunkter. För att arkitektur och applikationsdesign ska vara enkel att skala kan detta öka resurserna under högtider och minska dem efter det.