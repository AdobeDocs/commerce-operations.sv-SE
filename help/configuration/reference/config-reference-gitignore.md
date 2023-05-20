---
title: .gitignore-referens
description: Se hur du lägger till en fil som ingår i ignoreringslistan.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 0%

---

# .gitignore-referens

Magento Open Source har en bas `.gitignore` -fil. Se [den senaste handeln `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) -fil. Om du måste lägga till en fil som finns i `.gitignore` kan du använda `-f` (force) när en implementering mellanlagras:

```bash
git add <path/filename> -f
```
