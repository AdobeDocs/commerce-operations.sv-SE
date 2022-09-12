---
title: Ändra öknings-ID
description: Ändra ID för ökning för en Commerce-databasenhet.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# Ändra öknings-ID

I den här artikeln beskrivs hur du ändrar tilläggs-ID för en enhet i en Commerce-databas (DB) (order, faktura, kreditnota o.s.v.) i en viss Commerce-butik med hjälp av `ALTER TABLE` SQL-sats.

## Berörda versioner

- Adobe Commerce (lokalt): 2.x.x
- Adobe Commerce om molninfrastruktur: 2.x.x
- MySQL: [alla versioner som stöds](../../installation/prerequisites/database/mysql.md)

## När behöver du ändra ID för ökning

Du kan behöva ändra ID:t för ökning för nya DB-entiteter i följande fall:

- Efter en återställning av en hård säkerhetskopiering på en Live-webbplats
- Vissa orderposter har gått förlorade, men deras ID används redan av betalningsgateways (som PayPal) för ditt aktuella Merchant-konto. Så är fallet, så upphör betalningsgatewayen att bearbeta nya order som har samma ID, vilket returnerar felet &quot;Duplicera faktura-ID&quot;

>[!INFO]
>
>Du kan också åtgärda problemet med betalningsgateway för PayPal genom att tillåta flera betalningar per faktura-ID i PayPals Inställningar för betalningsmottagning. Se [PayPal-gateway avvisade begäran - dubblettfakturautleverans] i _Knowledge Base_.

## Nödvändiga steg

1. Sök efter butiker och enheter som det nya tilläggs-ID:t ska ändras för.
1. Anslut till MySQL-databasen.
För Adobe Commerce i molninfrastruktur måste du först ansluta med SSH till din miljö.
1. Kontrollera aktuell `auto_increment` värde för entitetssekvensregistret med följande fråga:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Om du kontrollerar ett automatiskt tillägg för en order i butiken med ID=1 är tabellnamnet sekvensorder_1.

Om värdet för `auto_increment` kolumnen är &#39;1234&#39;, nästa order som läggs i butiken med `ID=1` har ID &#39;#100001234&#39;.

## Uppdatera enhet för att ändra öknings-ID

Uppdatera entiteten med följande fråga:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
Viktigt: Det nya ökningsvärdet måste vara större än det aktuella.

När följande fråga har körts:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

Nästa beställning som läggs i butiken med `ID=1` kommer att ha ID &#39;#100002000&#39;.

## Ytterligare rekommenderade steg i molnproduktionsmiljöer

Innan du kör `ALTER TABLE` fråga om en produktionsmiljö i Adobe Commerce om molninfrastruktur rekommenderar vi att du utför följande steg:

- Testa hela proceduren för att ändra tilläggs-ID i mellanlagringsmiljön
- [Skapa en DB-säkerhetskopia] för att återställa produktionsdatabasen om fel uppstår

<!-- Link Definitions -->

[PayPal-gateway avvisade begäran - dubblettfakturautleverans]: https://support.magento.com/hc/en-us/articles/115002457473
[Skapa en DB-säkerhetskopia]: https://support.magento.com/hc/en-us/articles/360003254334
[alla versioner som stöds]
