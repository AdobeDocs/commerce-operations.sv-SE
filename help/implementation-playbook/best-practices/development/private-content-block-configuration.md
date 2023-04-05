---
title: Bästa tillvägagångssätt för privata innehållsblock
description: Lär dig de bästa sätten att konfigurera privata innehållsblock för att optimera butiksprestanda.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Bästa tillvägagångssätt för privata innehållsblock

När ett privat innehållsblock innehåller `_isScopePrivate` -variabel är blocket inte tillgängligt. Eftersom det privata blocket inte cachelagras måste Adobe Commerce hämta samma data för varje kundbegäran, vilket ökar serverbelastningen.

I stället för att använda `_isScopePrivate` -variabel för privat innehåll skapar du ett block och en mall för att visa användaragnostiska data. Dessa data ersätts med användarspecifika data av Adobe Commerce UI-komponenten som hanterar data före återgivning mer effektivt. Instruktioner finns i [Privat innehåll](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) i _[!DNL Commerce PHP Extensions Guide]_.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Potentiell inverkan på prestanda

Webbplatser med privata innehållsblock som innehåller `_isScopePrivate` -variabler utlöser AJAX förfrågningar om att hämta samma data för varje kundförfrågan. Detta ökar svarstiden och använder ytterligare resurser som kan användas för att hantera mer affärskritiska butiksåtgärder som kundregistrering, kundvagnsuppdateringar, orderinlämning och betalningstransaktioner.

## Ytterligare information

- [Privat innehåll](../../../performance/configuration.md#client-side-optimization-settings)
- [Hög genomströmning AJAX begäranden orsakar dålig prestanda](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)


