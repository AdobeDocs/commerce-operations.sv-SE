---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.37'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.37.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.37

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.37.

QPT v1.1.37 innehåller följande patchar:

1. **ACSD-52613**: Korrigerar problemet där cacheminnen och index uppdateras även när inga uppdateringar görs av `Inventory_source` objekt via vila-API.
1. **ACSD-51884**: Korrigerar problemet där produktbildens cachesökväg blir felaktig efter att kommandot för storleksändring körts.
1. **ACSD-53628**: Korrigerar problemet där CSV-försäljningsorderrapporten innehåller felaktiga specialtecken.
1. **ACSD-49843**: Korrigerar problemet där länken vid produktnedladdning inte är tillgänglig efter att den beställda artikeln har fakturerats automatiskt med onlinebetalningsmetoden med inställningen *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* aktiverad.
1. **ACSD-53148**: Korrigerar problemet där två parallella begäranden i GraphQL om att lägga till samma konfigurerbara produkt i vagnen resulterade i två separata artiklar i vagnen med samma produkt-SKU.
1. **ACSD-47054**: Korrigerar problemet där omindexering av förhandsgranskning kör omindexering för alla butiker, vilket orsakar långsamhet.
1. **ACSD-52606**: Korrigerar problemet där felmeddelandet *Din beställning inte är klar för hämtning* visas när användaren klickar på **[!UICONTROL Notify Order is Ready for Pickup]**.
1. **ACSD-51574**: Korrigerar ett fel där bilden inte uppdateras på kantlinjen efter att den har ersatts med en annan bild med samma namn.
1. **ACSD-53728**: Korrigerar problemet där produktindexeraren tar längre tid att slutföra.
1. **ACSD-53979**: Korrigerar JS-problemet som inträffar på hemsidan om välkomstmeddelandet innehåller ett enkelt citattecken.
1. **ACSD-52143**: Korrigerar problemet där anpassade alternativ tas bort efter produktimporten.
1. **ACSD-53750**: Korrigerar felet *Avbruten pipe eller stängd anslutning* under omindexering av flertrådiga `catalog_product_price`.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
