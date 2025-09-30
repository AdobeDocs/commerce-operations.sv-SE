---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.71'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.71.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 57fea42c0c893166c3489f6b95e09ccba787b9f1
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.71

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.71.

QPT v1.1.71 innehåller följande patchar:


* **ACSD-60624**: **[!UICONTROL Upload Image]** fungerar inte för tomt innehåll i avsnitten [!UICONTROL Image], [!UICONTROL Banner] och [!UICONTROL Slider] i [!DNL Page Builder].
* **ACSD-67089**: Problem med sidnumrering i `inventory/export-stock-salable-qty` API, som felaktigt begränsar `total_count` till sidstorleken.
* **ACSD-67093**: Om du hämtar order via [!DNL GraphQL] med datumintervallfiltret returneras felaktiga resultat.
* **ACSD-67459**: Produkter med beskrivningar som är längre än 65 536 tecken kan inte importeras.
* **ACSD-67603**: Långa bearbetningstider för webbplatskartor för produkter där avbildningsinkludering är aktiverat
* **ACSD-67643**: Dubblettposter skapas under schemalagda uppdateringar i miljöer med ett stort antal kapslade kategorier.
* **ACSD-67652**: Paketproduktstatus returneras som ej i lager i [!DNL GraphQL] anrop, även med underordnade och överordnade produkter i lager.
* **ACSD-67904**: Det går inte att placera order om stadsnamnet innehåller siffror (0-9), et-tecken (&amp;), punkt (.) eller parenteser ().

Använd menyn till vänster för att navigera till en viss korrigeringssida.
