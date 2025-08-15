---
title: Ändra öknings-ID
description: Ändra ID för ökning för en Commerce-databasenhet.
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 2a45fe77d5a6fac089ae2c55d0ad047064dd07b0
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Ändra öknings-ID

I den här artikeln beskrivs hur du ändrar tilläggs-ID för en Commerce-databasentitet (order, faktura, kreditnota och så vidare) på en viss Commerce-butik med hjälp av SQL-satsen `ALTER TABLE`.

## Berörda versioner

- Adobe Commerce (lokalt): 2.x.x
- Adobe Commerce i molninfrastruktur: 2.x.x
- MySQL: [alla versioner som stöds](../../installation/prerequisites/database/mysql.md)

## När behöver du ändra ID för ökning

Du kan behöva ändra ID:t för ökning för nya DB-entiteter i följande fall:

- Efter en återställning av en hård säkerhetskopiering på en Live-webbplats
- Vissa orderposter har gått förlorade, men deras ID används redan av betalningsgateways (som PayPal) för ditt aktuella Merchant-konto. Så är fallet, så upphör betalningsgatewayen att bearbeta nya order som har samma ID, vilket returnerar felet &quot;Duplicera faktura-ID&quot;

>[!INFO]
>
>Du kan också åtgärda problemet med betalningsgateway för PayPal genom att tillåta flera betalningar per faktura-ID i PayPals Inställningar för betalningsmottagning. Se [PayPal-gateway avvisade begäran - dubblettfakturaproblem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.html) i _kunskapsbasen_.

## Krav på steg

1. Sök efter butiker och enheter som det nya tilläggs-ID:t ska ändras för.
1. Anslut till MySQL-databasen.
För Adobe Commerce i molninfrastruktur måste du först ansluta med SSH till din miljö.
1. Kontrollera det aktuella `auto_increment`-värdet för entitetssekvenstabellen med följande fråga:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Om du kontrollerar ett automatiskt tillägg för en order i butiken med ID=1 är tabellnamnet sekvensorder_1.

Om värdet för kolumnen `auto_increment` är 1234 får nästa ordning som placeras i butiken med `ID=1` ID:t #100001234.

## Uppdatera enhet för att ändra öknings-ID

Uppdatera entiteten med följande fråga:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
>
>Viktigt: Det nya ökningsvärdet måste vara större än det aktuella.

När följande fråga har körts:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

Nästa order som placeras i butiken med `ID=1` får ID:t #100002000.

## Ytterligare rekommenderade steg i molnproduktionsmiljöer

Innan vi kör `ALTER TABLE`-frågan på en produktionsmiljö i Adobe Commerce i molninfrastrukturen rekommenderar vi att du utför följande steg:

- Testa hela proceduren för att ändra tilläggs-ID i mellanlagringsmiljön
- [Skapa en DB-säkerhetskopia] för att återställa din Production DB om fel uppstår

<!-- Link Definitions -->

[PayPal gateway rejected request - duplicate invoice issue]: https://support.magento.com/hc/en-us/articles/115002457473
[Skapa en DB-säkerhetskopia]: https://support.magento.com/hc/en-us/articles/360003254334
[alla versioner som stöds]
