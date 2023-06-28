---
title: Bästa praxis för konfiguration av produktalternativ
description: Optimera Adobe Commerce prestanda genom att begränsa antalet produktalternativ.
role: Admin
feature: Best Practices, Catalogs
exl-id: 7571a163-798a-40be-b26f-4a184bceb809
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Bästa praxis för produktalternativ

För bästa prestanda bör du konfigurera maximalt 100 produktalternativ per produkt.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Minska produktmöjligheterna

Använd följande strategier för att minska antalet produktalternativ för att få bästa prestanda för webbplatsen:

- Konfigurera komplexa produkter och anpassade alternativ som en källa till produktvariationer.
- I stället för att skapa globala produktmallar och alternativbehållare som gäller för alla produkter kan du använda attributuppsättningar för att skapa specifika produktmallar med riktade attribut och alternativ.
- Hantera produktinformation via ett externt produkthanteringssystem (PMS).

## Potentiell inverkan på prestanda

När du konfigurerar många produktalternativ ökar mängden data som hämtas för varje produkt vid alla läs- och skrivåtgärder, vilket resulterar i:

- Ökad SQL-frågetrafik och tyngre `JOIN` åtgärder ökar databasens genomströmning.
- Ökad storlek för Adobe Commerce-index och fulltextsökningsindex.

Ökningarna ovan kan påverka webbplatsens prestanda på följande sätt:

- Längre svarstid för de flesta butiksscenarier som är relaterade till produkter som innehåller många alternativ i attribut.
- Betydande ökning av den tid som krävs för att slutföra Product Management-åtgärder i Admin som kan leda till timeout, särskilt för scenarier som rör attributlista och hämtning av träd, inklusive hantering av kampanjregler.
- Kan blockera gruppåtgärder som slutför asynkrona massåtgärder som import och export och tilldela anpassade priser till flera produkter i en delad katalog.

## Ytterligare information

- [Skapa en produkt](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Bästa tillvägagångssätt för konfiguration av produktattribut](product-attributes-and-options.md)
- [Logg för gruppåtgärd](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [API för massåtgärder för lager](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [Utbildning: Hantera kataloger och produkter med Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
