---
title: Hämta exempeldatapaket för disposition
description: Följ de här stegen för att installera exempeldata för Adobe Commerce och Magento Open Source med Composer PHP Package Manager.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Hämta exempeldatapaket för disposition

I det här avsnittet beskrivs hur du installerar exempeldata om du har Adobe Commerce eller Magento Open Source på något av följande sätt:

* Hämtade ett komprimerat arkiv från `https://magento.com/tech-resources/download`.

  Om du hämtade ett arkiv från GitHub fungerar inte den här metoden eftersom `composer.json` filen innehåller inte `repo.magento.com` URL.

* Används `composer create-project`

Du kan använda den här metoden för att hämta exempeldata för både Adobe Commerce och Magento Open Source, men du måste använda samma [autentiseringsnycklar](../prerequisites/authentication-keys.md) som du använde för att installera programmet.

>[!NOTE]
>
>Om du stöter på fel, till exempel `Could not find package...` eller `...no matching package found...`Kontrollera att det inte finns några stavfel i kommandot. Om du fortfarande råkar ut för fel kanske du inte har tillgång till rätt Composer-databaser, särskilt om du använder Adobe Commerce. Kontakt [Adobe Commerce Support](https://support.magento.com/hc/en-us) om du behöver hjälp.

Du kan använda Composer för att installera exempeldata antingen före eller efter installationen av programmet, men det kan finnas [ytterligare uppgifter](remove-or-update.md).

Om du är en bidragsgivare kan du läsa [Installera genom att klona databaser](git-repositories.md).

>[!WARNING]
>
>Installera inte exempeldata om programmet är inställt för [produktionsläge](../../configuration/bootstrap/application-modes.md#production-mode). Växla till [utvecklarläge](../../configuration/bootstrap/application-modes.md#developer-mode) först. Installera exempeldata i produktionsläge [misslyckas](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Om du vill installera exempeldata via kommandoraden anger du följande kommando som filsystemsägare i `<app_root>` katalog:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Om du installerar exempeldata _efter_ måste du också köra följande kommando för att uppdatera databasen och schemat i `<app_root>` katalog:

```bash
bin/magento setup:upgrade
```

Du måste [autentisera](../prerequisites/authentication-keys.md) för att slutföra åtgärden.

## Autentiseringsfel

Följande autentiseringsfel kan visas:

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Om felet visas byter du till programinstallationskatalogen och kör `composer update`, som ber dig att [autentiseringsnycklar](../prerequisites/authentication-keys.md).

## Slutför installationen av exempeldata

{{$include /help/_includes/sample-data-complete.md}}
