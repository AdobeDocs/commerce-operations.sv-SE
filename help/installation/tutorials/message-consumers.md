---
title: Konfigurera meddelandeanvändare
description: Följ de här stegen för att konfigurera beteendet för användare av Adobe Commerce meddelandekö.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# Konfigurera meddelandeanvändare

Innan du kör det här kommandot måste du göra följande *eller* måste du [installera programmet](../advanced.md):

* [Skapa eller uppdatera distributionskonfigurationen](deployment.md)
* [Skapa databasschemat](database.md)

## Konfigurera konsumentbeteendet

Konsument-beteendet konfigureras genom att nyckelpar/värdepar skickas i inställningsfunktionen:

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeskrivningar

{{$include /help/_includes/cli-consumers.md}}
