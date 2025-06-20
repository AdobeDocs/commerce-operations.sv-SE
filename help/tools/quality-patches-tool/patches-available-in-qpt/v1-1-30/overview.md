---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.30'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.30.
feature: Tools and External Services
role: Admin
exl-id: 36c6e0cc-fd8c-4583-b147-fe4897b101d8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.30

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.30.

QPT v1.1.30 innehåller följande patchar:

1. **ACSD-50336**: Korrigerar problemet där e-postmeddelanden om produktaviseringar inte skickas när en produkt finns i lager igen eller priset ändras.
1. **ACSD-50367**: Korrigerar problemet där kundadressexport inte fungerar när ett flervalsattribut utan värden skapas.
1. **ACSD-49877**: Korrigerar problemet där automatisk uppspelning av video inte fungerar på mobilen [!DNL Safari] när videon är länkad direkt till en fjärrvideofil och inte till en direktuppspelningstjänst.
1. **ACSD-50165**: Korrigerar felet *Det går inte att ta bort filen. Varning!unlink: Det finns ingen sådan fil eller katalog när JS/CSS-cache tömdes från Admin*.
1. **ACSD-49737**: Korrigerar problemet där en kupong felaktigt markerats som använd efter en misslyckad kortbetalning.
1. **ACSD-50814**: Korrigerar problemet där en administratörsanvändare inte kan skapa en kreditnota.
1. **ACSD-50116**: Korrigerar problemet där en administratörsanvändare inte kan skapa en URL-omskrivning för underkategorierna nivå 3 eller lägre.
1. **ACSD-49513**: Korrigerar problemet där synkronisering av fjärrlagring misslyckas på grund av filer på 0 byte.
1. **ACSD-46683**: Korrigerar problemet där leveranspriset visar *Inte beräknat än*.
1. **ACSD-49129**: Korrigerar problemet där innehållsattributet ([!UICONTROL base64 image code]) inte returneras i `rest/V1/products/sku/media` API-svar för produktmedia.
1. **ACSD-50276**: Korrigerar problemet där kundregistreringsformuläret inte fungerar i butiken om ett kundattribut med flera val skapas.
1. **ACSD-50527**: Korrigerar felet som inträffar när en sida sparas med ett tomt dynamiskt block.
1. **ACSD-49973**: Förbättrar prestanda för hämtning av paketerade produkter via GraphQL.
1. **ACSD-51114**: Korrigerar problemet där en slumpmässig produkt försvinner från stora kataloger när asynkron indexering är aktiverat. Förbättrar prestanda för asynkron omindexering för stora kataloger.
1. **B2B-2598**: Lägger till cachelagring i GraphQL-frågorna `availableStores`, `countries`, `country`, `currency` och `storeConfig`.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
