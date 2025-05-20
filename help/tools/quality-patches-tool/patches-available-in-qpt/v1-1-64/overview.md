---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.64'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.64.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f6013ec84c1b3c65e2fe2ca062616976326d2fef
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.64

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som är tillgängliga i [!DNL Quality Patches Tool] (QPT) v1.1.64.

QPT v1.1.64 innehåller följande patchar:

1. **ACP2E-3838**: Korrigerar problemet där [!DNL Page Builder] CORS-fel förhindrar att ändringar sparas i administrationspanelen i produktionsläge.
1. **ACP2E-3841**: Korrigerar problemet där kundprisregler för flerleveransprodukter inte gäller korrekt när `subselect` -villkor används och **[!UICONTROL Free Shipping]** är aktiverat.
1. **ACSD-63139**: Korrigerar problemet där produktexport misslyckas när produktattribut innehåller tusentals alternativvärden.
1. **ACSD-65100**: Korrigerar problemet där borttagning av värdena för **[!UICONTROL Maximum Width]** och **[!UICONTROL Maximum Height]** i konfigurationen **[!UICONTROL Media Gallery Image Optimization]** orsakar ett fel under bildoptimeringsprocessen.
1. **ACSD-65127**: Korrigerar problemet där aktivering av JavaScript-miniatyr i produktionsläge medför att [!DNL TinyMCE] 6 genererar fel i webbläsarkonsolen, vilket påverkar funktionalitet och användarupplevelse.
1. **ACSD-65787**: Korrigerar problemet där klassen `SchemaBuilder` kraschar när schema skapas eller uppdateras på grund av en odefinierad arraynyckel *kolumn* vid bearbetning av tabelldata.
1. **ACSD-65223**: Korrigerar problemet där manuellt valda villkor och avtal för [!DNL B2B] inköpsorder resulterar i ett fel.
1. **ACSD-65540**: Korrigerar problemet där ett SQL-syntaxfel inträffar på grund av att funktionen `REGEXP_LIKE` saknas när tabellen `company_structure` uppdateras.
1. **ACSD-65684**: Korrigerar prestandaproblemet där det tog för lång tid att uppgradera `Magento_Company`-modulen efter att ha uppdaterat till [!DNL B2B] 1.5.2 när ett stort antal poster bearbetades (~100 000+) i tabellen `company_structure`.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
