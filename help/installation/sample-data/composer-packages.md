---
title: Hämta exempeldatapaket för disposition
description: Följ de här stegen för att installera exempeldata för Adobe Commerce med Composer PHP Package Manager.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Hämta exempeldatapaket för disposition

I det här avsnittet beskrivs hur du installerar exempeldata om du har Adobe Commerce på något av följande sätt:

* Hämtade ett komprimerat arkiv från `https://magento.com/tech-resources/download`.

  Om du hämtade ett arkiv från GitHub fungerar inte den här metoden eftersom `composer.json`-filen inte innehåller URL:en för `repo.magento.com`.

* Använt `composer create-project`

Du kan använda den här metoden för att hämta exempeldata för Adobe Commerce, men du måste använda samma [autentiseringsnycklar](../prerequisites/authentication-keys.md) som du använde för att installera programmet.

>[!NOTE]
>
>Om du stöter på fel, till exempel `Could not find package...` eller `...no matching package found...`, kontrollerar du att det inte finns några stavfel i kommandot. Om du fortfarande råkar ut för fel kanske du inte har tillgång till rätt Composer-databaser, särskilt om du använder Adobe Commerce. Kontakta [Adobe Commerce Support](https://support.magento.com/hc/en-us) om du behöver hjälp.

Du kan använda Composer för att installera exempeldata antingen före eller efter installationen av programmet, men det kan finnas [ytterligare uppgifter](remove-or-update.md).

Om du är en utvecklare som bidrar läser du [Installera genom att klona databaser](git-repositories.md).

>[!WARNING]
>
>Installera inte exempeldata om programmet är inställt för [produktionsläge](../../configuration/bootstrap/application-modes.md#production-mode). Växla till [utvecklarläge](../../configuration/bootstrap/application-modes.md#developer-mode) först. Det gick inte att installera exempeldata i produktionsläget [&#128279;](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Om du vill installera exempeldata med kommandoraden anger du följande kommando som filsystemsägare i katalogen `<app_root>`:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Om du installerar exempeldata _efter_-installationen av programmet måste du också köra följande kommando för att uppdatera databasen och schemat i katalogen `<app_root>`:

```bash
bin/magento setup:upgrade
```

Du måste [autentisera](../prerequisites/authentication-keys.md) för att slutföra åtgärden.

## Autentiseringsfel

Följande autentiseringsfel kan visas:

```
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Om felet visas ändrar du till programinstallationskatalogen och kör `composer update`, som ber dig ange [autentiseringsnycklar](../prerequisites/authentication-keys.md).

## Slutför installationen av exempeldata

{{$include /help/_includes/sample-data-complete.md}}

<!-- Last updated from includes: 2022-09-08 11:33:05 -->
