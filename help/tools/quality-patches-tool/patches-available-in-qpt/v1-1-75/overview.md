---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.75'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.75.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: d952deb1c82ce0d99c3e13909cfc18b7a48034c3
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.75

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.75.

QPT v1.1.75 innehåller följande patchar:
1. **ACSD-68289**: Korrigerar ett fel där fulltextsökning nu returnerar matchande produkter om det lägsta matchningsvillkoret uppfylls för alla sökbara fält tillsammans, i stället för att villkoret måste uppfyllas av ett enskilt fält.
1. **ACSD-68359**: Korrigerar ett fel där det inte längre går att välja en butik vid utcheckning med **[!UICONTROL Pick in Store]** på grund av långa URL:er när många produkter finns i vagnen. Tidigare utlöste detta ett 414-fel som orsakats av alltför långa URL:er som genererats under en butiksförsäljning.
1. **ACSD-68451**: Korrigerar ett fel för flera webbplatser där en företagsadministratör loggar in på en webbplats, skapar ett icke-relaterat företag på en annan webbplats men är felaktigt länkat till det icke-närstående företaget.
1. **ACSD-68490**: **[!UICONTROL Add New Attribute]**-knapp som är synlig för en begränsad administratör när en konfigurerbar produkt skapas.
1. **ACSD-68517**: Korrigerar ett formuläröverföringsfel på sidorna för katalog- och katalogsökning.
1. **ACSD-68573**: Korrigerar problemet där kategoribehörigheter inte tillämpades korrekt på kundens önskelisteobjekt. Efter korrigeringen visas önskelisteobjekten korrekt och sidnumreras både på webben och i GraphQL.
1. **ACSD-68615**: Korrigerar problemet där CLI för kompensation för lagerreservation visade ett undantag om den bearbetade kombinationen saknade order-ID.
1. **ACSD-68793**: Korrigerar ett fel där giltiga produkter nekades felaktigt när de tilldelades till en delad katalog.
1. **ACSD-68925**: Korrigerar ett fel där svar för GraphQL-begäranden nu justeras mot GraphQL över HTTP-specifikationer. En 4XX-svarskod returneras när begäran inte kan tolkas, inte är auktoriserad eller stöter på ett allmänt problem om begäran tolkas.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
