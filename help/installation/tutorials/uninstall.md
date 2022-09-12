---
title: Avinstallera eller installera om Adobe Commerce
description: Följ de här stegen för att avinstallera och installera om lokala installationer av Adobe Commerce och Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# Avinstallera eller installera om Adobe Commerce

Innan du använder dessa kommandon måste du [installera programmet](../tutorials/install.md).

## Uppdatera programmet

Så här uppdaterar du programmet:

* Om du har installerat programmet från ett arkiv eller om du använde &#39;Composer-create-project&#39; läser du [Uppgraderingshandbok](../../upgrade/overview.md).
* Om du är en bidragsgivare (dvs. du använde `git clone`), se [Uppdatera programmet](../../upgrade/developer/git-installs.md).

## Installera om programmet

Hur du installerar om programmet från kommandoraden beror på din roll:

* Om du har installerat programmet från ett arkiv eller om du använde &#39;Composer-create-project&#39; läser du [Uppdatera installationsberoenden](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* Om du är en bidragsgivare (d.v.s. har du börjat använda `git clone`), se [Uppdatera installationsberoenden](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Avinstallera programmet

Om programmet avinstalleras, tas databasen bort och återställs, distributionskonfigurationen tas bort och katalogerna rensas under `var`.

Ange följande kommando för att avinstallera programmet:

```bash
bin/magento setup:uninstall
```

Följande meddelande visas för att bekräfta att avinstallationen lyckades:

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## Spara genererade filer som ett alternativ

Som standard `bin/magento setup:upgrade` rensar kompilerad kod och cachen. Vanligtvis använder du `bin/magento setup:upgrade` för att uppdatera komponenter och varje komponent kan kräva olika kompilerade klasser.

I vissa situationer (särskilt vid distribution till produktion) kanske du vill undvika att rensa kompilerad kod eftersom det kan ta en stund. (Med [cache](https://glossary.magento.com/cache) är fortfarande rensad.) Så här uppdaterar du [databasschema](https://glossary.magento.com/database-schema) och data *utan* rensa kompilerad kod, ange:

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>Valfritt `--keep-generated` bör under vissa omständigheter användas av erfarna systemintegratörer *endast*. Det här alternativet bör *aldrig* användas i en utvecklingsmiljö. Felaktig användning av den här valfria parametern kan orsaka fel under kodkörningen.

## Installera programmet

* [Installera med kommandoraden](../advanced.md)
