---
title: Sekretessbibliotek för JavaScript
description: Lär dig hur du använder anpassade verktyg för att komma åt och ta bort kundpersonuppgifter som samlats in av Adobe Commerce och Magento Open Source.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Sekretessbibliotek för JavaScript

JavaScript-biblioteket för skydd av privatlivet är en uppsättning verktyg för att skapa en process för åtkomst till och borttagning av privata data som samlats in av Adobe Commerce och Magento Open Source.

Tjänster för spårning av Commerce-data kan lagra privat information som är tillämplig på sekretessregler, t.ex. [Allmänna dataskyddsförordningen (GDPR)](gdpr.md) och [California Consumer Privacy Act (CCPA)](ccpa.md).

Det här biblioteket innehåller en uppsättning funktioner för att skapa förfrågningar om sekretessdata och samla in deras svar. Använd det här biblioteket för att hämta och ta bort data som lagras i webbläsaren av Adobe Commerce och Magento Open Source dataspårningstjänster.

>[!NOTE]
>
>If [Begränsningsläge för cookie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) är aktiverat samlar inte Commerce in beteendedata förrän kunden godkänner det. If [!UICONTROL **Begränsningsläge för cookie**] är inaktiverat samlar Commerce in beteendedata som standard.

## Installation

JavaScript-biblioteket för sekretess finns på följande CDN-plats: `commerce.adobe.net/magentoprivacy.js`

När du har filen måste du lägga till den i en anpassad modul eller ett tema som är installerat i Adobe Commerce- eller Magento Open Source-instansen. Följ instruktionerna som beskrivs i [Använd anpassad JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) ämne som ska utföra den här uppgiften.

### Initiering

Importera och instansiera en ny `MagentoPrivacy` eller använder `window` -objekt för att komma åt JavaScript-funktioner för sekretess.

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
Den här funktionen returnerar ett JavaScript-löfte för ett identitetsobjekt med ett `isDeleted` boolesk egenskap som anger om data har tagits bort.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
