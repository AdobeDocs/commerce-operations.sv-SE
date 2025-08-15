---
title: Sekretessbibliotek för JavaScript
description: Lär dig hur du använder anpassade verktyg för att komma åt och ta bort kundpersonuppgifter som samlats in av Adobe Commerce.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Sekretessbibliotek för JavaScript

JavaScript Sekretessbibliotek är en uppsättning verktyg som hjälper dig att skapa en process för att komma åt och ta bort privata data som samlats in av Adobe Commerce.

Commerce dataspårningstjänster kan lagra privat information som är tillämplig på sekretessbestämmelser, som [General Data Protection Regulation (GDPR)](gdpr.md) och [California Consumer Privacy Act (CCPA)](ccpa.md).

Det här biblioteket innehåller en uppsättning funktioner för att skapa förfrågningar om sekretessdata och samla in deras svar. Använd det här biblioteket för att hämta och ta bort data som lagras i webbläsaren av Adobe Commerce dataspårningstjänst.

>[!NOTE]
>
>Om [läget för cookie-begränsning](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) är aktiverat samlar Commerce inte in beteendedata förrän kunden godkänner det. Om [!UICONTROL **läget för cookie-begränsning**] är inaktiverat samlar Commerce in beteendedata som standard.

## Installation

Sekretessbiblioteket för JavaScript finns på följande CDN-plats: `commerce.adobe.net/magentoprivacy.js`

När du har filen måste du lägga till den i en anpassad modul eller ett anpassat tema som är installerat i din Adobe Commerce-instans. Följ instruktionerna som beskrivs i avsnittet [Använd anpassad JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) för att utföra den här åtgärden.

### Initiering

Importera och instansiera ett nytt `MagentoPrivacy`-objekt eller använd `window`-objektet för att komma åt JavaScript sekretessfunktioner.

Exempel med `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

Exempel med `window`:

```js
const magePriv = new window.MagentoPrivacy()
```

## Användning

JS-biblioteket för sekretess innehåller olika funktioner för att hantera identitetsdata som lagras i webbläsaren.

`retrieveIdentity()`
: Returnerar ett JavaScript-löfte för ett identitetsobjekt från en tjänst i webbläsaren.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: Tar bort identitetsdata från en tjänst i webbläsaren.
Den här funktionen returnerar ett JavaScript-löfte för ett identitetsobjekt med en boolesk egenskap på `isDeleted` som anger om data har tagits bort.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
