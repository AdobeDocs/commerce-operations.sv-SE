---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.34'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.34.
feature: Tools and External Services
role: Admin
exl-id: d6cc3161-802c-4a1a-95b1-1eb85715643b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.34

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som är tillgängliga i [!DNL Quality Patches Tool] (QPT) v1.1.34.

QPT v1.1.34 innehåller följande patchar:

1. **ACSD-52277**: Korrigerar problemet där en administratörsanvändare inte omdirigeras korrekt efter att butiksvyn har valts när en ny ordning skapas i administratören.
1. **ACSD-50813**: Korrigerar problemet där en administratör inte kan lägga till paketerade produkter som innehåller ett snedstreck i SKU:n med funktionen [!UICONTROL Add Products by SKU] i administratörsordningen.
1. **ACSD-51630**: Korrigerar problemet där ett stort antal systemmeddelanden gör att det går långsammare att hämta administratörssidor.
1. **ACSD-51853**: Korrigerar problemet där kopierade textformat inte används när [!DNL Page Builder] används.
1. **ACSD-52160**: Korrigerar problemet där ett produktvalideringsresultat mot kundvagnsprisregeln inte utvärderades korrekt, baserat på regelvillkoret *Om ett objekt hittas/inte hittas i vagnen med alla/något av dessa villkor är sant*.
1. **ACSD-51636**: Korrigerar problemet där en administratör inte kan lägga till nya användare från kundkontoavsnittet trots att de har alla nödvändiga roller och behörigheter.
1. **ACSD-51739**: Korrigerar problemet där ett fel returneras när `structure_id` begärs i en `CompanyTeam` GraphQL-begäran.
1. **ACSD-51857**: Korrigerar problemet där långsamma prestanda för `aggregate_sales_report_bestsellers_data` cron-rapporten påverkar stora `sales_order`- och `sales_order_item` databastabeller.
1. **ACSD-48448**: Korrigerar problemet där det uppstod ett konkurrensproblem under orderannulleringar, vilket orsakar dubblerad post i tabellen *Inventering_reservation*.
1. **ACSD-52689**: Korrigerar problemet där bilder inte kan överföras till [!DNL Amazon S3]-lagring med REST API.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
