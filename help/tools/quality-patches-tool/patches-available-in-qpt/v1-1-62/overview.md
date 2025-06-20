---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.62'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.62.
feature: Tools and External Services
role: Admin, Developer
exl-id: be8ffedc-b589-4a30-ba9a-eed705696825
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.62

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som är tillgängliga i [!DNL Quality Patches Tool] (QPT) v1.1.62.

QPT v1.1.62 innehåller följande patchar:

1. **ACSD-63406**: Korrigerar problemet där utgångna beständiga citattecken inte rensas av något cron-jobb när kron-jobbet `persistent_clear_expired` körs.
1. **ACSD-63520**: Korrigerar problemet där bilder som läggs till via **[!UICONTROL Configurations]** på administratörspanelen inte uppfyller den maximala gränsen för överföringsstorlek.
1. **ACSD-64523**: Korrigerar problemet där nya produkter kunde skapas utan ett namn via importprocessen (via admin eller API), vilket gjorde att administratörsgränssnittet bröts och resulterade i ogiltiga produkter.
1. **ACSD-64532**: Korrigerar problemet där en ENV-variabel som är inställd på *false* behandlas som en sträng *false* i stället för som booleskt falskt.
1. **ACSD-64592**: Korrigerar problemet där anspråkslänken från e-postmeddelandet för ett presentkort i icke-standardbutiker alltid omdirigerade presentkortsanspråket till standardwebbplatsen.
1. **ACSD-65164**: Korrigerar problemet där felmeddelandet *Vissa av de valda objektalternativen inte är tillgängliga* inträffar när en konfigurerbar produkt med ett enda anpassat kryssrutealternativ sorteras.
1. **ACSD-64732**: Korrigerar problemet där externa styrenheter inte cachelagrades korrekt med kundsegment.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
