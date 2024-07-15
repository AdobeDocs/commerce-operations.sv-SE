---
title: .gitignore-referens
description: Se hur du lägger till en fil som ingår i ignoreringslistan.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '51'
ht-degree: 0%

---

# .gitignore-referens

Magento Open Source innehåller en `.gitignore`-basfil. Se [den senaste Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore)-filen. Om du måste lägga till en fil som finns i listan `.gitignore` kan du använda alternativet `-f` (force) när du mellanlagrar en implementering:

```bash
git add <path/filename> -f
```
