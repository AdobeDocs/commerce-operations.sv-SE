---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.72'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.72.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: a6a18a4cbab9d2e5a0c4824fc5ad9463f9e61c1c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.72

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.72.

QPT v1.1.72 innehåller följande patchar:
1. **ACSD-68040**: Prestandan för frontend-söksidor försämras på [!DNL MariaDB] 10.6 och 11.4 med många historiksökbegäranden.
1. **ACSD-67941**: GraphQL-begäranden med okända filternamn orsakar PHP-undantagsloggar.
1. **ACSD-68064**: Om schemalagda uppdateringar skapas dubblettposter i miljöer med ett stort antal kapslade kategorier.
1. **ACSD-66807**: `report_viewed_product_index`-tabellen visar ett felaktigt antal produktsidesvisningar.
1. **ACSD-67383**: Inloggning som kund med två företagsadministratörskonton i samma session orsakar ett *Ingen sådan entitet med cartId*-fel.
1. **ACSD-67518**: Avancerad rapportering genererar duplicerade rubrikrader när radantalet överskrider batchstorleken.
1. **ACSD-67639**: Det går inte att skapa en kreditnota för paketprodukter med **[!UICONTROL Dynamic Price]** inställt på *No*.
1. **[ACSD-67696](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-72/acsd-67696.md)**: `media_gallery` poster returneras inte i produktnoden för kundvagnen i GraphQL efter en cachetömning.
1. **ACSD-67946**: I kundvagnsuppdateringar visas dubbla felbanderoller.
1. **ACSD-68011**: SKU:er som inte finns kan tilldelas till en delad katalog via `/V1/sharedCatalog/:id/assignProducts` [!DNL REST] API:t.
1. **ACSD-68118**: `customerCart` GraphQL-frågan returnerar produktattributvärden som inte återspeglar butikshuvudet, vilket orsakar inkonsekvent lokalisering.
1. **ACSD-68092**: Alternativ för paketprodukter går förlorade efter flera sparningar på grund av felaktig synkronisering mellan schemalagda uppdateringar och basproduktdata.
1. **ACSD-67424**: `updated_at` värdet i `GET /carts/search` [!DNL REST] API-svaret matchar inte värdet som visas i **[!UICONTROL Admin panel]** när Negotiable Quotes används.
1. **ACSD-67187**: Administratörsanvändare som är begränsade till icke-standardwebbplatser kan se felet *&quot;*Skapa minst en offentlig delad katalog för att fortsätta* och kan inte komma åt knappen **[!UICONTROL Add New Company]** i företagsrutnätet.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
