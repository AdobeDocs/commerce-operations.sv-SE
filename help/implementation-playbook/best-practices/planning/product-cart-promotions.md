---
title: Bästa tillvägagångssätt för att konfigurera kampanjer
description: Lär dig de bästa sätten att konfigurera försäljningsregler och kupongkoder för att optimera Commerce Store-prestanda.
role: User
feature: Best Practices, Price Rules, Shopping Cart
exl-id: 6e177836-b8da-4e55-842c-e12ff54ffaf5
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Bästa tillvägagångssätt för att konfigurera kampanjer

För bästa prestanda bör du följa de här bästa metoderna för att konfigurera försäljning och kampanjer för artiklar i en kundvagn:

- **Försäljningsregler (kundprisregler)**-Konfigurera inte fler än 1000 kundvagnsregler för alla webbplatser
   - Hantera och ta bort oanvända regler.
   - Lägg till strikta regelvillkor (som attribut- eller kategorifilter) för den mest effektiva matchningen.
- **Kuponger**—
   - Kontrollera att det totala antalet kuponger i databasen är mindre än 250 000.
   - Ta bort oanvända och utgångna kuponger.
   - Generera endast det antal kuponger som behövs för att uppfylla kampanjkraven.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Potentiella resultateffekter

Om du har fler än det rekommenderade maximala antalet kundvagnsregler eller kuponger kan det påverka webbplatsens prestanda på följande sätt:

- Ökad svarstid när produkter läggs till i kundvagnen.
- Ökad tid för inläsning och rendering av minikortet.
- Den tid det tog att återge kundvagnssidan ökade.
- Ökad tid för att återge **Summor** -block på utcheckningssidan.
- Att tillämpa kuponger kan ta mer än 2 sekunder.

## Ytterligare information

- [Förstå marknadsföringskampanjer och kampanjer](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [Kundprisregler](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [Självstudie: Skapa en kundvagnsprisregel](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [Kupongkoder](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce om molninfrastruktur: Bästa metoder för butikskonfiguration](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
