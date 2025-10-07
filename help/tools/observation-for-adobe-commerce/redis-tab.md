---
title: Fliken [!UICONTROL Redis]
description: Läs mer om fliken [!UICONTROL Redis] i  [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Fliken [!DNL Redis]

## [!UICONTROL Redis Node summary]

![Redis Node summary](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

**[!UICONTROL Redis Node summary]** innehåller alla noder i en miljö. Exemplet ovan innehåller noderna för delad mellanlagring. Det finns en primär och två sekundära i produktionen och dessutom en primär och två sekundära i mellanstadiet.

## [!UICONTROL Redis node detail]

![Redis server performance metrics and node configuration details](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

Bildrutan **[!UICONTROL Redis node detail]** anger miljö, roll [!DNL Redis], programversion och nodstorlek.

## [!UICONTROL Redis node roles timeline]

![Redis node roles timeline](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

Bildrutan **[!UICONTROL Redis node roles timeline]** indikerar förlust av tjänsten [!DNL Redis] i vissa roller. Om en rad försvinner visar det att den speciella roll som raden representerar har förlorat en eller flera noder.

## [!UICONTROL Connection to Redis]

![Anslutning till Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

Ramen **[!UICONTROL Connection to Redis]** visar net.connectedClients-värdet från exempeldata för [!DNL New Relic Redis]. Den visar antalet anslutningar per [!DNL New Relic]-program (miljö) och nod.

## [!UICONTROL Commands per second by node]

![Kommandon per sekund och nod](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

I bildrutan **[!UICONTROL Commands per second by node]** visas kommandona [!DNL Redis] per nod per sekund under den valda tidsramen.

## [!UICONTROL Redis % of memory used]

![Redis % av använt minne](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

Bildrutan **[!UICONTROL Redis % of memory used]** visar procentandelen av maximalt minne som används av servrarna [!DNL Redis].

## [!UICONTROL Redis used memory]

![Återanvänt minne](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

Bildrutan **[!UICONTROL Redis used memory]** visar nodanvändningen för minne i GB/MB.

## [!UICONTROL Redis changes since last db save]

![Gör om ändringar sedan den senaste databasen sparades](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] är en minnesplats och sparar informationen i lagringsutrymmet. Bildrutan **[!UICONTROL Redis changes since last db save]** anger antalet minnesändringar som har gjorts sedan den senaste databasen sparades i lagringen. Mer information om [-beständighet finns i ](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/)Redis-beständighet[!DNL Redis's].

## [!UICONTROL Redis synchronization from Log]

![Synkronisera igen från logg](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

Bildrutan **[!UICONTROL Redis synchronization from Log]** fokuserar på de fel som uppstod under synkroniseringen av [!DNL Redis] eller på fel som inträffar på grund av synkroniseringsproblem. Mer information om [!DNL Redis] finns i [[!DNL Redis] Dokumentation](https://redis.io/docs/).
