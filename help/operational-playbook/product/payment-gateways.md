---
title: Betalningsgateways
description: Välj en leverantör av betaltjänster för ditt e-handelsprojekt baserat på ditt företags behov.
exl-id: eab50191-0744-41da-99ba-2e06ea61da27
feature: Best Practices, Payments
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# Betalningsgateways

Det fanns en tid då kontanter var huvudkällan till transaktioner, men onlinevärlden har tagit över och onlinebetalningsmetoderna ersätter gamla betalningsmetoder. Allt finns nu online, vilket gör det enklare och mer tillgängligt, inklusive kreditkort, e-plånböcker och banköverföringar.

![Leverantörslogotyper för betalningsgateway](../../assets/playbooks/payment-gateways.png)

En betalningstjänst är en tjänsteleverantör som ansluter och bearbetar betalningar för e-handelswebbplatser. De spelar en viktig roll när det gäller kundupplevelsen och konverteringsgraden. Komplexa betalningssystem tenderar att få kunderna att överge sina kundvagnar. Det är viktigt att ge kunderna ett enkelt, användarvänligt betalningssystem där även om en betalningsmetod misslyckas, har de en alternativ metod att motivera dem att slutföra köpet.

## Granska krav

Återförsäljarna måste välja den bästa betalningsgatewayen som uppfyller deras krav. Det finns många betalningslösningar på marknaden, som Braintree och Stripe, men innan du bestämmer dig för en betalningstjänst kan du ställa följande frågor:

- Vad har jag för affärskrav?
- Är det inom min budget?
- Hur stark är säkerheten på betalningsgatewayen?
- Kommer min butiksgränssnitt att påverkas?
- Hur bra fungerar betalningstjänsten?
- Hur fungerar supportservicen för betalningsgatewayen efter köpet?
- Vilken betalningstjänst passar mig bäst?
- Erbjuder betalningstjänsten andra funktioner, som att beräkna skatt, använda geolokalisering och beräkna serviceavgift?

Det finns vissa begränsningar för betalningsgatewayar som du måste känna till, bland annat:

- Alla typer av kort accepteras inte av betalningsgateways.
- Vissa betalningsalternativ kanske inte är tillgängliga för internationella kunder.
- Säkerhetsluckor i betalningstjänsten. På grund av säkerhetsskäl är det ofta svårt att lägga onlineorder.

När ett företag bestämmer sig för att integrera en betalningstjänst med sin plattform är det alltid bättre att se hur den ser ut i butiken, vilken typ av upplevelse den ger kunderna och om den är användarvänlig. Se även till att säkerheten för betalningen inte kan äventyras. En bra och säker fungerande betalningstjänst ger en bättre kundupplevelse.

## B2B- och B2C-aspekter

B2B- och B2C-företag har liknande betalningssystem, men B2B-företag har fler regler, bestämmelser och processer. B2B-företag tenderar att handla i större volymer jämfört med B2C-företag.

B2C-kunder köper produkter eller tjänster för enskilt bruk. Kunderna betalar vanligtvis samma pris som andra kunder och det är ingen förhandling. B2B-kunder har olika intressenter, vilket gör godkännandet mer komplicerat och dyrt.

B2B-kunder har olika beställningar och krav som måste behandlas och godkännas av säljaren eller en säljare måste involveras när en kund köper online med en anbudsförfrågan eller en inköpsorder.

B2C-betalningar kan vara engångs och ger mindre värde. Kunderna lägger till produkter i kundvagnen och checkar ut med hjälp av en säker betalning med kreditkort eller e-plånbok.

På grund av B2B-transaktionernas höga inköpsvärde erbjuder B2B-företag fler betalningsalternativ utöver standardalternativen, som checkar, banköverföringar och inköpsorder.

Rätt betalningsalternativ baseras på verksamhetens och verksamhetens behov.
