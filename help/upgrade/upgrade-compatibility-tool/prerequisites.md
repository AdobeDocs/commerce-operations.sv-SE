---
title: Krav för verktyget Kompatibilitet för uppgradering
description: 'Kontrollera att datorn uppfyller de krav som krävs för att köra verktyget för kompatibilitetsuppgradering för ditt Adobe Commerce-projekt. '
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Krav för verktyget Kompatibilitet för uppgradering

Genom att köra verktyget för uppgraderingskompatibilitet kan du identifiera vad du måste göra **före** uppgradera din Adobe Commerce-version.

Minimikraven för att köra verktyget Kompatibilitet för uppgradering är:

| **Krav** | **Begränsningar** |
|----------------|-----------------|
| PHP-version | >= 7.3 |
| Disposition | ingen |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`, eller `>=16.0.0`) |
| Minnesbegränsningar | Minst 2 GB RAM |
| Adobe Commerce Access-tangenter | ingen |
| Adobe Commerce (Open Source eller Enterprise) | ingen |

Du kan köra verktyget Kompatibilitet för uppgradering i vilket operativsystem som helst. Du behöver inte köra verktyget Kompatibilitet för uppgradering där Adobe Commerce-instansen finns.

Du måste ha tillgång till källkoden för Adobe Commerce-instansen för verktyget Kompatibilitet för uppgradering. Du kan t.ex. installera det på en server och peka det vid din Adobe Commerce-installation på en annan server. Se [installera](../upgrade-compatibility-tool/install.md) för mer information.
