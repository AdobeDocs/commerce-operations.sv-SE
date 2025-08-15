---
title: Bästa tillvägagångssätt för privata innehållsblock
description: Lär dig de bästa sätten att konfigurera privata innehållsblock för att optimera butiksprestanda.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Bästa tillvägagångssätt för privata innehållsblock

När ett privat innehållsblock innehåller variabeln `_isScopePrivate` är blocket inte tillgängligt. Eftersom det privata blocket inte cachelagras måste Adobe Commerce hämta samma data för varje kundbegäran, vilket ökar serverbelastningen.

I stället för att använda variabeln `_isScopePrivate` för privat innehåll skapar du ett block och en mall för att visa användaragnostiska data. Dessa data ersätts med användarspecifika data av Adobe Commerce UI-komponenten som hanterar data före återgivning mer effektivt. Instruktioner finns i [Privat innehåll](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) i _[!DNL Commerce PHP Extensions Guide]_.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Potentiell inverkan på prestanda

Webbplatser med privata innehållsblock som innehåller variablerna `_isScopePrivate` utlöser AJAX-begäranden om att hämta samma data för varje kundbegäran. Detta ökar svarstiden och använder ytterligare resurser som kan användas för att hantera mer affärskritiska butiksåtgärder som kundregistrering, kundvagnsuppdateringar, orderinlämning och betalningstransaktioner.

## Ytterligare information

- [Privat innehåll](../../../performance/configuration.md#client-side-optimization-settings)
- [Högt dataflöde AJAX-begäranden orsakar dålig prestanda](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html?lang=sv-SE)
