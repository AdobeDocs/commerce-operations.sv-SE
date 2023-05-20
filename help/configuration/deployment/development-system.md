---
title: Installation av utvecklingssystem
description: Lär dig hur du konfigurerar ett utvecklingssystem för Commerce-programmet.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Installation av utvecklingssystem

Du kan ha ett valfritt antal utvecklingssystem, förutsatt att följande stämmer för alla:

- Alla använder Commerce 2.2 eller senare
- All Commerce-kod står under källkontroll i samma databas som bygg- och produktionssystemen
- Varje utvecklingssystem bör använda antingen [standardläge](../bootstrap/application-modes.md#default-mode) eller [utvecklarläge](../bootstrap/application-modes.md#developer-mode)
- Ägarskap och behörigheter för filsystemet anges enligt [Krav för dina utvecklings-, bygg- och produktionssystem](../deployment/technical-details.md).
- Se till att alla följande är _exkluderad_ från källkontroll:

   - `vendor` katalog (och underkataloger)
   - `generated` katalog (och underkataloger)
   - `pub/static` katalog (och underkataloger)
   - `app/etc/env.php` fil

- Se till att `app/etc/config.php` är _ingår_ in source control

Om du använder Git `.gitignore` filen innehåller det mesta av föregående. Se [`.gitignore` referens](../reference/config-reference-gitignore.md).
