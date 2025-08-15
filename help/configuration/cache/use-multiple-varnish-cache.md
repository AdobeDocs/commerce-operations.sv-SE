---
title: Cachelagring med flera varianter
description: Lär dig hur cache-rensning fungerar med flera varianter.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 1%

---

# Cachelagra flera varianter

Adobe Commerce har stöd för flera varnish-instanser direkt.

I det här avsnittet beskrivs grunderna för hur du konfigurerar flera Varnish-instanser med Commerce.

## Konfiguration för att rensa flera Varnish-instanser

Commerce tömmer Varnish-värdar efter att du har konfigurerat Varnish-värdar med kommandot [`magento setup:config:set`](../../installation/tutorials/deployment.md).

Du bör använda parametern `--http-cache-hosts` för att ange en kommaavgränsad lista med varnish-värdar och avlyssningsportar. (Separera inte värdar med ett blanksteg.)

Parameterformatet måste vara `<hostname or ip>:<listen port>`, där du kan utelämna `<listen port>` om det är port 80.

Exempel:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Du kan sedan rensa alla lack-värdar när du uppdaterar Commerce-cachen (kallas även _rensning_ av cachen) i Admin eller via kommandoraden.

Om du vill uppdatera cacheminnet med Admin klickar du på **SYSTEM** > Verktyg > **Cachehantering** och sedan på **Rensa Magento-cacheminnet** överst på sidan. (Du kan också uppdatera enskilda cachetyper.)

Om du vill uppdatera cachen för flera Varnish-instanser från klippet använder du kommandot [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) som [filsystemsägare](../../installation/prerequisites/file-system/overview.md).
