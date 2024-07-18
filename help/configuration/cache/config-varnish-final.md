---
title: Slutlig verifiering
description: Kontrollera att din lack-konfiguration är korrekt konfigurerad för att fungera med Adobe Commerce-programmet.
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Slutlig verifiering av lack-konfiguration

Nu när du använder de `default.vcl` som har genererats av Commerce kan du utföra några slutverifieringar för att se till att Varnish fungerar.

## Verifiera HTTP-svarshuvuden

Använd `curl` eller något annat verktyg för att visa HTTP-svarshuvuden när du besöker en Commerce-sida i en webbläsare.

Kontrollera först att du använder [utvecklarläget](../cli/set-mode.md#change-to-developer-mode). Annars ser du inte rubrikerna.

Exempel:

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Viktiga rubriker:

```
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>Det här värdet är också godtagbart: `X-Magento-Cache-Debug: HIT`.

## Kontrollera sidinläsningstider

Om lack fungerar bör alla Commerce-sidor med cache-lagrade block läsas in på mindre än 150 ms. Exempel på sådana sidor är kategorisidorna för ytterdörren och butiken.

Använd en webbläsarkontroll för att mäta sidinläsningstiden.

Så här använder du till exempel Chrome-inspektören:

1. Gå till alla cachelagrade Commerce-sidor i Chrome.
1. Högerklicka var som helst på sidan.
1. Klicka på **[!UICONTROL Inspect Element]** på snabbmenyn.
1. Klicka på fliken **[!UICONTROL Network]** i kontrollpanelen.
1. Uppdatera sidan.
1. Bläddra till toppen av kontrollpanelen så att du kan se URL-adressen till sidan som du visar.

   I följande bild visas ett exempel på hur indexsidan `magento2` läses in.

   ![Klicka på sidan som du visar](../../assets/configuration/varnish-inspector.png)

   Sidans inläsningstid visas bredvid sidans URL. I det här fallet är inläsningstiden 5 ms. Detta bekräftar att lack cachelagrade sidan.

1. Om du vill visa rubriker för HTTP-svar klickar du på sidans URL (i kolumnen Namn).

   Du kan visa HTTP-rubriker som beskrivs mer ingående i avsnittet Verifiera HTTP-svarshuvuden.

## Verifiera Commerce cache

Kontrollera att katalogen `<magento_root>/var/page_cache` är tom:

1. Logga in på Commerce-servern eller växla till filsystemets ägare.
1. Ange följande kommando:

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. Åtkomst till en eller flera tillgängliga Commerce-sidor.
1. Kontrollera katalogen `var/page_cache/`.

   Om katalogen är tom, grattis! Varnish och Commerce har konfigurerats att samarbeta!

1. Om du har rensat katalogen `var/page_cache/` startar du om Varnish.

>[!TIP]
>
>Om 503-fel (Backend Fetch Failed) inträffar, se [Felsökning 503-fel (tjänsten är inte tillgänglig)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html) i _Adobe Commerce Help Center_.
