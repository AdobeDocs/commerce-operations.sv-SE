---
title: Installera [!DNL Upgrade Compatibility Tool]
description: Följ de här stegen för att installera [!DNL Upgrade Compatibility Tool] för ditt Adobe Commerce-projekt.
source-git-commit: 218b099caa883f66ddda48407fb789e51fedc203
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Installera [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

The [!DNL Upgrade Compatibility Tool] är ett kommandoradsverktyg som kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla installerade moduler. Den returnerar en lista med fel och varningar som måste åtgärdas innan du uppgraderar till den senaste versionen av Adobe Commerce.

## Ladda ned [!DNL Upgrade Compatibility Tool]

Ladda ned [!DNL Upgrade Compatibility Tool]kör du följande kommando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Installera

Så här installerar du [!DNL Upgrade Compatibility Tool]måste du installera de nödvändiga kraven:

* Adobe Commerce åtkomstnycklar
* Disposition
* Node.js

## Förutsättningar

Se [krav](../upgrade-compatibility-tool/prerequisites.md) för mer information.

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

Klona [!DNL Upgrade Compatibility Tool] databas och köra `composer install` i terminalen för att installera beroenden.

>[!WARNING]
>
>Om **Adobe Commerce åtkomstnycklar** är inte korrekt konfigurerade, [!DNL Upgrade Compatibility Tool] installeras inte och du får felmeddelanden när du kör `composer install` -kommando.

### Node.js

Mer information om hur du installerar Node.js finns i Node.js [dokumentation](https://nodejs.dev/learn/how-to-install-nodejs).

## Tredjepartstillägg

Adobe rekommenderar att du kontaktar din tilläggsleverantör för att avgöra om tillägget är helt kompatibelt med den senaste versionen från Adobe Commerce.

Se [Kör verktyget](../upgrade-compatibility-tool/run.md) för information om hur du kör [!DNL Upgrade Compatibility Tool].
