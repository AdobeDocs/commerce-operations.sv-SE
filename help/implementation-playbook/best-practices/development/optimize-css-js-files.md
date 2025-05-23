---
title: Optimera CSS- och JS-resursfiler
description: Lär dig hur du sammanfogar och minimerar CSS- och JavaScript-filer (JS) för Adobe Commerce-projekt från Admin eller från kommandoraden.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Optimera resursfiler

För en mer responsiv Commerce-webbplats optimerar du CSS- och JavaScript-resursfiler (JS) och eliminerar resurser för återgivningsblockering.

- **Optimera CSS- och JS-filer** - Minska den tid som krävs för att läsa in CSS- och JavaScript-filer (JS) genom att konfigurera Adobe Commerce så att separata filer sammanfogas, minimeras och paketeras i en enda fil.
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

Om du vill aktivera CSS-sammanslagning eller -miniatyr går du till [!UICONTROL **Admin** > **Lager** > **Inställningar** > **Konfiguration** > **Avancerat** > **Utvecklare** > **CSS-inställningar**].

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

### Använda Admin

Gå till **Store** > **Settings** > **Configuration** > **Advanced** > **Developer** > **JavaScript Settings** på sidofältet *Admin*.

### Använda kommandoraden

Så här aktiverar du JS-miniatyr i Adobe Commerce i molninfrastruktur:

1. Kör det här kommandot lokalt:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Genomför ändringar i filen `app/etc/config.php` och omdistribuera den.

## Sammanfoga och bunta JS-filer

Du kan aktivera sammanslagning eller paketering i Commerce Admin (sammanslagning och paketering kan inte aktiveras samtidigt): [!UICONTROL **Lagrar** > **Inställningar** > **Konfiguration** > **Avancerat** > **Utvecklare** > **JavaScript-inställningar**].

Du kan även aktivera Adobe Commerce inbyggda paketering (grundläggande paketering) via kommandoraden:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Ytterligare information

- [Optimeringsinställningar på klientsidan](../../../performance/configuration.md#client-side-optimization-settings)
- [Användarhandbok: Optimera resursfiler](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [Utvecklarhandbok för Fornend: CSS-sammanslagning, miniatyr- och webbplatsprestanda](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Avancerad JavaScript-paketering](../../../performance/advanced-js-bundling.md)
