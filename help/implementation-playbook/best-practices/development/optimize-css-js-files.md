---
title: Optimera CSS- och JS-resursfiler
description: Lär dig hur du sammanfogar och minimerar CSS- och JavaScript-filer (JS) för Adobe Commerce-projekt från Admin eller från kommandoraden.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: a08560eb307638a36fdc52224c41bdf2c5d47763
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Optimera resursfiler

För en mer responsiv Commerce-webbplats optimerar du CSS- och JavaScript-resursfiler (JS) och eliminerar resurser för återgivningsblockering.

- **Optimera CSS- och JS-filer** - Minska den tid som krävs för att läsa in CSS- och JavaScript-filer (JS) genom att konfigurera Adobe Commerce för att minimera och paketera filer.
- **Eliminera resurser för återgivningsblockering** - Överväg att leverera viktiga JS- och CSS-funktioner som är infogade och skjuta upp alla icke-kritiska JS/CSS-format. Mer information finns i [Ta bort resurser för återgivningsblockering](https://web.dev/render-blocking-resources/).

## Berörda produkter och versioner

[Alla versioner som stöds, 2.3 och senare](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Sammanfoga eller miniatyrbilder för CSS-filer

Den tid det tar att läsa in CSS- och JavaScript-filer (JS) kan minskas genom att separata filer sammanfogas, minimeras och paketeras i en enda fil.

>[!IMPORTANT]
>
>Adobe Commerce i molninfrastruktur körs alltid i produktionsläget och det går inte att ställa in det på något annat sätt. Därför måste du använda kommandoradsmetoden för att aktivera sammanfogning, miniatyr och paketering.

Sammanfoga inte eller paketera filer om HTTP/2 används i distributionen. HTTP/2 hämtar statiska filer asynkront. Webbläsare måste hämta en hel sammanfogad fil innan filinnehållet kan bearbetas.

### Använda Admin

Om du vill aktivera CSS-sammanslagning eller -miniatyr går du till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL CSS Settings]**.

### Använda kommandoraden

Så här aktiverar du CSS-sammanslagning i Adobe Commerce i molninfrastruktur:

1. Kör det här kommandot lokalt:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Genomför ändringar i filen `app/etc/config.php` och omdistribuera den.

Så här aktiverar du CSS-miniatyr i Adobe Commerce i molninfrastruktur:

1. Kör det här kommandot lokalt:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Genomför ändringar i filen `app/etc/config.php` och omdistribuera den.

## Minimera JS-filer

### Använder [!UICONTROL Admin]

Gå till [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** på sidofältet **[!UICONTROL JavaScript Settings]**.

### Använda kommandoraden

Så här aktiverar du JS-miniatyr i Adobe Commerce i molninfrastruktur:

1. Kör det här kommandot lokalt:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Genomför ändringar i filen `app/etc/config.php` och omdistribuera den.

## Paketera JS-filer

Du kan aktivera paketering i Commerce [!UICONTROL Admin]: **[!UICONTROL Stores]** > ***[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**.

>[!NOTE]
>
>Sammanfogning och paketering kan inte aktiveras samtidigt.

Du kan även aktivera Adobe Commerce inbyggda paketering (grundläggande paketering) via kommandoraden:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Sammanfoga JS-filer (rekommenderas inte) {#merge-js-files}

>[!WARNING]
>
>Vi rekommenderar inte att du aktiverar **[!UICONTROL Merge JavaScript Files]**. Den här inställningen har endast utformats för synkront inläst JavaScript i avsnittet **[!UICONTROL HEAD]** på sidan och kan göra att paketering och [!DNL RequireJS]-logik inte fungerar som de ska. Den behålls endast för bakåtkompatibilitet och ger inga prestandafördelar när HTTP/2 är aktiverat.
>
>Om du har **[!UICONTROL Merge JavaScript Files]** aktiverat och stöter på problem kan du inaktivera det innan du använder några korrigeringar. Se [ACSD-67908](../../../tools/quality-patches-tool/patches-available-in-qpt/v1-1-73/acsd-67908.md) om du inte kan inaktivera sammanslagning.

## Ytterligare information

- [Optimeringsinställningar på klientsidan](../../../performance/configuration.md#client-side-optimization-settings)
- [Pakettips](../../../performance/configuration.md#bundling-tips) i *Bästa praxis för konfiguration* - paketeringsverktyg från tredje part, HTTP/2 och vägledning om borttagen JS- och CSS-sammanslagning
- [Användarhandbok: Optimera resursfiler](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [Utvecklarhandbok för Fornend: CSS-sammanslagning, miniatyr- och webbplatsprestanda](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Avancerad JavaScript-paketering](../../../performance/advanced-js-bundling.md)
