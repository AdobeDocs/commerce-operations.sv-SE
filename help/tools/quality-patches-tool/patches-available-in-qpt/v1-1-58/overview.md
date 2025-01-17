---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.58'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.58.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f8473bbdedef26b291547d828e47a9ba08a5d142
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.58

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som är tillgängliga i [!DNL Quality Patches Tool] (QPT) v1.1.58.

QPT v1.1.58 innehåller följande patchar:

1. **ACSD-48570**: Korrigerar problemet där sidan för återställning av lösenord inte kunde nås genom att klicka på länken [!UICONTROL Admin] Återställ lösenord när **Lägg till lagringskod i URL:er** var *aktiverad*, vilket tidigare ledde till att inloggningssidan eller en 404-sida visades.
1. **ACSD-62118**: Korrigerar problemet där tabellen `sales_order_tax_item` inte uppdateras fullständigt när [!DNL B2B] order placeras med metoden Inköpsorder.
1. **ACSD-63067**: Korrigerar problemet där alla produktkvantiteter markeras felaktigt och meddelandet *[!DNL Please specify the quantity of product(s).]* visas för alla produkter i en grupperad produkt när endast en kvantitet är felaktig.
1. **ACSD-63090**: Korrigerar problemet där kundvagnsartiklar tas bort när en produkt tas bort efter att ha lagts till i vagnen.
1. **ACSD-63182**: Korrigerar problemet där ett fel inträffar när en duplicerad paketprodukt sparas med **[!DNL MSI]** *enabled*.
1. **ACSD-63283**: Korrigerar problemet där beställningsartiklar från presentregistret orsakar ett undantag och där presentregisteruppdateringar innehåller objekt som inte tillhör registret.
1. **ACSD-63299**: Korrigerar problemet där specialpriset för en konfigurerbar produkt inte visas i butiken.
1. **ACSD-63325**: Korrigerar problemet där ett `Syntax Error: Unexpected <EOF>`-fel inträffar när en tom [!DNL GraphQL]-begäran skickas.
1. **ACSD-63329**: Korrigerar problemet där standardvärden för attribut med indatatyperna **[!UICONTROL Date]** eller **[!UICONTROL Date and Time]** inte anges när produkter skapas via [!DNL REST API].
1. **ACSD-63572**: Korrigerar problemet där temporära tabeller för `CatalogRule` indexeraren inte rensas om indexeringsprocessen avslutas.
1. **ACSD-63578**: Korrigerar felet där **[!UICONTROL Delete]**-knappen i **[!UICONTROL Add to Order by SKU]** i [!UICONTROL Admin] inte tar bort [!DNL SKU] när du klickar på knappen .

Använd menyn till vänster för att navigera till en viss korrigeringssida.

