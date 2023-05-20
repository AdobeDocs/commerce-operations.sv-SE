---
title: Bearbetning av beställning med hög genomströmning
description: Optimera beställnings- och utcheckningsupplevelsen för Adobe Commerce eller Magento Open Source.
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 0%

---

# Bearbetning av stora mängder order

Du kan optimera orderplaceringen och utcheckningen genom att konfigurera följande uppsättning moduler för **orderhantering med hög genomströmning**:

- [AsyncOrder](#asynchronous-order-placement)—Beställningar bearbetas asynkront med en kö.
- [Uppskjuten total beräkning](#deferred-total-calculation)—Uppskjuter beräkningar för ordersummor tills utcheckningen börjar.
- [Lagerkontroll vid offertinläsning](#disable-inventory-check)- Välj att hoppa över lagervalidering av kundvagnsartiklar.

Alla funktioner - AsyncOrder, Deferred Total Calculation och Inventory Check - fungerar oberoende av varandra. Du kan använda alla tre funktionerna samtidigt eller aktivera och inaktivera funktioner i valfri kombination.

## Asynkron orderplacering

The _Asynkron ordning_ aktiverar asynkron placering av order, vilket markerar ordningen som `received`, placerar ordern i en kö och bearbetar order från kön först-i-först-ut-baserat. AsyncOrder är **inaktiverad** som standard.

En kund t.ex. lägger till en produkt i kundvagnen och väljer **[!UICONTROL Proceed to Checkout]**. De fyller ut **[!UICONTROL Shipping Address]** formulär, välj önskat **[!UICONTROL Shipping Method]**, väljer en betalningsmetod och gör en beställning. Kundvagnen är rensad, ordern är markerad som **[!UICONTROL Received]**, men produktkvantiteten har inte justerats ännu och inte heller skickas ett säljmejl till kunden. Ordern tas emot, men orderinformationen är inte tillgänglig än eftersom ordern inte har bearbetats fullständigt. Den finns kvar i kön tills `placeOrderProcess` konsumenten börjar, verifierar beställningen med [lagerkontroll](#disable-inventory-check) funktionen (aktiverad som standard) och uppdaterar ordningen enligt följande:

- **Produkten finns tillgänglig**—orderstatusen ändras till _Väntande_, produktkvantiteten justeras, ett e-postmeddelande med beställningsinformation skickas till kunden och beställningsinformationen blir tillgänglig för visning i **Beställningar och returer** lista med alternativ som kan ändras, t.ex. ändra ordning.
- **Produkt som inte finns i lager eller som har låg tillgång**—orderstatusen ändras till _Avvisad_, produktkvantiteten inte justeras, ett e-postmeddelande med beställningsinformation om problemet skickas till kunden och den avvisade beställningsinformationen blir tillgänglig i **Beställningar och returer** lista utan alternativ som kan användas.

Använd kommandoradsgränssnittet för att aktivera dessa funktioner eller redigera `app/etc/env.php` enligt motsvarande README-filer som definieras i [_Referenshandbok för modul_][mrg].

**Aktivera AsyncOrder**:

Du kan aktivera AsyncOrder med kommandoradsgränssnittet:

```bash
bin/magento setup:config:set --checkout-async 1
```

The `set` skriver följande till `app/etc/env.php` fil:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Se [AsyncOrder] i _Referenshandbok för modul_.

**Så här inaktiverar du AsyncOrder**:

>[!WARNING]
>
>Innan du inaktiverar modulen AsyncOrder måste du verifiera att _alla_ asynkrona orderprocesser är slutförda.

Du kan inaktivera AsyncOrder med kommandoradsgränssnittet:

```bash
bin/magento setup:config:set --checkout-async 0
```

The `set` skriver följande till `app/etc/env.php` fil:

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### AsyncOrder-kompatibilitet

AsyncOrder har stöd för en begränsad uppsättning [!DNL Commerce] funktioner.

| Kategori | Funktion som stöds |
|------------------|--------------------------------------------------------------------------|
| Utcheckningstyper | OnePage-utcheckning<br>Standardutcheckning<br>B2B - överlåtbar offert |
| Betalningsmetoder | Check-/penningorder<br>Kontant vid leverans<br>Braintree<br>PayPal PayFlow Pro |
| Leveransmetoder | Alla leveransmetoder stöds. |

Följande funktioner är **not** stöds av AsyncOrder, men fortsätter att fungera synkront:

- Betalningsmetoder som inte ingår i listan över funktioner som stöds
- Checka ut flera adresser
- Skapa administratörsorder

#### Stöd för webb-API

När modulen AsyncOrder är aktiverad körs följande REST-slutpunkter och GraphQL-mutationer asynkront:

**REST:**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL:**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL har inte stöd för att placera överlåtbara offertorder asynkront.

#### Utesluta betalningsmetoder

Utvecklare kan uttryckligen utesluta vissa betalningsmetoder från Asynchronous Order-placeringen genom att lägga till dem i `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` array. Order som använder uteslutna betalningsmetoder behandlas synkront.

### Asynk order för överlåtbar offert

The _Asynk order för överlåtbar offert_ Med B2B-modulen kan du spara orderobjekt asynkront för `NegotiableQuote` funktionalitet. AsyncOrder och NegotiableQuote måste vara aktiverade.

## Uppskjuten total beräkning

The _Uppskjuten total beräkning_ i kan du optimera utcheckningsprocessen genom att skjuta upp den totala beräkningen tills den begärs för kundvagnen eller under de slutliga utcheckningsstegen. När det här alternativet är aktiverat beräknas endast delsumman när kunden lägger till produkter i kundvagnen.

DeferredTotalCalculation är **inaktiverad** som standard. Använd kommandoradsgränssnittet för att aktivera dessa funktioner eller redigera `app/etc/env.php` enligt motsvarande README-filer som definieras i [_Referenshandbok för modul_][mrg].

**Aktivera uppskjutenTotalCalculation**:

Du kan aktivera DeferredTotalCalculation med kommandoradsgränssnittet:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

The `set` skriver följande till `app/etc/env.php` fil:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**Inaktivera uppskjutenTotalCalculation**:

Du kan inaktivera DeferredTotalCalculation med kommandoradsgränssnittet:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

The `set` skriver följande till `app/etc/env.php` fil:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Se [UppskjutenTotalBeräkning] i _Referenshandbok för modul_.

### Fast produktskatt

När DeferredTotalCalculation är aktiverat inkluderas inte FPT (Fixed Product Tax) i produktpriset och kundvagnens delsumma efter att produkten lagts till i kundvagnen. FPT-beräkningen skjuts upp när en produkt läggs till i minivagnen. FPT visas korrekt i kundvagnen när du har gått till den slutliga utcheckningen.

## Inaktivera lagerkontroll

The _Aktivera lager vid kundvagnsinläsning_ global inställning avgör om en inventeringskontroll ska utföras när en produkt läses in i kundvagnen. Om du inaktiverar lagerkontrollprocessen förbättras prestanda för alla utcheckningssteg, särskilt när du hanterar bulkprodukter i vagnen.

När alternativet är inaktiverat görs ingen lagerkontroll när en produkt läggs till i kundvagnen. Om inventeringskontrollen hoppas över kan vissa scenarier utanför lagret ge upphov till andra typer av fel. En lagerkontroll _alltid_ inträffar vid orderplaceringssteget, även när det är inaktiverat.

**Aktivera lagerkontroll vid vagninläsning** är aktiverat (inställt på Ja) som standard. Om du vill inaktivera lagerkontrollen när vagnen läses in anger du **[!UICONTROL Enable Inventory Check On Cart Load]** till `No` i administratörsgränssnittet **Lager** > **Konfiguration** > **Katalog** > **Lager** > **Alternativ för Stock** -avsnitt. Se [Konfigurera globala alternativ][global] och [Kataloginventering][inventory] i _Användarhandbok_.

## Belastningsutjämning

Du kan hjälpa till att balansera inläsningen mellan olika noder genom att aktivera sekundära anslutningar för MySQL-databasen och Redis-instansen.

Adobe Commerce kan läsa flera databaser eller Redis-instanser asynkront. Om du använder Commerce i molninfrastruktur kan du konfigurera de sekundära anslutningarna genom att redigera [MYSQL_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection) och [REDIS_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_use_slave_connection) värden i `.magento.env.yaml` -fil. Endast en nod behöver hantera läs- och skrivtrafik, så variabeln måste anges till `true` resulterar i att en sekundär anslutning skapas för skrivskyddad trafik. Ange värdena till `false` om du vill ta bort en befintlig skrivskyddad anslutningsmatris från `env.php` -fil.

Exempel på `.magento.env.yaml` fil:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

<!-- link definitions -->

[global]: https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/global-options.html
[inventory]: https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html
[mrg]: https://developer.adobe.com/commerce/php/module-reference/
[AsyncOrder]: https://developer.adobe.com/commerce/php/module-reference/module-async-order/
[UppskjutenTotalBeräkning]: https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/
