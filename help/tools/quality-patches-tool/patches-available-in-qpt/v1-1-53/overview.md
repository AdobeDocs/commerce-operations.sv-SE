---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.53'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.53.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: e87723f395563b645d25bac6e6cb7887ce23f1ab
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.53

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som är tillgängliga i [!DNL Quality Patches Tool] (QPT) v1.1.53.

QPT v1.1.53 innehåller följande patchar:

1. **ACSD-48318**: Korrigerar problemet där miljöemuleringsinkapsling inte tillåts. Emuleringen startar under anropet `send()` när emuleringen stoppas under anropet till `getInfoBlockHtml()`.
1. **ACSD-59930**: Förbättrar prestanda för företagets *[!UICONTROL Create]*-, *[!UICONTROL Save]*- och *[!UICONTROL Delete]*-flöden.
1. **ACSD-60584**: Korrigerar problemet där en åtkomsttoken som skapats för användaren på en webbplats tillåts komma åt eller ändra kundinformation på andra webbplatser.
1. **ACSD-60804**: Korrigerar problemet där redigering av en kund som är länkad till ett borttaget företag orsakar felet *Anrop till en medlemsfunktion `getSuperUserId()` på null*.
1. **ACSD-61133**: Korrigerar problemet där `sales_clean_quotes` kron tar bort offerter från ej godkända inköpsorder.
1. **ACSD-61528**: Korrigerar problemet där hämtning av roller från [!UICONTROL Admin] med GraphQL inte ger några resultat.
1. **ACSD-61553**: Korrigerar problemet där *[!UICONTROL Cart Price Rule]* rabatter inte beräknas korrekt när flera rabatter med olika prioriteter och *[!UICONTROL Maximum Qty Discount is Applied To]* tillämpas på produkten.
1. **ACSD-61667**: Förbättrar lagerprestanda för att skapa leveranser för många källor med *In-Store-hämtning*.
1. **ACSD-61969**: Korrigerar problemet där användaren måste skriva in en skiftlägeskänslig kupongkod som exakt matchar den konfigurerade kupongkoden.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
