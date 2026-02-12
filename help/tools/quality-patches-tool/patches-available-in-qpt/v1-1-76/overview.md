---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.76'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.76.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: aeda6ddd9bac7e5f81329d9bd05ab8957ef2fb76
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.76

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.76.

QPT v1.1.76 innehåller följande patchar:
1. **ACSD-67091**: Korrigerar det maximala skrivstorleksfelet för att säkerställa att katalogregelns produktindex rensas genom att implementera två raderingsstrategier som baseras på datavolym.
1. **ACSD-67370**: Korrigerar flera problem där felaktiga priser visades för paketprodukter på PDP/PLP och kundvagnssidan för butiker med flera valutor.
1. **ACSD-68410**: Korrigerar ett problem där en order för en överlåtbar offert felaktigt lägger till eller sammanfogar ytterligare kundvagnsrader i offerten. Produkterna läggs nu korrekt till i kundvagnen efter att du lämnat det sista steget i utcheckningen av en överlåtbar offert.
1. **ACSD-69086**: Korrigerar problemet där cron-jobbet inte kan rensa ändringstabeller, vilket orsakar [!DNL Galera Cluster] krascher när stora mängder data hanteras.
1. **ACSD-69115**: Korrigerar ett fel där kundvagnsfel inte visades för administratörsanvändaren vid hantering av kundvagnen för en kund som tilldelats en icke-standardwebbplats.
1. **ACSD-69129**: Korrigerar ett fel där borttagning av standardbaswebbplatsen och användning av den sekundära webbplatsen som standard resulterar i ett fel när nivåpriset för den sekundära webbplatsen skulle uppdateras via [!DNL REST] API.
1. **ACSD-69203**: Korrigerar ett fel där widgeten **[!UICONTROL Products List]** returnerar felaktiga resultat när flera kategorier listades i kategorivillkoret.
1. **ACSD-69261**: Korrigerar ett problem där en kundprisregelkupong som konfigurerats för engångsbruk per kund återanvändes flera gånger på grund av felaktig hantering av attributet `times_used` i scenarier med partiell faktura och återstående kvantitetsåterkallning.
1. **ACSD-69308**: Korrigerar ett fel där katalogprisreglerna inte tillämpades när `special_price` bara angavs på webbplatsnivå (inte på **[!UICONTROL All Store Views]**). Efter korrigeringen tillämpas katalogprisreglerna korrekt genom att kontrollera webbplatsens standardbutik först.
1. **ACSD-69319**: Korrigerar ett fel där paketpriser inte indexerades korrekt när underordnade produkter lagrades under anpassade källor.
1. **ACSD-69325**: Korrigerar ett fel där ändring av SKU-skiftläget gör att produkten inte finns i lager på butiken.
1. **ACSD-69331**: Korrigerar ett fel där innehållsskapare i mediegalleriet inte kunde skapa mappar med bara behörigheten `create_folder`. Efter korrigeringen kan de skapa mappar som förväntat.
1. **ACSD-69333**: Korrigerar ett fel där SKU-ändringar var tillåtna för produkter med en aktiv schemalagd uppdatering. Efter korrigeringen tillåts inte SKU-ändringar under aktiva uppdateringar. Sparningar misslyckas med ett tydligt fel och fältet admin-SKU är inaktiverat. Detta förhindrar MSI.
1. **ACSD-69541**: Korrigerar ett fel där det inte gick att redigera produktkvantiteten i varukorgen via GraphQL om du reducerade en produkts kvantitet i administratören till mindre än vad som redan finns i en varukorg.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
