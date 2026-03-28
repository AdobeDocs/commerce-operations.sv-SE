---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.77'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.77.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 98ccb5c357ebcb3bc2a7bb48e61b8557a65049f9
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.77

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.77.

QPT v1.1.77 innehåller följande patchar:

1. **[ACSD-63687](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-63687.md)**: Korrigerar ett fel där felaktiga priser visas eftersom det inte går att rensa [!DNL Redis]-cachen.
1. **[ACSD-68341](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68341.md)**: Korrigerar ett fel där `X-Magento-Vary` cookie ställs in flera gånger under PDP-inläsning när flera kundsegment skapas i butiken.
1. **[ACSD-68537](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68537.md)**: Korrigerar ett fel där utcheckningsprestanda försämrades när antalet kundsegment ökade.
1. **[ACSD-68664](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68664.md)**: Korrigerar ett fel där förhandsgranskningen av den schemalagda uppdateringen avbryts vid försök att förhandsgranska innehåll för butiker med anpassade domäner.
1. **[ACSD-68759](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68759.md)**: Korrigerar ett problem där det inte går att skapa ett kundkonto när den arabiska språkversionen används och där attributet Födelsedatum (DOB) är inställt på att visas i butiken.
1. **[ACSD-68892](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68892.md)**: Korrigerar ett fel där cachebara sidor inte lagras eller hanteras korrekt från [!DNL Fastly]-cachen, vilket resulterar i inkonsekvent cachningsbeteende och försämrade prestanda.
1. **[ACSD-69016](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69016.md)**: Korrigerar ett fel där specialpriset inte gäller för webbplatser som skapats i olika tidszoner.
1. **[ACSD-69020](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69020.md)**: Korrigerar ett fel där en konfigurerbar produkt automatiskt inkluderas i [!DNL Page Builder] produktkaruselllistor om någon av dess underordnade produkter uppfyller filtervillkoren.
1. **[ACSD-69237](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69237.md)**: Korrigerar ett fel där antalet poster som kan bearbetas och infogas genom `sales_*_async_insert` kronjobb är begränsat till *100* per körning.
1. **[ACSD-69311](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69311.md)**: Korrigerar ett problem med felaktig momsberäkning i kreditnotor när en partiell återbetalning skapas från en faktura, om en tidigare kreditnota skapades från ordervysidan.
1. **[ACSD-69351](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69351.md)**: Korrigerar ett problem där presentkortssaldon och utgångsdatum inte visas i enlighet med det tilldelade webbplatsomfånget.
1. **[ACSD-69494](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69494.md)**: Korrigerar ett problem med asynkrona återbetalningsåtgärder där återbetalningsbegäranden med parametern `is_online` inte behandlas korrekt.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
