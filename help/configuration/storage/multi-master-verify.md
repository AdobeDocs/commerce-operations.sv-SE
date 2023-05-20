---
title: Verifiera delad databas
description: Lär dig hur du kontrollerar att en konfiguration för en delad databas i Commerce fungerar som den ska.
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Verifiera delad databas

{{ee-only}}

{{deprecate-split-db}}

Efter konfigurationen konfigureras de överordnad databaserna enligt följande:

- Main Commerce database: 369 tabeller
- Databas för handelsoffert: 11 tabeller
- Försäljningsdatabas: 55 tabeller

För att verifiera att de delade databaserna fungerar som de ska utför du följande åtgärder och kontrollerar att data har lagts till i databastabellerna med hjälp av ett databasverktyg som [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| Verifiera | Verifiera |
| -------------- | ------------- |
| offertdatabasen fungerar | Lägg artiklar i en kundvagn. Verifiera att rader har lagts till i offertdatabasens `quote`, `quote_address`och `quote_item` tabeller. |
| försäljningsdatabasen fungerar | Slutför en beställning (alla betalningsmetoder, inklusive check-/penningorder). Verifiera att rader har lagts till i försäljningsdatabasens `sales_order_address`, `sales_order_item`och `sales_order_payment` tabeller. |

>[!WARNING]
>
>Du måste säkerhetskopiera de två ytterligare databasinstanserna manuellt. Endast huvuddatabasinstansen säkerhetskopieras. The [`magento setup:backup --db`](../../installation/tutorials/backup.md) kommando- och administratörsalternativen säkerhetskopierar inte de ytterligare tabellerna.
