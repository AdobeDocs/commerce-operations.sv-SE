---
title: '"[!DNL Upgrade Compatibility Tool] krav"'
description: 'Verifiera att systemet uppfyller de krav som krävs för att köra [!DNL Upgrade Compatibility Tool] för ditt Adobe Commerce-projekt. '
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---


# Systemkrav

{{commerce-only}}

Minimikraven för att använda [!DNL Upgrade Compatibility Tool] är:

| **Krav** | **Begränsningar** |
|----------------|-----------------|
| PHP-version | >= 7.3 |
| Disposition | inget känt krav |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`, eller `>=16.0.0`) |
| Minnesbegränsningar | Minst 2 GB RAM |

Du kan köra [!DNL Upgrade Compatibility Tool] i flera operativsystem (Windows stöds inte). Du behöver inte köra [!DNL Upgrade Compatibility Tool] där din Adobe Commerce-instans finns.

Det är nödvändigt för [!DNL Upgrade Compatibility Tool] för att få tillgång till källkoden för Adobe Commerce-instansen. Du kan t.ex. installera det på en server och peka det vid din Adobe Commerce-installation på en annan server.

Om du kör [!DNL Upgrade Compatibility Tool] för en Adobe Commerce-instans med stora moduler och filer kan verktyget kräva mycket RAM-minne (minst 2 GB).

## Adobe Commerce åtkomstnycklar

Du måste ha [Adobe Commerce åtkomstnycklar](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) för att ladda ned och använda [!DNL Upgrade Compatibility Tool]. Lägg till dina Adobe Commerce-nycklar i `auth.json` -fil, som finns på `~/.composer` som standard.

>[!WARNING]
>
>Kontrollera **COMPOSER_HOME** systemvariabel för att se var `auth.json` filen finns.

The **publik nyckel** motsvarar _användarnamn_ Med **privat nyckel** är _lösenord_:

### Exempel på Adobe Commerce åtkomstnycklar

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

## Disposition

Ladda ned [!DNL Upgrade Compatibility Tool] databas och köra `composer install` i terminalen för att installera beroenden.

>[!NOTE]
>
> Om du inte konfigurerar **Adobe Commerce åtkomstnycklar** kan du inte hämta [!DNL Upgrade Compatibility Tool]. Kör `composer create-project` kommandot misslyckas.

## Node.js

Mer information om hur du installerar Node.js finns i Node.js [dokumentation](https://nodejs.dev/learn/how-to-install-nodejs).

## Tredjepartstillägg

Adobe rekommenderar att du kontaktar din tilläggsleverantör för att avgöra om tillägget är helt kompatibelt med den senaste versionen av Adobe Commerce.
