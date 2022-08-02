---
title: Verifiera delad databas
description: Lär dig hur du kontrollerar att en konfiguration för en delad databas i Commerce fungerar som den ska.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---


# Verifiera delad databas

{#ee-only}

{{deprecate-split-db}}

Efter konfigurationen konfigureras de överordnad databaserna enligt följande:

- Main Commerce database: 369 tabeller
- Handel [citat](https://glossary.magento.com/quote) databas: 11 tabeller
- Försäljningsdatabas: 55 tabeller

För att verifiera att de delade databaserna fungerar som de ska utför du följande åtgärder och kontrollerar att data har lagts till i databastabellerna med hjälp av ett databasverktyg som [phpmyadmin](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/optional.html#install-optional-phpmyadmin):

| Verifiera | Verifiera |
| -------------- | ------------- |
| offertdatabasen fungerar | Lägg artiklar i en kundvagn. Verifiera att rader har lagts till i offertdatabasens `quote`, `quote_address`och `quote_item` tabeller. |
| försäljningsdatabasen fungerar | Slutför en beställning (alla betalningsmetoder, inklusive check-/penningorder). Verifiera att rader har lagts till i försäljningsdatabasens `sales_order_address`, `sales_order_item`och `sales_order_payment` tabeller. |

>[!WARNING]
>
>Du måste säkerhetskopiera de två ytterligare databasinstanserna manuellt. Endast huvuddatabasinstansen säkerhetskopieras. The [`magento setup:backup --db`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html) kommando- och administratörsalternativen säkerhetskopierar inte de ytterligare tabellerna.
