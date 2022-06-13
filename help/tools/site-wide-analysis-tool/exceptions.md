---
title: '"[!DNL Exceptions]"'
description: Läs mer om [!UICONTROL Exceptions] i [!DNL Site-Wide Analysis Tool], när det ska användas, dess fördelar och bästa praxis.
source-git-commit: 6cbb4b4fef5e1ccc06803b5a3af5dd9f4d0e7df8
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# [!DNL Exceptions]

The [!DNL Site-Wide Analysis Tool’s] [!UICONTROL Exceptions] sidan visar fel/undantag i webbplatsloggfilen. Undantag är onormala tillstånd som kan ha eller inte har en känd lösning.

Den information som visas på den här sidan innehåller [!UICONTROL Last Detected] (datum/tid i UTC), [!UICONTROL Exception Detail]och [!UICONTROL Count] (antal förekomster) att undantaget inträffade det datumet.

## När ska användas

Använd [!UICONTROL Exceptions] om du vill se loggfilsfel/undantagsloggar för Adobe Commerce-projekt. De är användbara för felsökning av problem som rör Adobe Commerce bygg- och driftsättningshooks, molntjänster och Adobe Commerce-programmet.

## Fördelar

* Lär dig mer om de undantag som kan förekomma och hur ofta de förekommer på din webbplats.

* Spåra problem med undantagsloggen och, om det behövs, implementera lämpliga korrigerande åtgärder för att förbättra webbplatsens prestanda.

## God praxis

Övervaka [!DNL Site-Wide Analysis Tool’s] [!UICONTROL Exceptions] för att se vilka undantag som inträffar. Mer information finns i [Visa och hantera loggar](https://devdocs.magento.com/cloud/project/log-locations.html) i vår dokumentation för utvecklare.
