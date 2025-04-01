---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.61'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.61.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 0800285df83eb3e3ffcfb003bf984248b750db32
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.61

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som är tillgängliga i [!DNL Quality Patches Tool] (QPT) v1.1.61.

QPT v1.1.61 innehåller följande patchar:

1. **ACP2E-3689**: Korrigerar flera problem med kategoriträdvisning på djupare nivåer och reflekterar ankarpunktsrelationer/icke-ankarrelationer.
1. **ACP2E-3705**: Korrigerar ett fel där körningen av `indexer_update_all_views` kron misslyckas när `MAGE_INDEXER_THREADS_COUNT` är inställd.
1. **ACSD-63883**: Korrigerar problemet där [!UICONTROL Requisition List] returnerar ett felaktigt `items_count` i [!DNL GraphQL]-svaret.
1. **ACSD-63974**: Korrigerar problemet där [!UICONTROL Requisition List] -sidan tar för lång tid att läsa in när det finns för många objekt. Genom att lägga till en sidnumreringsfunktion i [!UICONTROL Requisition List]-rutnätet på butiken, som endast visar delar av poster som är begränsade till antalet poster per sida, i stället för alla poster samtidigt.
1. **ACSD-64178**: Korrigerar problemet där redigeringssidan för [!UICONTROL Attribute Set] läses in långsamt om det finns tusentals produktattribut.
1. **ACSD-64209**: Korrigerar problemet där cron Scheduler hämtar alla överlåtbara offerter utan att utesluta dem med statusen **[!UICONTROL ordered]**, vilket medför att ett e-postmeddelande eller e-postmeddelande utlöses.
1. **ACSD-64431**: Den `placeOrder`-mutation som innehåller kupongkodinformationen i begäran genererar inte längre ett internt fel, utan visar i stället att ordern har placerats korrekt.
1. **ACSD-64467**: Korrigerar problemet där WYSIWYG-redigeraren verkar vara tom efter att en kategoribeskrivning har sparats på butiksvynivån.
1. **ACSD-64546**: Korrigerar problemet där ett generiskt felmeddelande visas i användargränssnittet och ett *Array-konverteringsundantag* lagras i loggarna när UPS-leveransetiketter skapas, vilket säkerställer att det faktiska felet visas i användargränssnittet och att rätt felmeddelande sparas i loggarna.
1. **ACSD-64684**: Korrigerar problemet där ett valideringsfel inträffar när du redigerar och sparar ett presentkort med ett värde som är större än *999* på grund av kommatecken (tusentalsavgränsare) i talet *ett tusen (1 000)*.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
