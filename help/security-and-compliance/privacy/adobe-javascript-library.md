---
title: Adobe Privacy JavaScript Library
description: Lär dig hur du använder anpassade verktyg för att komma åt och ta bort kundpersonuppgifter som samlats in av Adobe Commerce och Magento Open Source.
hide: true
hidefromtoc: true
source-git-commit: 495dfd515759e4df507479de57118586eac14fda
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# Adobe Privacy JavaScript Library

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

The [Adobe Privacy JavaScript Library](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) är en uppsättning verktyg som hjälper dig att skapa en process för att komma åt och ta bort privata data.

Adobe Commerce och Magento Open Source dataspårningstjänster kan lagra privat information som är tillämplig på sekretessregler som [Allmänna dataskyddsförordningen (GDPR)](gdpr.md) och [California Consumer Privacy Act (CCPA)](ccpa.md).

Det här biblioteket innehåller en enhetlig uppsättning funktioner för att skapa förfrågningar om sekretessdata, skicka dem till varje produkts implementeringar och samla in svaren. Använd det här biblioteket för att hämta och ta bort data som lagras i webbläsaren av dessa dataspårningstjänster.

## Installation

Hämta biblioteksfilen på något av följande sätt:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

När du har filen måste du lägga till den i en anpassad modul eller ett tema som är installerat i Adobe Commerce och Magento Open Source. Följ instruktionerna som beskrivs i [Använd anpassad JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) ämne som ska utföra den här uppgiften.

## Användning

JS-biblioteket för Adobe Privacy innehåller olika funktioner för att hantera identitetsdata som lagras i webbläsaren.

`retrieveIdentities()`
: Returnerar en array med identiteter från en tjänst tillsammans med en array med identiteter som inte finns i tjänsten

`removeIdentities()`
: Tar bort identiteter från webbläsaren och returnerar en array med identitetsobjekt med en `isDeleteClientSide` boolesk egenskap som anger om data har tagits bort.

`retrieveThenRemoveIdentities()`
: Den här funktionen liknar `removeIdentities()` på så sätt att den hämtar en array med identiteter och tar bort dem från webbläsaren.

Mer information och exempel på hur du använder dessa funktioner finns i [officiell biblioteksdokumentation](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html).

### Initiering

Instansiera en ny `AdobePrivacy` -objekt för att använda Adobe Privacy JS Library i din implementeringskod.

```js
var adobePrivacy = new AdobePrivacy({});
```

Konstruktorn accepterar ett konfigurationsobjekt med parametrar under instansieringen.
Se [officiell biblioteksdokumentation](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) för en lista över dessa konfigurationsparametrar.
