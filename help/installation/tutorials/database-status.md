---
title: Kontrollera databasstatus
description: Följ de här stegen för att kontrollera statusen för din Adobe Commerce-databas.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 2%

---

# Kontrollera databasstatus

Innan du kör kommandot måste du [Skapa eller uppdatera distributionskonfigurationen](deployment.md).

## Kommandoanvändning

Kontrollera databasens status.

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
