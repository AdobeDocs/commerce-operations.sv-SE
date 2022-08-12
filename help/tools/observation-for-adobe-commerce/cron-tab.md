---
title: '"Den [!UICONTROL Cron] tab"'
description: Läs mer om [!UICONTROL Cron] flik för [!DNL Observation for Adobe Commerce].
source-git-commit: 3c1e50b3bff1bd2b2760e2e763173275161b0044
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# The [!UICONTROL Cron] tab

Den här fliken är ett försök att snabbt isolera problem och orsaker till allvarliga problem.

## [!UICONTROL Cron transaction duration in seconds]

![Kravtransaktionens varaktighet i sekunder](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

The **[!UICONTROL Cron transaction duration in seconds]** bildrutan visar varaktigheten för krontransaktioner i sekunder. Detta visar transaktioner som har långa körningsmiljöer. En djupdykning i APM visar mer information om vilken fråga transaktionen/åtgärden kan köra.

## [!UICONTROL MySql Non-Sleeping Threads by Node]

![MySql icke-sovande trådar per nod](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

The **[!UICONTROL MySql Non-Sleeping Threads by Node]** I visas MySql-trådar som inte är vilande efter nod över den valda tidsramen.

## [!UICONTROL SQL Trace count by path]

![Antal SQL-spårningar efter sökväg](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

The **[!UICONTROL SQL Trace count by path]** I frame-vyn kontrolleras antalet MySQL-spårningar per sökväg, vilket kan hjälpa till att spåra SQL-satser under en vald tidsram.

## [!UICONTROL Cron database call]

![Cron-databasanrop](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

The **[!UICONTROL Cron database call]** bildrutan tittar på antalet kroner som anropar databasen under en vald tidsram.

## [!UICONTROL Cron schedule table locks]

![Cron schedule table locks](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

The **[!UICONTROL Cron schedule table locks]** bildrutan tittar på cron schedule table locks över en vald tidsram.

## [!UICONTROL Cron schedule clean cron fired]

![Cron schedule table locks](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

The **[!UICONTROL Cron schedule clean cron fired]** bildrutan tittar på hur många kroner som har rensats under en vald tidsram. Om inga data visas i den här bildrutan kan det tyda på ett problem med att serierna körs korrekt. Om schemat för cron-jobb inte rensas kommer crons inte att köras optimalt och kan ta längre tid att köra.

## [!UICONTROL Cron schedule clean records details table]

![Rensa poster i schemaläggningstabell](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

The **[!UICONTROL Cron schedule clean records details table]** tabellen innehåller information om jobbet för att rensa poster från `cron_schedule` över en markerad tidsram.

## [!UICONTROL cron_schedule table updates]

![cron_schedule table updates](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

The **[!UICONTROL cron_schedule table updates]** bildrutan tittar på antalet schemalagda uppdateringar av cron-tabeller för en vald tidsram. Hög aktivitet vid borttagning eller uppdatering av tabellen kan tyda på problem med crons. Kronerna uppdaterar även den här tabellen när de körs och är klara, så om det inte finns någon aktivitet i det här registret och det finns konfigurerade kroner kan det vara problem med kroner.

## [!UICONTROL Datastore Operations Tables]

![Register för dataarkivåtgärder](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

The **[!UICONTROL Datastore Operations Tables]** läser databastabellåtgärder, inklusive `SELECT`, `DELETE`och `UPDATE` över en vald tidsram. I den här ramen visas databastabellerna med den högsta operationsfrekvensen mot dem.
