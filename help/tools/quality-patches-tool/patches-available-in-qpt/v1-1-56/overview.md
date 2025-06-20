---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.56'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.56.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6433df73-b6df-4c88-93a4-12ac1e5080ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.56

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som är tillgängliga i [!DNL Quality Patches Tool] (QPT) v1.1.56.

QPT v1.1.56 innehåller följande patchar:

1. **ACSD-63244**: Korrigerar problem där ett JavaScript-fel förhindrar att [!DNL Google Maps] återges korrekt och där det finns många *ej infångade TypeError: detta._each är inte en funktion*-fel i konsolen på panelen [!UICONTROL Admin].
1. **ACSD-63242**: Korrigerar problemet med långsam import när katalogprodukter med fler än 10 000 poster läggs till.
1. **ACSD-63062**: Korrigerar problemet där felaktiga kundvagnsrabattberäkningar inträffar när flera överlappande regler tillämpas.
1. **ACSD-62979**: Korrigerar problemet där fel [!UICONTROL Store ID] i GraphQL-huvudet orsakar ett allvarligt minnesfel.
1. **ACSD-62971**: Korrigerar problemet där import av Stock-källor med icke-numeriska värden i kolumnen *[!UICONTROL Quantity]* resulterar i att *quantity* anges till *0*.
1. **ACSD-62872**: Korrigerar problemet med unik attributvalidering där schemauppdateringar valideras felaktigt.
1. **ACSD-62755**: Korrigerar problemet där [!DNL TinyMCE] 7 kräver att teckensnittsstorlek och teckensnitt läggs till specifikt i initieringsinställningarna för redigeraren.
1. **ACSD-62670**: Korrigerar problemet där [!UICONTROL Products Ordered] -rapportexporten till CSV och XML returnerar ett fel.
1. **ACSD-62577**: Korrigerar problemet med långsam prestanda för sökfrågor i butiker genom att optimera både fråga- och tabellindex.
1. **ACSD-62475**: Korrigerar problemet där [!UICONTROL Gift Card]-produkterna sammanfogas felaktigt i kundvagnen.
1. **ACSD-62428**: Korrigerar problemet där `is_out_of_stock` är inställt på ett felaktigt värde i katalogsökindexet när [!DNL SKU] inte är inställt som ett sökbart attribut.
1. **ACSD-62355**: Förbättrar inläsningstiden för den konfigurerbara produktredigeringssidan när den konfigurerbara produkten är baserad på många attribut med många värden.
1. **ACSD-61805**: Korrigerar problemet där produkter ligger utanför lagret efter att lagerstatus har uppdaterats via [!DNL REST API].
1. **ACSD-60811**: Korrigerar problemet där det bara går att uppdatera orderstatus med ett anpassat värde eller en kommentar om den aktuella statusen är antingen *[!UICONTROL Processing]* eller *[!UICONTROL Fraud]*.
1. **ACSD-62952**: Korrigerar problemet där datumet [!UICONTROL Gift Registry] visas felaktigt på butiken.
1. **ACSD-55339**: Korrigerar problemet där en produkt [!DNL SKU] som börjar med *0* (noll) tar bort *0*, vilket förhindrar att offerten uppdateras.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
