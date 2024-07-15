---
title: Avinstallera eller installera om Adobe Commerce
description: Följ de här stegen för att avinstallera och installera om lokala installationer av Adobe Commerce.
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Avinstallera eller installera om Adobe Commerce

Innan du använder dessa kommandon måste du [installera programmet](../tutorials/install.md).

## Uppdatera programmet

Så här uppdaterar du programmet:

* Om du installerade programmet från ett arkiv eller om du använde &#39;Composer-create-project&#39; läser du [uppgraderingshandboken](../../upgrade/overview.md).
* Om du är en medverkande utvecklare (det vill säga om du använde `git clone`) kan du läsa [Uppdatera programmet](../../upgrade/developer/git-installs.md).

## Installera om programmet

Hur du installerar om programmet från kommandoraden beror på din roll:

* Om du installerade programmet från ett arkiv eller om du använde &#39;Composer-create-project&#39; läser du [Uppdatera installationsberoenden](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* Om du är en utvecklare som bidrar (det vill säga du började använda `git clone`) kan du läsa [Uppdatera installationsberoenden](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Avinstallera programmet

Om du avinstallerar programmet tas databasen bort och återställs, distributionskonfigurationen tas bort och katalogerna under `var` rensas.

Ange följande kommando för att avinstallera programmet:

```bash
bin/magento setup:uninstall
```

Följande meddelande visas för att bekräfta att avinstallationen lyckades:

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## Behåll genererade filer som tillval

Som standard rensar `bin/magento setup:upgrade` kompilerad kod och cachen. Vanligtvis använder du `bin/magento setup:upgrade` för att uppdatera komponenter, och varje komponent kan kräva olika kompilerade klasser.

I vissa situationer (särskilt vid distribution till produktion) kanske du vill undvika att rensa kompilerad kod eftersom det kan ta en stund. (Cachen är fortfarande rensad.) Om du vill uppdatera databasschemat och data *utan att* radera kompilerad kod anger du:

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>Det valfria alternativet `--keep-generated` bör under vissa omständigheter användas av erfarna systemintegratörer *only*. Det här alternativet bör *aldrig* användas i en utvecklingsmiljö. Felaktig användning av den här valfria parametern kan orsaka fel under kodkörningen.

## Installera programmet

* [Installera med kommandoraden](../advanced.md)
