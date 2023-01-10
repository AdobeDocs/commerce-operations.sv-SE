---
title: "[!DNL Upgrade Compatibility Tool] krav"
description: Verifiera att systemet uppfyller de krav som krävs för att köra [!DNL Upgrade Compatibility Tool] i ett kommandoradsgränssnitt för ditt Adobe Commerce-projekt.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Adobe Commerce åtkomstnycklar

{{commerce-only}}

Du måste ha [Adobe Commerce åtkomstnycklar](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) för att ladda ned och använda [!DNL Upgrade Compatibility Tool]. Lägg till dina Adobe Commerce-nycklar i `auth.json` -fil, som finns på `~/.composer` som standard.

>[!NOTE]
>
>Kontrollera **COMPOSER_HOME** systemvariabel för att se var `auth.json` filen finns.

The **publik nyckel** motsvarar _användarnamn_ Med **privat nyckel** är _lösenord_:

## Exempel på Adobe Commerce åtkomstnycklar

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

>[!NOTE]
>
> Om du inte konfigurerar **Adobe Commerce åtkomstnycklar** kan du inte hämta [!DNL Upgrade Compatibility Tool] och `composer create-project` kommandot misslyckas.

Kör `composer install` i terminalen för att installera beroenden.

## Systemkrav

Minimikraven för att använda [!DNL Upgrade Compatibility Tool] i ett kommandoradsgränssnitt är:

| **Krav** | **Begränsningar** |
|----------------|-----------------|
| PHP-version | >= 7.3 |
| Disposition | inga kända krav. |
| Node.js | Node.js-versioner `^12.22.0`, `^14.17.0`, eller `>=16.0.0` (se [Installera Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs/)) |
| Minnesbegränsningar | Minst 2 GB RAM-minne. |

[!DNL Upgrade Compatibility Tool] kräver [PCNTL](https://www.php.net/manual/en/book.pcntl.php) och andra PHP-tillägg för körningen. Kontrollera önskade PHP-tillägg med `composer check-platform-reqs` kommando:

```bash
# Example output of `composer check-platform-reqs` command for UCT 2.2.6 and PHP 7.4:

$ composer check-platform-reqs
Checking platform requirements for packages in the vendor dir
ext-ctype     *         success provided by symfony/polyfill-ctype
ext-dom       20031129  success
ext-filter    7.4.30    success
ext-json      7.4.30    success
ext-libxml    7.4.30    success
ext-mbstring  *         success provided by symfony/polyfill-mbstring
ext-openssl   7.4.30    success
ext-pcntl     7.4.30    success
ext-pcre      7.4.30    success
ext-phar      7.4.30    success
ext-simplexml 7.4.30    success
ext-tokenizer 7.4.30    success
ext-xml       7.4.30    success
ext-xmlwriter 7.4.30    success
ext-zip       1.15.6    success
php           7.4.30    success
```

Adobe Commerce stöds bara på Linux-operativsystem. Du kan köra [!DNL Upgrade Compatibility Tool] i ett Linux-operativsystem. Du behöver inte köra [!DNL Upgrade Compatibility Tool] där din Adobe Commerce-instans finns.

Det är nödvändigt för [!DNL Upgrade Compatibility Tool] för att få tillgång till källkoden för Adobe Commerce-instansen. Du kan t.ex. installera det på en server och peka det vid din Adobe Commerce-installation på en annan server.

Om du kör [!DNL Upgrade Compatibility Tool] för en Adobe Commerce-instans med stora moduler och filer kan verktyget kräva mycket RAM-minne (minst 2 GB).
