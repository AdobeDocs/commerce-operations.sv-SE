---
title: Kontrollera databasstatus
description: Följ de här stegen för att kontrollera statusen för din Adobe Commerce-databas.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 2%

---

# Kontrollera databasstatus

Innan du kör det här kommandot måste du [skapa eller uppdatera distributionskonfigurationen](deployment.md).

## Kommandoanvändning

Kontrollera databasens status.

```bash
bin/magento setup:db:status
```

Det här kommandot har inga argument eller alternativ.

Exempelutdata följer:

```
All modules are up to date.
```

Kommandot returnerar en av följande avslutskoder:

| Avslutskod | Beskrivning | Föreslagen åtgärd |
|--------------|--------------|---------------|
| 0 | Normal | Ingen |
| 1 | Vissa moduler använder kodversioner som är nyare eller äldre än databasen | Kör [`magento setup:upgrade`](database-upgrade.md) för att uppdatera databasschemat och kör `composer update` från programmets rotkatalog för att uppdatera komponentberoenden |
| 2 | `magento setup:upgrade` krävs | [`magento setup:upgrade`](database-upgrade.md) för att uppdatera databasschemat |
