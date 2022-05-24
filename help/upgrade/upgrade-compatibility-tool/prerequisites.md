---
title: '"[!DNL Upgrade Compatibility Tool] Förutsättningar"'
description: 'Verifiera att systemet uppfyller de krav som krävs för att köra [!DNL Upgrade Compatibility Tool] för ditt Adobe Commerce-projekt. '
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] krav

{{commerce-only}}

Minimikraven för att köra [!DNL Upgrade Compatibility Tool] är:

| **Krav** | **Begränsningar** |
|----------------|-----------------|
| PHP-version | >= 7.3 |
| Disposition | ingen |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`, eller `>=16.0.0`) |
| Minnesbegränsningar | Minst 2 GB RAM |
| Adobe Commerce Access-tangenter | ingen |
| Adobe Commerce | ingen |

Du kan köra [!DNL Upgrade Compatibility Tool] i flera operativsystem (Windows stöds inte). Du behöver inte köra [!DNL Upgrade Compatibility Tool] där din Adobe Commerce-instans finns.

Det är nödvändigt för [!DNL Upgrade Compatibility Tool] för att få tillgång till källkoden för Adobe Commerce-instansen. Du kan t.ex. installera det på en server och peka det vid din Adobe Commerce-installation på en annan server. Se [installera](../upgrade-compatibility-tool/install.md) för mer information.

Om du kör [!DNL Upgrade Compatibility Tool] för en Adobe Commerce-instans med stora moduler och filer kan verktyget kräva mycket RAM-minne (minst 2 GB). Du kan använda `[=MODULE-PATH]` i ditt kommando för att ange modulens sökvägskatalog för att undvika problem på grund av en låg minnesbegränsning:

```bash
bin/uct upgrade:check <dir> -m[=MODULE-PATH]
```

Där argumenten är följande:

- `<dir>`: Adobe Commerce installationskatalog.
- `[=MODULE-PATH]`: En specifik modulsökvägskatalog.
