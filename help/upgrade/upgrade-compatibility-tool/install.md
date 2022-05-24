---
title: Ladda ned [!DNL Upgrade Compatibility Tool]
description: Följ de här stegen för att hämta [!DNL Upgrade Compatibility Tool] för ditt Adobe Commerce-projekt.
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---


# Installera [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

The [!DNL Upgrade Compatibility Tool] är ett kommandoradsverktyg som kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla installerade moduler. Den returnerar en lista med fel och varningar som måste åtgärdas innan du uppgraderar till den senaste versionen av Adobe Commerce.

## Förutsättningar

Så här installerar du [!DNL Upgrade Compatibility Tool]måste du installera de nödvändiga förutsättningarna.

Se [krav](../upgrade-compatibility-tool/prerequisites.md) för mer information.

## Ladda ned [!DNL Upgrade Compatibility Tool]

Ladda ned [!DNL Upgrade Compatibility Tool]kör du följande kommando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Adobe Commerce åtkomstnycklar

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

### Disposition

Ladda ned [!DNL Upgrade Compatibility Tool] databas och köra `composer install` i terminalen för att installera beroenden.

>[!WARNING]
>
>Om **Adobe Commerce åtkomstnycklar** är inte korrekt konfigurerade kan du inte hämta [!DNL Upgrade Compatibility Tool] och när du kör `composer create-project` kommer det att misslyckas.

### Node.js

Mer information om hur du installerar Node.js finns i Node.js [dokumentation](https://nodejs.dev/learn/how-to-install-nodejs).

## Tredjepartstillägg

Adobe rekommenderar att du kontaktar din tilläggsleverantör för att avgöra om tillägget är helt kompatibelt med den senaste versionen från Adobe Commerce.

Se [Kör verktyget](../upgrade-compatibility-tool/run.md) för information om hur du kör [!DNL Upgrade Compatibility Tool].
