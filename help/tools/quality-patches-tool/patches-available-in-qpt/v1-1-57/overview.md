---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.57'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.57.
feature: Tools and External Services
role: Admin, Developer
exl-id: 3e252a71-f35f-4046-9353-169060451ffe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.57

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.57.

QPT v1.1.57 innehåller följande patchar:

1. **ACSD-57570**: Korrigerar problemet där en begränsad administratörsanvändare med åtkomst till en viss butik inte alltid kan se alla delade kataloger som produkterna är tilldelade till eller kan se kunder som inte kan spara, vilket leder till inkonsekvenser i systemet.
1. **ACSD-58325**: Korrigerar problemet där knappen [!UICONTROL Import] är tillgänglig även efter ett valideringsfel.
1. **ACSD-59083**: Korrigerar problemet där vissa databasuppdateringsåtgärder resulterar i felet _Bastabell eller vy hittades inte_ om [!DNL mview]-uppdateringen körs samtidigt.
1. **ACSD-61622**: Korrigerar problemet där [!DNL FedEx] kontospecifika frekvenser saknas i svaret. ACSD-61622 ersätter den korrigering som beskrivs i [[!DNL FedEx] migrering av integrering av leveransmetoder från [!DNL SOAP] till [!DNL RESTful API]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/fedex-shipping-method-integration-migration-soap-restful-api).
1. **ACSD-61895**: Korrigerar problemet där kategorifrågan [!DNL GraphQL] returnerar kategorier med behörigheten *allow* även om rotkategorin inte har behörigheten *allow* .
1. **ACSD-62212**: Korrigerar problemet där e-postinnehållet i [!UICONTROL Forgot Password] inte översätts till butiksvyns språk.
1. **ACSD-62481**: Korrigerar problemet där kundens kundvagn blir tom även om [!UICONTROL Persistence] är aktiverat.
1. **ACSD-62629**: Korrigerar problemet där en produktlista som används i [!UICONTROL Widgets] inte uppfyller kategorivillkoret.
1. **ACSD-62635**: Korrigerar problemet där produkter som är relaterade till flera lager inte visas korrekt i produktfrågan för [!DNL GraphQL].
1. **ACSD-62671**: Korrigerar problemet där [!DNL GraphQL]-begäran inte returnerar aktuell adressinformation vid det första försöket.
1. **ACSD-62689**: Korrigerar problemet där kunden inte kan lägga till kategorier i [!UICONTROL Related Product Rules] och [!UICONTROL Widgets] efter djup 4.
1. **ACSD-62708**: Korrigerar problemet där [!DNL TinyMCE] 7-redigeringsteckenstorleken i administratören visar [!UICONTROL pt] och inte [!UICONTROL px] efter korrigeringen från [!UICONTROL ACP2E-3430]. Nu kan du även ange teckenstorleken i [!UICONTROL px] i stället för [!UICONTROL pt].
1. **ACSD-62758**: Korrigerar problemet där produktvideor inte återges korrekt på informationssidan för [!UICONTROL Configurable Product] om URL:en innehåller valda alternativ.
1. **ACSD-62951**: Korrigerar problemet där e-postmeddelandet [!UICONTROL Credit Memo] skickas utan att några objekt eller summor tas med.
1. **ACSD-62965**: Korrigerar problemet där ett *LocalizedException* -meddelande inte ingår i orderplaceringen [!DNL GraphQL response].
1. **ACSD-63286**: Korrigerar problemet där produkter som tilldelats till en delad katalog via API inte visas på butiken förrän en manuell omindexering har utförts.
1. **ACSD-63326**: Korrigerar problemet där administratören omdirigeras till en skadad sida efter att en beställning från serverdelen har gjorts.


Använd menyn till vänster för att navigera till en viss korrigeringssida.
