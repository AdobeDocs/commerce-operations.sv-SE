---
title: Bästa praxis för utcheckning av prestanda
description: Lär dig hur du optimerar resultatet för utcheckningsupplevelser på din Adobe Commerce webbplats.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: e4c1832076bb81cd3e70ff279a6921ffb29ea631
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# Bästa praxis för utcheckning av prestanda

Processen [Checka ut](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) i Adobe Commerce är en viktig del av butiksupplevelsen. Den bygger på de inbyggda funktionerna [cart](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) och [checkout](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page) .

Prestanda är avgörande när det gäller att upprätthålla en bra användarupplevelse. Granska sammanfattningen för [prestandatestet](../implementation-playbook/infrastructure/performance/benchmarks.md) om du vill veta mer om prestandaförväntningarna. Du kan optimera utcheckningsprestanda genom att konfigurera följande alternativ för **bearbetning av order med hög genomströmning**:

- [AsyncOrder](#asynchronous-order-placement) - Bearbetar order asynkront med en kö.
- [Uppskjuten total beräkning](#deferred-total-calculation) - Skjut upp beräkningar för ordersummor tills utcheckningen börjar.
- [Inventeringskontroll vid kundvagnsinläsning](#disable-inventory-check) - Välj om du vill hoppa över lagervalidering av kundvagnsartiklar.
- [Lastbalansering](#load-balancing) - Aktivera sekundära anslutningar för MySQL-databasen och Redis-instansen.

Konfigurationsalternativen AsyncOrder, Laterred Total Calculation och Inventory Check on Cart Load fungerar alla oberoende av varandra. Du kan använda alla tre funktionerna samtidigt eller aktivera och inaktivera funktionerna i valfri kombination.

>[!NOTE]
>
>Använd inte anpassad PHP-kod för att anpassa de inbyggda funktionerna för kundvagn och utcheckning. Förutom potentiella prestandaproblem kan anpassad PHP-kod leda till komplexa uppgraderingar och underhållsproblem. De här problemen ökar din totala ägandekostnad. Om det inte går att undvika anpassningar av varukorgar och kassor använder du bara tillägg som godkänts av [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/). Alla tillägg på marknadsplatsen genomgår [omfattande granskning](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) för att verifiera att de uppfyller Adobe Commerce kodningsstandarder och bästa praxis.

## Asynkron orderplacering

Modulen _Asynkron ordning_ aktiverar asynkron placering av ordningen som `received`, placerar ordern i en kö och bearbetar order från kön första-i-första-ut-basis. AsyncOrder är **inaktiverad** som standard.

En kund lägger till exempel till en produkt i kundvagnen och väljer **[!UICONTROL Proceed to Checkout]**. De fyller i formuläret **[!UICONTROL Shipping Address]**, väljer önskad **[!UICONTROL Shipping Method]**, väljer en betalningsmetod och gör en beställning. Kundvagnen har rensats, ordern har markerats som **[!UICONTROL Received]**, men produktkvantiteten har inte justerats ännu och inte heller skickas ett e-postmeddelande till kunden. Ordern tas emot, men orderinformationen är inte tillgänglig än eftersom ordern inte har bearbetats fullständigt. Den ligger kvar i kön tills konsumenten `placeOrderProcess` börjar, verifierar ordern med funktionen [ lagerkontroll](#disable-inventory-check) (aktiverad som standard) och uppdaterar ordningen enligt följande:

- **Produkten är tillgänglig** - orderstatusen ändras till _Väntande_, produktkvantiteten justeras, ett e-postmeddelande med orderinformation skickas till kunden och den slutförda orderinformationen blir tillgänglig för visning i listan **Beställningar och Returer** med åtgärdbara alternativ, till exempel ändra ordning.
- **Produkten är inte i lager eller har låg leverans** - orderstatusen ändras till _Avvisad_, produktkvantiteten justeras inte, ett e-postmeddelande med orderinformation om utgåvan skickas till kunden och den avvisade orderinformationen blir tillgänglig i listan **Beställningar och Returer** utan några åtgärdbara alternativ.

Använd kommandoradsgränssnittet för att aktivera de här funktionerna eller redigera filen `app/etc/env.php` enligt motsvarande README-filer som definieras i [_Modulreferenshandboken_](https://developer.adobe.com/commerce/php/module-reference/).

**Så här aktiverar du AsyncOrder**:

Du kan aktivera AsyncOrder med kommandoradsgränssnittet:

```bash
bin/magento setup:config:set --checkout-async 1
```

Kommandot `set` skriver följande till filen `app/etc/env.php`:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Se [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) i _Modulens referenshandbok_.

**Så här inaktiverar du AsyncOrder**:

>[!WARNING]
>
>Innan du inaktiverar AsyncOrder-modulen måste du verifiera att _alla_ asynkrona orderprocesser är slutförda.

Du kan inaktivera AsyncOrder med kommandoradsgränssnittet:

```bash
bin/magento setup:config:set --checkout-async 0
```

Kommandot `set` skriver följande till filen `app/etc/env.php`:

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### AsyncOrder-kompatibilitet

AsyncOrder stöder en begränsad uppsättning Adobe Commerce-funktioner.

| Kategori | Funktion som stöds |
|------------------|--------------------------------------------------------------------------|
| Utcheckningstyper | OnePage-utcheckning<br>Standardutcheckning<br>Förhandlingsbar B2B-offert |
| Betalningsmetoder | Check/Money Order<br>Cash on Delivery<br>Braintree<br>PayPal PayFlow Pro |
| Leveransmetoder | Alla leveransmetoder stöds. |

Följande funktioner stöds **inte** av AsyncOrder, men fortsätter att fungera synkront:

- Betalningsmetoder som inte ingår i listan över funktioner som stöds
- Checka ut flera adresser
- Skapa administratörsorder

#### Stöd för webb-API

När modulen AsyncOrder är aktiverad körs följande REST-slutpunkter och GraphQL-mutationer asynkront:

**REST:**

- [`POST /V1/carts/mine/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/cartsminepayment-information#operation/PostV1CartsMinePaymentinformation)
- [`POST /V1/guest-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/guest-cartscartIdpayment-information#operation/PostV1GuestcartsCartIdPaymentinformation)
- [`POST /V1/negotiable-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/negotiable-cartscartIdpayment-information#operation/PostV1NegotiablecartsCartIdPaymentinformation)

**GraphQL:**

- [`placeOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)
- [`setPaymentMethodAndPlaceOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/set-payment-place-order/)

>[!INFO]
>
>GraphQL har inte stöd för att placera överlåtbara offertorder asynkront.

#### Utesluta betalningsmetoder

Utvecklare kan uttryckligen exkludera vissa betalningsmetoder från asynkron orderplacering genom att lägga till dem i `Magento\AsyncOrder\Model\OrderManagement::paymentMethods`-arrayen. Order som använder uteslutna betalningsmetoder behandlas synkront.

### Asynk order för överlåtbar offert

Med B2B-modulen _Förhandlingsbar offertasynkron ordning_ kan du spara orderobjekt asynkront för funktionen `NegotiableQuote`. AsyncOrder och NegotiableQuote måste vara aktiverade.

## Uppskjuten total beräkning

Modulen _Uppskjuten total beräkning_ optimerar utcheckningsprocessen genom att skjuta upp den totala beräkningen tills den begärs för kundvagnen eller under de sista utcheckningsstegen. När det här alternativet är aktiverat beräknas endast delsumman när kunden lägger till produkter i kundvagnen.

Uppskjuten total beräkning är **inaktiverad** som standard. Använd kommandoradsgränssnittet för att aktivera de här funktionerna eller redigera filen `app/etc/env.php` enligt motsvarande README-filer som definieras i [_Modulreferenshandboken_](https://developer.adobe.com/commerce/php/module-reference/).

**Så här aktiverar du DeferredTotalCalculation**:

Du kan aktivera DeferredTotalCalculation med kommandoradsgränssnittet:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

Kommandot `set` skriver följande till filen `app/etc/env.php`:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**Så här inaktiverar du DeferredTotalCalculation**:

Du kan inaktivera DeferredTotalCalculation med kommandoradsgränssnittet:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

Kommandot `set` skriver följande till filen `app/etc/env.php`:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Se [DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) i _referenshandboken för modulen_.

### Fast produktskatt

När Uppskjuten total beräkning är aktiverad inkluderas inte FPT (Fixed Product Tax) i produktpriset och kundvagnens delsumma efter att produkten lagts till i kundvagnen. FPT-beräkningen skjuts upp när en produkt läggs till i minivagnen. FPT visas korrekt i kundvagnen när du har gått till den slutliga utcheckningen.

## Inaktivera lagerkontroll

Den globala inställningen _Aktivera lager vid kundvagnsbeläggning_ avgör om en inventeringskontroll ska utföras när en produkt läses in i kundvagnen. Om du inaktiverar lagerkontrollprocessen förbättras prestanda för alla utcheckningssteg, särskilt när du hanterar bulkprodukter i vagnen.

När alternativet är inaktiverat görs ingen lagerkontroll när en produkt läggs till i kundvagnen. Om inventeringskontrollen hoppas över kan vissa scenarier utanför lagret ge upphov till andra typer av fel. En lagerkontroll _alltid_ utförs vid orderplaceringssteget, även när den är inaktiverad.

**Aktivera inläsning av kundvagn för lagerkontroll** är aktiverat (inställt på Ja) som standard. Om du vill inaktivera lagerkontrollen när vagnen läses in anger du **[!UICONTROL Enable Inventory Check On Cart Load]** till `No` i administratörsgränssnittet **Lagrar** > **Konfiguration** > **Katalog** > **Lager** > **Stock-alternativ** . Se [Konfigurera globala alternativ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) och [Kataloginventering](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) i _användarhandboken_.

## Belastningsutjämning

Du kan hjälpa till att balansera inläsningen mellan olika noder genom att aktivera sekundära anslutningar för MySQL-databasen och Redis-instansen.

Adobe Commerce kan läsa flera databaser eller Redis-instanser asynkront. Om du använder Commerce i en molninfrastruktur kan du konfigurera de sekundära anslutningarna genom att redigera värdena [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) och [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) i filen `.magento.env.yaml` . Endast en nod behöver hantera läs- och skrivtrafik, så om variablerna anges till `true` skapas en sekundär anslutning för skrivskyddad trafik. Ange värdena till `false` om du vill ta bort en befintlig skrivskyddad anslutningsmatris från filen `env.php`.

Exempel på filen `.magento.env.yaml`:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
