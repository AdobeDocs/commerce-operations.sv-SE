---
title: Kontrollera databasstatus
description: Följ de här stegen för att kontrollera databasstatusen för Adobe Commerce eller Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 2%

---


# Kontrollera databasstatus

Innan du kör det här kommandot måste du [Skapa eller uppdatera distributionskonfigurationen](deployment.md).

## Kommandoanvändning

För att kontrollera databasens status.

```bash
bin/magento setup:db:status
```

Det här kommandot har inga argument eller alternativ.

Exempelutdata följer:

```terminal
All modules are up to date.
```

Kommandot returnerar en av följande avslutskoder:

| Avslutskod | Beskrivning | Föreslagen åtgärd |
|--------------|--------------|---------------|
| 0 | Normal | Ingen |
| 1 | Vissa moduler använder kodversioner som är nyare eller äldre än databasen | Kör [`magento setup:upgrade`](database-upgrade.md) för att uppdatera databasschemat och köra `composer update` från programmets rotkatalog för att uppdatera komponentberoenden |
| 2 | `magento setup:upgrade` krävs | [`magento setup:upgrade`](database-upgrade.md) för att uppdatera databasschemat |
