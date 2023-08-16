---
title: '[!DNL Exceptions]'
description: Läs mer om [!UICONTROL Exceptions] i [!DNL Site-Wide Analysis Tool], när det ska användas, dess fördelar och bästa praxis.
exl-id: bd793536-b95c-47db-9372-33c00be8e144
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# [!DNL Exceptions]

The [!DNL Site-Wide Analysis Tool’s] [!UICONTROL Exceptions] sidan visar fel/undantag i webbplatsloggfilen. Undantag är onormala tillstånd som kan ha eller inte har en känd lösning.

Den information som visas på den här sidan innehåller [!UICONTROL Last Detected] (datum/tid i UTC), [!UICONTROL Exception Detail]och [!UICONTROL Count] (antal förekomster) att undantaget inträffade det datumet.

## När ska du använda

Använd [!UICONTROL Exceptions] om du vill se loggfilsfel/undantagsloggar för Adobe Commerce-projekt. De är användbara för felsökning av problem som rör Adobe Commerce bygg- och driftsättningshooks, molntjänster och Adobe Commerce-programmet.

## Fördelar

* Lär dig mer om de undantag som kan förekomma och hur ofta de förekommer på din webbplats.

* Spåra problem med undantagsloggen och, om det behövs, implementera lämpliga korrigerande åtgärder för att förbättra webbplatsens prestanda.

## God praxis

Övervaka [!DNL Site-Wide Analysis Tool’s] [!UICONTROL Exceptions] för att se vilka undantag som inträffar. Mer information finns i [Visa och hantera loggar](https://devdocs.magento.com/cloud/project/log-locations.html) i vår dokumentation för utvecklare.
