---
title: The [!UICONTROL Redis] tab
description: Läs mer om [!UICONTROL Redis] flik för [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# The [!DNL Redis] tab

## [!UICONTROL Redis Node summary]

![Redis Node summary](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

The **[!UICONTROL Redis Node summary]** innehåller alla noder i en miljö. Exemplet ovan innehåller noderna för delad mellanlagring. Det finns en primär och två sekundära i produktionen och dessutom en primär och två sekundära i testperioden.

## [!UICONTROL Redis node detail]

![Redis-noddetalj](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

The **[!UICONTROL Redis node detail]** bildruta visar miljön, [!DNL Redis] roll, programversion och nodstorlek.

## [!UICONTROL Redis node roles timeline]

![Redis node roles timeline](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

The **[!UICONTROL Redis node roles timeline]** bildrutan visar förlusten av [!DNL Redis] i synnerhet roller. Om en rad försvinner visar det att den speciella roll som raden representerar har förlorat en eller flera noder.

## [!UICONTROL Connection to Redis]

![Anslutning till Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

The **[!UICONTROL Connection to Redis]** frame visar net.connectedClients-värdet från [!DNL New Relic Redis] exempeldata. Den visar antalet anslutningar med [!DNL New Relic] program (miljö) och nod.

## [!UICONTROL Commands per second by node]

![Kommandon per sekund efter nod](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

The **[!UICONTROL Commands per second by node]** bildrutan visar [!DNL Redis] kommandon per nod per sekund över den valda tidsramen.

## [!UICONTROL Redis % of memory used]

![Redis % av använt minne](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

The **[!UICONTROL Redis % of memory used]** bildrutan visar hur många procent av det maximala minnet som används av [!DNL Redis] servrar.

## [!UICONTROL Redis used memory]

![Redis använt minne](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

The **[!UICONTROL Redis used memory]** bildrutan visar nodanvändningen för minne i GB/MB.

## [!UICONTROL Redis changes since last db save]

![Gör om ändringar sedan den senaste databasen sparades](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] är en minnesplats och sparar informationen i lagringsutrymmet. The **[!UICONTROL Redis changes since last db save]** bildrutan anger antalet minnesändringar som har gjorts sedan den senaste databasen sparades i lagringen. Se [Redis persistence](https://redis.io/docs/manual/persistence/) för mer information om [!DNL Redis's] beständighet.

## [!UICONTROL Redis synchronization from Log]

![Synkronisera igen från logg](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

The **[!UICONTROL Redis synchronization from Log]** bildrutan fokuserar på de fel som uppstår under [!DNL Redis] synkronisering eller fel som inträffar på grund av synkroniseringsproblem. Mer information om [!DNL Redis], se [[!DNL Redis] Dokumentation](https://redis.io/docs/).
