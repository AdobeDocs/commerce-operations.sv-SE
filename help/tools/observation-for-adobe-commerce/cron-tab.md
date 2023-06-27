---
title: The [!DNL Cron] tab
description: Läs mer om [!DNL Cron] flik för [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# The [!DNL Cron] tab

Fliken är ett försök att snabbt isolera problem och orsaker till [!DNL cron] problem.

## [!UICONTROL Cron transaction duration in seconds]

![Kravtransaktionens varaktighet i sekunder](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

The **[!UICONTROL Cron transaction duration in seconds]** bildrutevisning [!DNL crons] transaktionens varaktighet i sekunder. Detta visar transaktioner som har långa körningsmiljöer. En djupdykning i APM visar mer information om vilken fråga transaktionen/åtgärden kan köra.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL icke-vilande trådar efter nod](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

The **[!UICONTROL MySQL Non-Sleeping Threads by Node]** I visas MySQL-trådar som inte är vilande efter nod över den valda tidsramen.

## [!UICONTROL SQL Trace count by path]

![Antal SQL-spårningar efter sökväg](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

The **[!UICONTROL SQL Trace count by path]** Vid sökning efter MySQL-spårningsantal efter sökväg, vilket kan hjälpa till att spåra SQL-satser under en vald tidsram.

## [!UICONTROL Cron database call]

![Cron-databasanrop](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

The **[!UICONTROL Cron database call]** bildrutan tittar på antalet [!DNL crons] anrop till databasen över en vald tidsram.

## [!UICONTROL Cron schedule table locks]

![Cron schedule table locks](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

The **[!UICONTROL Cron schedule table locks]** bildrutan ser ut på [!DNL cron] schematabellen låses över en vald tidsram.

## [!UICONTROL Cron schedule clean cron fired]

![Cron schedule table locks](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

The **[!UICONTROL Cron schedule clean cron fired]** bildrutan tittar på antalet [!DNL crons] rensad över en vald tidsram. Om inga data visas i den här bildrutan kan det tyda på ett problem med [!DNL crons] fungerar som det ska. Om [!DNL cron] Jobbschemat har inte rensats, [!DNL crons] kommer inte att fungera optimalt och kan ta längre tid att köra.

## [!UICONTROL Cron schedule clean records details table]

![Rensa poster i schemaläggningstabell](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

The **[!UICONTROL Cron schedule clean records details table]** tabellen innehåller information om jobbet för att rensa poster från `cron_schedule` över en markerad tidsram.

## [!UICONTROL cron_schedule table updates]

![cron_schedule table updates](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

The **[!UICONTROL cron_schedule table updates]** bildrutan tittar på antalet [!DNL cron] schemalagda tabelluppdateringar för en vald tidsram. Hög aktivitet vid borttagning eller uppdatering av tabellen kan tyda på ett problem med [!DNL crons]. Dessutom [!DNL crons] uppdatera den här tabellen när den körs och är klar, så om det inte finns någon aktivitet i den här tabellen och det finns [!DNL crons] konfigurerad, kan det vara problem med [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Register för dataarkivåtgärder](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

The **[!UICONTROL Datastore Operations Tables]** läser databastabellåtgärder, inklusive `SELECT`, `DELETE`och `UPDATE` över en vald tidsram. I den här ramen visas databastabellerna med den högsta operationsfrekvensen mot dem.
