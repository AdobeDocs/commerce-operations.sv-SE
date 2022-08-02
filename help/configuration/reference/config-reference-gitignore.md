---
title: .gitignore-referens
description: Se hur du lägger till en fil som ingår i ignoreringslistan.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 0%

---


# .gitignore-referens

Magento Open Source har en bas `.gitignore` -fil. Se [den senaste handeln `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) -fil. Om du måste lägga till en fil som finns i `.gitignore` kan du använda `-f` (force) när en implementering mellanlagras:

```bash
git add <path/filename> -f
```
