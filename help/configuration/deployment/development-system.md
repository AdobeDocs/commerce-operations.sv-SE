---
title: Installation av utvecklingssystem
description: Lär dig hur du konfigurerar ett utvecklingssystem för Commerce-programmet.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# Installation av utvecklingssystem

Du kan ha ett valfritt antal utvecklingssystem, förutsatt att följande stämmer för alla:

- Alla kör Commerce 2.2 eller senare
- All Commerce-kod styrs av källan i samma databas som bygg- och produktionssystemen
- Varje utvecklingssystem ska antingen använda [standardläge](../bootstrap/application-modes.md#default-mode) eller [utvecklarläge](../bootstrap/application-modes.md#developer-mode)
- Den har ägarskap och behörigheter för filsystemet inställda enligt beskrivningen i [Krav för ditt utvecklings-, bygg- och produktionssystem](../deployment/technical-details.md).
- Kontrollera att alla följande är _exkluderade_ från källkontrollen:

   - `vendor`-katalog (och underkataloger)
   - `generated`-katalog (och underkataloger)
   - `pub/static`-katalog (och underkataloger)
   - `app/etc/env.php` fil

- Kontrollera att `app/etc/config.php` är _inkluderad_ i källkontrollen

Om du använder Git innehåller filen `.gitignore` det mesta av det föregående. Se [`.gitignore`-referensen](../reference/config-reference-gitignore.md).
