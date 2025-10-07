---
title: .gitignore-referens
description: Lär dig hur du lägger till filer i .gitignore-listan för Adobe Commerce-projekt. Upptäck de bästa sätten att hantera versionskontroll och exkludera filer.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---

# .gitignore-referens

Magento Open Source innehåller en `.gitignore`-basfil. Se [den senaste Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore)-filen. Om du måste lägga till en fil som finns i listan `.gitignore` kan du använda alternativet `-f` (force) när du mellanlagrar en implementering:

```bash
git add <path/filename> -f
```
