---
title: Skapa databasschemat
description: Följ de här stegen för att skapa en databas för din Adobe Commerce eller Magento Open Source.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
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
