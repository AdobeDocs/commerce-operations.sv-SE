---
title: Cachelagring med lack
description: Lär dig hur cacherensning fungerar med lack och hur du använder det som en accelerator för webb-cachning för Adobe Commerce-programmet.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Cachelagring med lack

I det här avsnittet diskuteras grunderna i hur du använder Varnish som accelerator för webbcachelagring för Adobe Commerce.

## Finska renar

Enligt [lack-dokumentation](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html) är&quot;En *tömning* vad som händer när du plockar ut ett objekt från cachen och tar bort det tillsammans med dess varianter.&quot; En rensning av lack påminner om ett rensningskommando för cache (eller klicka på **Rensa Magento-cache** i Admin).

Faktum är att när du rensar, tömmer eller uppdaterar Commerce-cachen så töms även varnish.

När du har installerat och konfigurerat lack för att arbeta med Commerce kan följande åtgärder resultera i en tömning av lack:

- Underhålla en webbplats.

  Till exempel allt du gör i Admin i:

   - **LAGRAR** > **Inställningar** > **Konfiguration** > ALLMÄNT > **Allmänt**
   - **LAGRAR** > **Inställningar** > **Konfiguration** > ALLMÄNT > **Valutainställningar**
   - **LAGRAR** > **Inställningar** > **Konfiguration** > ALLMÄNT > **Lagra e-postadresser**

  När Commerce upptäcker en sådan ändring visas ett meddelande om att du behöver uppdatera cachen.

- Upprätthålla en butik (till exempel lägga till eller redigera kategorier, priser, produkter och kampanjpriser).

  Finska töms automatiskt när du utför någon av dessa åtgärder.

- Underhåll källkod.

  Du bör uppdatera cachen och även ta bort allt i katalogerna `generated/code` och `generated/metadata` regelbundet. Mer information om hur du uppdaterar cacheminnet finns i nästa avsnitt.

## Konfigurera Commerce att rensa bort lack

Commerce tömmer Varnish-värdar efter att du har konfigurerat Varnish-värdar med kommandot [`magento setup:config:set`](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset).

Du kan använda den valfria parametern `--http-cache-hosts` för att ange en kommaavgränsad lista med Varnish-värdar och avlyssningsportar. Konfigurera alla varniska värdar, oavsett om du har en eller flera. (Separera inte värdar med ett blanksteg.)

Parameterformatet måste vara `<hostname or ip>:<listen port>`, där du kan utelämna `<listen port>` om det är port 80.

Exempel:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

Du kan sedan rensa varnish-värdar när du uppdaterar Commerce-cachen (kallas även *rensning* av cachen) i Admin eller via kommandoraden.

Om du vill uppdatera cacheminnet med Admin klickar du på **[!UICONTROL SYSTEM]** > Verktyg > **Cachehantering** och sedan på **Rensa Magento-cachen** överst på sidan. (Du kan också uppdatera enskilda cachetyper.)

Om du vill uppdatera cachen med kommandoraden använder du vanligtvis kommandot [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) som [filsystemsägare](../../installation/prerequisites/file-system/overview.md).
