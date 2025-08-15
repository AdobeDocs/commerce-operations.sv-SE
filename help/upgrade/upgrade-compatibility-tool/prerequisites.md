---
title: Krav för [!DNL Upgrade Compatibility Tool]
description: Kontrollera att datorn uppfyller de krav som krävs för att köra  [!DNL Upgrade Compatibility Tool]  i ett kommandoradsgränssnitt för ditt Adobe Commerce-projekt.
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Adobe Commerce åtkomstnycklar

{{commerce-only}}

Du måste ha [Adobe Commerce-nycklar](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) för att kunna hämta och använda [!DNL Upgrade Compatibility Tool]. Lägg till dina Adobe Commerce-nycklar i din `auth.json`-fil, som finns på `~/.composer` som standard.

>[!NOTE]
>
>Kontrollera miljövariabeln **COMPOSER_HOME** för att se var `auth.json`-filen finns.

Den **publika nyckeln** motsvarar _användarnamnet_ medan den **privata nyckeln** är _lösenordet_:

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
> Om du inte konfigurerar dina **Adobe Commerce-nycklar** korrekt kan du inte hämta [!DNL Upgrade Compatibility Tool] och kommandot `composer create-project` misslyckas.

Kör `composer install` i terminalen för att installera beroenden.

## Systemkrav

Minimikraven för att använda [!DNL Upgrade Compatibility Tool] i ett kommandoradsgränssnitt är:

| **Krav** | **Begränsningar** |
|----------------|-----------------|
| PHP version | >= 7.3 |
| Disposition | inga kända krav. |
| Node.js | Node.js-versionerna `^12.22.0`, `^14.17.0` eller `>=16.0.0` (se [Installera Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)) |
| Minnesbegränsningar | Minst 2 GB RAM. |

[!DNL Upgrade Compatibility Tool] kräver [PCNTL](https://www.php.net/manual/en/book.pcntl.php) och andra PHP-tillägg för körningen. Kontrollera önskade PHP-tillägg med kommandot `composer check-platform-reqs`:

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

Adobe Commerce stöds bara på Linux-operativsystem. Du kan köra [!DNL Upgrade Compatibility Tool] i ett Linux OS. Du behöver inte köra [!DNL Upgrade Compatibility Tool] där din Adobe Commerce-instans finns.

[!DNL Upgrade Compatibility Tool] måste ha åtkomst till källkoden för Adobe Commerce-instansen. Du kan t.ex. installera det på en server och peka det vid din Adobe Commerce-installation på en annan server.

Om du kör [!DNL Upgrade Compatibility Tool] mot en Adobe Commerce-instans med stora moduler och filer kan verktyget kräva mycket RAM-minne (minst 2 GB).

Kör [!DNL Upgrade Compatibility Tool] från [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) för [Adobe Commerce i molninfrastrukturprojekt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank}.
