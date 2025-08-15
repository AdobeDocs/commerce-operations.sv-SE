---
title: Bästa praxis för konfiguration av orderbearbetning
description: Lär dig de bästa sätten att förbättra utcheckning och prestanda för orderbearbetning.
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Bästa praxis för konfiguration av orderbearbetning

När ordervolymen ökar på dina Commerce-sajter kan du optimera utcheckningsprestanda och orderbearbetning genom att aktivera följande alternativ för butikskonfiguration:

- **[!UICONTROL Asynchronous indexing]** - Aktivera det här alternativet för att förhindra databaslås och långsam bearbetning som kan inträffa när ett stort antal order placeras samtidigt.
- **[!UICONTROL Asynchronous email notifications]** - Aktivera det här alternativet om du vill öka utcheckningsprestanda genom att skicka utcheckning och beställa e-postmeddelanden med angivna intervall i stället för att skicka dem direkt.
- **[!UICONTROL Enable Archiving]** - Aktivera det här alternativet om du vill förbättra prestanda för beställningar, fakturor, leveranser och kreditnotor, och hålla arbetsytan fri från onödig information så att du kan fokusera på den aktuella verksamheten. Se [Aktivera arkivering](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Aktivera asynkron orderbearbetning

Vilka steg som ska aktiveras för asynkron orderbearbetning beror på distributionsläget:

- För Adobe Commerce i molninfrastruktur och lokala webbplatser i produktionsläge använder du följande Magento CLI-kommando för att aktivera asynkron indexering:

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- För Adobe Commerce lokala webbplatser i standardläge eller produktionsläge aktiverar du asynkron indexering genom att uppdatera konfigurationen för stödrasterinställningar i Admin.

  Se [Aktivera schemalagda stödrasteruppdateringar och omindexering](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

  >[!WARNING]
  >
  >Testa alltid konfigurationsändringarna i mellanlagringsmiljön innan du uppdaterar produktionsmiljön.

## Ytterligare information

- [Bästa praxis för konfiguration](../../../performance/configuration.md)
- [Allmän och avancerad konfigurationssökvägsreferens](../../../configuration/reference/config-reference-general.md)
- [Bearbetning av stora mängder order](../../../performance/high-throughput-order-processing.md)
