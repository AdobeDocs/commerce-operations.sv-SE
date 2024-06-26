---
title: Maskinvarubaserad Recommendations
description: Granska en lista över rekommenderad maskinvara för optimala prestanda vid driftsättning av Adobe Commerce.
feature: Best Practices, Install
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Maskinvarurekommendationer

## CPU

[!DNL Commerce] webbnoder hanterar alla begäranden som inte cachelagras eller som inte kan cachelagras via programmet. En processorkärna kan fungera runt två (ibland upp till fyra) [!DNL Commerce] effektivt. Använd följande ekvation för att avgöra hur många webbnoder/kärnor du behöver för att bearbeta alla inkommande begäranden utan att placera dem i kö:

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Om du förväntar dig att belastningen på en butik ska ändras kan du manuellt öka antalet webnoder/kärnor för en aktiv försäljningsperiod. En modell för automatisk skalförändring kan också användas för att automatiskt utöka webblager.

## Minne

### PHP

Magento har olika PHP-minneskrav beroende på hur systemet är driftsatt.  Om du konfigurerar en enda serverbutik rekommenderar vi att du konfigurerar PHP-minne för 2G.  Om du konfigurerar en webbplats med pipeline-distribution rekommenderar vi 2 GB på din build-server och 1 GB på dina webnoder.

Scenarier och förväntade PHP-minneskrav:

* Webbnod endast för butikssidor: 256 MB
* Webbnod som visar administrationssidor med en stor katalog: 1 GB
* [!DNL Commerce] cron indexing a site with a large catalog: >256 MB (Se [avancerad installation](../performance/advanced-setup.md) för att optimera prestanda.)
* [!DNL Commerce] kompilera och driftsätta statiska resurser: 756 MB
* [!DNL Commerce] generering av prestandaverktygsprofiler: >1 GB PHP RAM, >16 MB [!DNL MySQL] Inställningar för TMP_TABLE_SIZE &amp; MAX_HEAP_TABLE_SIZE

### [!DNL MySQL]

The [!DNL Commerce] databasen (och alla andra databaser) är beroende av hur mycket minne som finns tillgängligt för lagring av data och index. Effektiv användning [!DNL MySQL] dataindexering bör mängden tillgängligt minne vara minst hälften så stor som storleken på de data som lagras i databasen.

### Cacher

Om du distribuerar flera [!DNL Commerce] och använder Redis eller [!DNL Varnish] för dina cacheminnen, tänk på följande principer:

* [!DNL Varnish] helsidescacheminnet är effektivt, rekommendera tillräckligt med minne allokerat till [!DNL Varnish] för dina mest populära sidor i minnet
* Sessionscachen är en bra kandidat att konfigurera för en separat instans av Redis.  Minneskonfigurationen för den här cachetypen bör ta hänsyn till webbplatsens strategi för att överge kundvagnen och hur länge en session förväntas finnas kvar i cachen
* Redis bör ha tillräckligt med minne för att rymma alla andra cacheminnen för optimala prestanda.  Blockcachen är nyckelfaktorn när det gäller att fastställa mängden minne som ska konfigureras.  Blockcachen ökar i förhållande till antalet sidor på en plats (antal skus x antal butiksvyer)

## Nätverksbandbredd

Tillräcklig bandbredd är ett av de viktigaste kraven för datautbyte mellan webbnoder, databaser, cachnings-/sessionsservrar och andra tjänster. För [!DNL Commerce] effektivt utnyttjar cachelagring för höga prestanda, kan ditt system aktivt utbyta data med cachningsservrar som Redis. Om Redis finns på en fjärrserver måste du tillhandahålla en tillräcklig nätverkskanal mellan webbnoderna och cachningsservern för att förhindra flaskhalsar vid läs-/skrivåtgärder.
