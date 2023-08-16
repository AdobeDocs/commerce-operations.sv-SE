---
title: Bästa praxis för varukorgen
description: Lär dig optimera Adobe Commerce prestanda genom att begränsa antalet produkter i en kundvagn.
role: User
feature: Best Practices, Shopping Cart
exl-id: 7ea5acc2-f6b2-4244-8c07-c71fd54a18a0
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Bästa tillvägagångssätt för hantering av varukorgar

Använd följande riktlinjer för att hantera kundvagnsbegränsningar för Adobe Commerce och Magento Open Source för bästa prestanda:

- I version 2.3.x - 2.4.2 tillåts maximalt 100 produkter i en kundvagn.
- I version 2.4.3 och senare ökade kundvagnens maximala storlek till 750.


För version 2.3.x - 2.4.2 är förväntad prestanda baserad på artikelgränsen för kundvagn:

- Upp till **100** produkter i en kundvagn - produkten fungerar och uppfyller prestationsmålen för svarstid.
- Upp till **300** produkter i varukorgen - produkten fungerar, men svarstiden ökar mer än målen.
- Över **500** produkter i en kundvagn - korgen och kassaflödena fungerar inte

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Minska antalet varukorgsartiklar

Använd följande strategier för att hantera antalet kundvagnsartiklar

- Dela upp order i flera mindre order med ett mindre antal rader genom att använda [!UICONTROL Add Item by SKU] -funktion.
- Lägg bara till den anpassade logik och kundvagnsanpassning som krävs för att läsa in en lista med objekt.

## Potentiella resultateffekter

Om du har fler än det rekommenderade maximala antalet produkter i vagnen kan det påverka webbplatsens prestanda på följande sätt:

- Ökad svarstid för datahämtningsåtgärder, validering av varukorgsartiklar, kontroll av prisregler samt moms- och totalberäkningar.
- Ökad svarstid för minicart-rendering, inklusive rendering av kundvagnen, kassaflöde och exekvering.
- Ökad inläsningstid för alla webbplatssidor där miniatyrbilden finns.

## Ytterligare information

- [Konfigurera produktalternativ](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [Hantera en kundvagn](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
