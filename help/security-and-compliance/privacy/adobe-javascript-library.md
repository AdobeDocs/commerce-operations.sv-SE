---
title: Adobe Privacy JavaScript Library
description: Lär dig hur du använder anpassade verktyg för att komma åt och ta bort kundpersonuppgifter som samlats in av Adobe Commerce.
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Adobe Privacy JavaScript Library

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

JavaScript-biblioteket [Adobe Integritet](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=sv-SE) är en uppsättning verktyg som hjälper dig att skapa en process för att komma åt och ta bort privata data.

Adobe Commerce dataspårningstjänster kan lagra privat information som är tillämplig på sekretessbestämmelser, som [General Data Protection Regulation (GDPR)](gdpr.md) och [California Consumer Privacy Act (CCPA)](ccpa.md).

Det här biblioteket innehåller en enhetlig uppsättning funktioner för att skapa förfrågningar om sekretessdata, skicka dem till varje produkts implementeringar och samla in svaren. Använd det här biblioteket för att hämta och ta bort data som lagras i webbläsaren av dessa dataspårningstjänster.

## Installation

Hämta biblioteksfilen på något av följande sätt:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

När du har filen måste du lägga till den i en anpassad modul eller ett anpassat tema som är installerat i din Adobe Commerce-instans. Följ instruktionerna som beskrivs i avsnittet [Använd anpassad JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) för att utföra den här åtgärden.

## Användning

JS-biblioteket för Adobe Privacy innehåller olika funktioner för att hantera identitetsdata som lagras i webbläsaren.

`retrieveIdentities()`
: Returnerar en array med identiteter från en tjänst tillsammans med en array med identiteter som inte finns i tjänsten

`removeIdentities()`
: Tar bort identiteter från webbläsaren och returnerar en array med identitetsobjekt med en `isDeleteClientSide` boolesk egenskap som anger om data har tagits bort.

`retrieveThenRemoveIdentities()`
: Den här funktionen liknar `removeIdentities()` eftersom den hämtar en array med identiteter och tar bort dem från webbläsaren.

Mer information och exempel på hur du använder dessa funktioner finns i [den officiella biblioteksdokumentationen](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=sv-SE).

### Initiering

Skapa en instans av ett nytt `AdobePrivacy`-objekt för att använda JS-biblioteket för AdobePrivacy i din implementeringskod.

```js
var adobePrivacy = new AdobePrivacy({});
```

Konstruktorn accepterar ett konfigurationsobjekt med parametrar under instansieringen.
En lista med de här konfigurationsparametrarna finns i [den officiella biblioteksdokumentationen](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=sv-SE).
