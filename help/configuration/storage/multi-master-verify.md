---
title: Verifiera delad databas
description: Lär dig hur du kontrollerar att en Commerce-delad databaskonfiguration fungerar som den ska.
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Verifiera delad databas

{{ee-only}}

{{deprecate-split-db}}

Efter konfigurationen konfigureras huvuddatabaserna enligt följande:

- Commerce huvuddatabas: 369 tabeller
- Commerce offertdatabas: 11 tabeller
- Commerce säljdatabas: 55 tabeller

Verifiera att de delade databaserna fungerar som de ska genom att utföra följande åtgärder och verifiera att data har lagts till i databastabellerna med ett databasverktyg som [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| Verifiera | Verifiera |
| -------------- | ------------- |
| offertdatabasen fungerar | Lägg artiklar i en kundvagn. Kontrollera att rader har lagts till i offertdatabasens `quote`-, `quote_address`- och `quote_item`-tabeller. |
| försäljningsdatabasen fungerar | Slutför en beställning (alla betalningsmetoder, inklusive check-/penningorder). Kontrollera att rader har lagts till i försäljningsdatabasens tabeller `sales_order_address`, `sales_order_item` och `sales_order_payment`. |

>[!WARNING]
>
>Du måste säkerhetskopiera de två ytterligare databasinstanserna manuellt. Commerce säkerhetskopierar bara huvuddatabasinstansen. Kommandot [`magento setup:backup --db`](../../installation/tutorials/backup.md) och administratörsalternativen säkerhetskopierar inte de ytterligare tabellerna.
