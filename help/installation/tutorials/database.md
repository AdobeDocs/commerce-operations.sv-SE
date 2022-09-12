---
title: Skapa databasschemat
description: Följ de här stegen för att skapa en databas för din Adobe Commerce eller Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# Skapa databasschemat

Innan du kör det här kommandot måste du [Skapa eller uppdatera distributionskonfigurationen](deployment.md).

## Konfigurera databasen och lägga till data

Kommandoanvändning:

```bash
bin/magento setup:db-schema:upgrade
```

Om du vill se databasens status anger du

```bash
bin/magento setup:db:status
```
