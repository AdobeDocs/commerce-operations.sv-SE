---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.55'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.55.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 97b52220f3b254ee17705a22137693abc6008c72
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.55

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som är tillgängliga i [!DNL Quality Patches Tool] (QPT) v1.1.55.

QPT v1.1.55 innehåller följande patchar:

1. **ACSD-58383**: Korrigerar problemet där en återbetalning skapas via [!DNL REST API] med två identiska begäranden som körs samtidigt, vilket skapar dubbla kreditnotor.
1. **ACSD-58471**: Korrigerar problemet där dynamiskt innehåll inte kan läsas in på produktinformationssidan när de associerade katalogprisreglerna är schemalagda.
1. **ACSD-58566**: Korrigerar problemet där [!DNL GraphQL] returnerar ett internt serverfel när fältet `created_at` i mutationen `addPurchaseOrderComment` efterfrågas.
1. **ACSD-58685**: Korrigerar ett problem där e-postmeddelanden som initieras när e-postkommunikation inaktiveras fortfarande skickas när e-postkommunikation återaktiveras.
1. **ACSD-58735**: Korrigerar problemet där en begränsad administratör inte kan visa de övergivna kundvagnarna på kundkontosidan i [!UICONTROL Admin] för en associerad webbplats.
1. **ACSD-58828**: Korrigerar problemet där verifieringsmeddelandet *på serversidan krävs* visas om ett obligatoriskt fält lämnas tomt, tillsammans med valideringsmeddelandet på klientsidan. Verifieringen på serversidan visar inte meddelandet om tomma obligatoriska fält, och verifieringen på klientsidan kommer att hantera felmeddelandet med meddelandet *Detta är ett obligatoriskt fält.*
1. **ACSD-60344**: Korrigerar problemet där dubbla orderbekräftelsemeddelanden skickas när en **[!UICONTROL Purchase Order]** används med automatiskt godkännande.
1. **ACSD-61348**: Korrigerar problemet där önskelisteobjekt visas via [!DNL GraphQL], men inte på butiken i en miljö med flera webbplatser.
1. **ACSD-61534**: Korrigerar problemet där designkonfigurationen inte kan anges med kommandot `bin/magento config:set` och låsta värden kan ändras med formulärhantering. Låsta värden som angetts från [!DNL CLI] med `--lock-env` eller `--lock-conf` kan inte uppdateras.
1. **ACSD-61785**: Korrigerar problemet där det inte går att uppdatera attributet `reward_warning_notification` via [!DNL GraphQL] mutation och [!DNL REST API] anrop, vilket anpassar beteendet till `reward_update_notification`.
1. **ACSD-62591**: Korrigerar problemet där temat inte växlar korrekt när **[!UICONTROL User Agent Rules]** har konfigurerats.
1. **ACSD-62793**: Korrigerar problemet där `datetime` -attribut i exporterade data inte innehåller tidskomponenten. Om *[!UICONTROL Fields Enclosure]* dessutom är *aktiverad* omges attributvärden i kolumnen `additional_attributes` av citattecken.
1. **ACSD-62332**: Korrigerar problemet där produktlistans [!DNL GraphQL] -fråga är begränsad till `total_count` av 10 000 produkter. Åtgärdar även problemet där [!DNL Live Search] ställer in den aktuella sidan på ** i stället för sidan ** i sökvillkoren när frågan ställs via [!DNL GraphQL].

Använd menyn till vänster för att navigera till en viss korrigeringssida.
