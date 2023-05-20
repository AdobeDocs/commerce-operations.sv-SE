---
title: Konfigurera meddelandeanvändare
description: Följ de här stegen för att konfigurera beteendet för användare av Adobe Commerce- eller Magento Open Source-meddelandekön.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---

# Konfigurera meddelandeanvändare

Innan du kör det här kommandot måste du göra följande *eller* du måste [installera programmet](../advanced.md):

* [Skapa eller uppdatera distributionskonfigurationen](deployment.md)
* [Skapa databasschemat](database.md)

## Konfigurera konsumentbeteendet

Konsument-beteendet konfigureras genom att nyckelpar/värdepar skickas i inställningsfunktionen:

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeskrivningar

{{$include /help/_includes/cli-consumers.md}}
