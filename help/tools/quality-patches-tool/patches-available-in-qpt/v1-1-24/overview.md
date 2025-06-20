---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.24'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.24.
feature: Tools and External Services
role: Admin
exl-id: 7f88a28b-f166-4c5b-8d69-239c57cc4001
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.1.24 - översikt

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.24.

QPT v1.1.24 innehåller följande patchar:

1. **ACSD-45168**: Korrigerar problemet där SEO-vänliga URL:er inte genereras för produkter som har *url_key* -attribut åsidosatta på butiksvisningsnivå.
1. **ACSD-46617**: Korrigerar problemet där knappen **[!UICONTROL Continue to Checkout]** är nedtonad även om delsumman är större än det konfigurerade *minimiorderbeloppet*.
1. **ACSD-46770**: Korrigerar problemet där e-postmeddelanden om administratörsorder skickas, även när *bekräftelsen av e-postorder* inte är markerad.
1. **ACSD-46865**: Korrigerar problemet där stödrastret [!UICONTROL Shipment and Credit Memo] inte fylls i när asynkron indexering är aktiverat.
1. **ACSD-47004**: Korrigerar problemet där moms inte tillämpas på en faktureringsadress utan moms-ID.
1. **ACSD-47079**: Korrigerar problemet där sammansatta produkter (bundle, grouped och configurable) inte uppdateras när delproduktens lagerstatus ändras via REST API POST /rest/V1/lager/source-items.
1. **ACSD-47137**: Förbättrar inläsningshastigheten för bildgalleriet när mappen för pub/media är mycket stor.
1. **ACSD-47336**: Korrigeringar *Något gick fel.*-fel när meddelanden i Commerce Admin stängs av.
1. **ACSD-47559**: Korrigerar problemet där e-postmallen för förhandsgranskning inte är helt synlig.
1. **ACSD-47803**: Korrigerar problemet där ej lagrade konfigurerbara produktfärgrutor visas som tillgängliga.
1. **ACSD-47920**: Korrigerar problemet där order kan placeras via Rest API som gästanvändare även när *Tillåt gästutcheckning* är inaktiverat.
1. **ACSD-47955**: Korrigerar problemet där kundvagnsrabatten inte visas korrekt i GraphQL.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
