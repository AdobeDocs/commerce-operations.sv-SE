---
title: Fliken  [!DNL Cron]
description: Lär dig mer om fliken  [!DNL Cron] i [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Fliken [!DNL Cron]

Den här fliken är ett försök att snabbt isolera problem och orsaker till [!DNL cron]-problem.

## [!UICONTROL Cron transaction duration in seconds]

![Krontransaktionens varaktighet i sekunder](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

**[!UICONTROL Cron transaction duration in seconds]**-bildrutan visar [!DNL crons] transaktionslängd i sekunder. Detta visar transaktioner som har långa körningsmiljöer. En djupdykning i APM visar mer information om vilken fråga transaktionen/åtgärden kan köra.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL Non Sleeping Threads by Node](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

Bildrutan **[!UICONTROL MySQL Non-Sleeping Threads by Node]** visar MySQL Non-Sleeping-trådar per nod under den valda tidsramen.

## [!UICONTROL SQL Trace count by path]

![Antal SQL-spårningar efter sökväg](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

Bildrutan **[!UICONTROL SQL Trace count by path]** tittar på MySQL-spårningsantalet efter sökväg, vilket kan hjälpa dig att spåra SQL-satser under en vald tidsram.

## [!UICONTROL Cron database call]

![Cron-databasanrop](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

Bildrutan **[!UICONTROL Cron database call]** tittar på antalet [!DNL crons]-anrop till databasen under en vald tidsram.

## [!UICONTROL Cron schedule table locks]

![Kronschematabellen låser](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

Bildrutan **[!UICONTROL Cron schedule table locks]** tittar på schematabellen [!DNL cron] som låses över en vald tidsram.

## [!UICONTROL Cron schedule clean cron fired]

![Kronschematabellen låser](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

Bildrutan **[!UICONTROL Cron schedule clean cron fired]** tittar på antalet [!DNL crons] som har rensats över en vald tidsram. Om inga data visas i den här bildrutan kan det tyda på ett problem med att [!DNL crons] körs korrekt. Om jobbschemat [!DNL cron] inte rensas kommer [!DNL crons] inte att köras optimalt och kan ta längre tid att köra.

## [!UICONTROL Cron schedule clean records details table]

![Rensa poster i schemat för kron](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

Tabellen **[!UICONTROL Cron schedule clean records details table]** innehåller information om jobbet för att rensa poster från tabellen `cron_schedule` över en vald tidsram.

## [!UICONTROL cron_schedule table updates]

![cron_schedule-tabelluppdateringar](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

Bildrutan **[!UICONTROL cron_schedule table updates]** tittar på antalet [!DNL cron] schemalagda tabelluppdateringar under en vald tidsram. Hög aktivitet vid borttagning eller uppdatering av tabellen kan tyda på ett problem med [!DNL crons]. [!DNL crons] uppdaterar även den här tabellen när den körs och är klar, så om det inte finns någon aktivitet i den här tabellen och det finns [!DNL crons] konfigurerad kan det vara problem med [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Tabeller för datastore-åtgärder](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

**[!UICONTROL Datastore Operations Tables]** undersöker databastabellåtgärder, inklusive `SELECT`, `DELETE` och `UPDATE`, över en vald tidsram. I den här ramen visas databastabellerna med den högsta operationsfrekvensen mot dem.
