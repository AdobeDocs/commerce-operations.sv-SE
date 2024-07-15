---
title: Skapa databasschemat
description: Följ de här stegen för att skapa en databas för ditt Adobe Commerce-projekt.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Skapa databasschemat

Innan du kör det här kommandot måste du [skapa eller uppdatera distributionskonfigurationen](deployment.md).

## Konfigurera databasen och lägga till data

Kommandoanvändning:

```bash
bin/magento setup:db-schema:upgrade
```

Om du vill se databasens status anger du

```bash
bin/magento setup:db:status
```
