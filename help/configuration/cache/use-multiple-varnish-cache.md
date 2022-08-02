---
title: Cachelagring med flera varianter
description: Lär dig hur cache-rensning fungerar med flera varianter.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 1%

---


# Cachelagra flera varianter

Adobe Commerce och Magento Open Source har stöd för flera Varnish-instanser.

I det här avsnittet beskrivs grunderna för hur du konfigurerar flera Varnish-instanser med Commerce.

## Konfiguration för att rensa flera Varnish-instanser

Commerce tömmer varnish-värdar efter att du har konfigurerat varnish-värdar med [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-deployment.html) -kommando.

Du bör använda `--http-cache-hosts` -parameter för att ange en kommaavgränsad lista med Varnish-värdar och avlyssningsportar. (Separera inte värdar med ett blanksteg.)

Parameterformatet måste vara `<hostname or ip>:<listen port>`där du kan utesluta `<listen port>` om det är port 80.

Exempel:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Du kan sedan rensa alla varnish-värdar när du uppdaterar Commerce-cachen (kallas även för _rengöring_ cacheminnet) i Admin eller via kommandoraden.

Om du vill uppdatera cachen med hjälp av administratören klickar du på **SYSTEM** > Verktyg > **Cachehantering** och sedan klicka **Rensa Magento-cache** överst på sidan. (Du kan också uppdatera enskilda cachetyper.)

Använd kommandot [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) kommandot som [ägare av filsystem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
