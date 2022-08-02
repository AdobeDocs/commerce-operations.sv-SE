---
title: Cachelagring med lack
description: Lär dig hur cacherensning fungerar med lack och hur du använder det som en accelerator för webb-cachning för Adobe Commerce-programmet.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---


# Cachelagring med lack

I det här avsnittet diskuteras grunderna i hur du använder Varnish som accelerator för webbcachelagring för Adobe Commerce och Magento Open Source.

## Finska renar

Enligt [Varnish-dokumentation](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *rensa* är vad som händer när du väljer ut ett objekt från [cache](https://glossary.magento.com/cache) och ta bort det tillsammans med dess varianter.&quot; En finsk tömning liknar ett cachelagrat kommando (eller klicka på **Rensa Magento-cache** i Admin).

Faktum är att när du rensar, tömmer eller uppdaterar Commerce-cachen så töms även varnish.

När du har installerat och konfigurerat lack för att arbeta med Commerce kan följande åtgärder resultera i en tömning av lack:

- Upprätthålla [webbplats](https://glossary.magento.com/website).

   Till exempel allt du gör i Admin i:

   - **LAGRING** > **Inställningar** > **Konfiguration** > ALLMÄNT > **Allmänt**
   - **LAGRING** > **Inställningar** > **Konfiguration** > ALLMÄNT > **Valutainställningar**
   - **LAGRING** > **Inställningar** > **Konfiguration** > ALLMÄNT > **E-postadresser för butik**

   När Commerce upptäcker en sådan ändring visas ett meddelande som talar om för dig att uppdatera cachen.

- Upprätthålla en butik (till exempel lägga till eller redigera kategorier, priser, produkter och kampanjpriser).

   Finska töms automatiskt när du utför någon av dessa åtgärder.

- Underhåll källkod.

   Du bör uppdatera cacheminnet och även ta bort allt i `generated/code` och `generated/metadata` kataloger. Mer information om hur du uppdaterar cacheminnet finns i nästa avsnitt.

## Konfigurera Commerce för att rensa lack

Commerce tömmer varnish-värdar efter att du har konfigurerat varnish-värdar med [`magento setup:config:set`](https://devdocs.magento.com/guides/2.4/install-gde/install/cli/install-cli-subcommands-deployment.html) -kommando.

Du kan använda den valfria parametern `--http-cache-hosts` -parameter för att ange en kommaavgränsad lista med Varnish-värdar och avlyssningsportar. Konfigurera alla varniska värdar, oavsett om du har en eller flera. (Separera inte värdar med ett blanksteg.)

Parameterformatet måste vara `<hostname or ip>:<listen port>`där du kan utesluta `<listen port>` om det är port 80.

Exempel:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

Du kan sedan rensa varnish-värdar när du uppdaterar Commerce Cache (kallas även för *rengöring* cacheminnet) i Admin eller via kommandoraden.

Om du vill uppdatera cachen med hjälp av administratören klickar du på **[!UICONTROL SYSTEM]** > Verktyg > **Cachehantering** och sedan klicka **Rensa Magento-cache** överst på sidan. (Du kan också uppdatera enskilda cachetyper.)

Om du vill uppdatera cachen med kommandoraden använder du vanligtvis kommandot [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) kommandot som [ägare av filsystem](https://devdocs.magento.com/guides/2.4/install-gde/prereq/file-sys-perms-over.html).
