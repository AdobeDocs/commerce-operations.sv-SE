---
title: Optimera CSS- och JS-resursfiler
description: Lär dig hur du sammanfogar och minimerar CSS- och JavaScript-filer (JS) för Adobe Commerce-projekt från Admin eller från kommandoraden.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: e6e8a2d7ef059265dbcbfcd6be117828a639f6d6
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Optimera resursfiler

För en mer responsiv Commerce-webbplats optimerar du CSS- och JavaScript-resursfiler (JS) och eliminerar resurser som blockerar renderingar.

- **Optimera CSS- och JS-filer**- Minska tiden som krävs för att läsa in CSS- och JavaScript-filer (JS) genom att konfigurera Adobe Commerce för att sammanfoga, minimera och paketera separata filer i en enda fil.
- **Eliminera resurser som blockerar återgivningen**- Överväg att leverera viktiga JS- och CSS-funktioner som infogas och skjuta upp alla icke-kritiska JS/CSS-format. Mer information finns i [Eliminera resurser som blockerar återgivningen](https://web.dev/render-blocking-resources/).

## Berörda produkter och versioner

[Alla versioner som stöds, 2.3 och senare](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt
- Magento Open Source

## Sammanfoga eller miniatyrbilder för CSS-filer

Den tid det tar att läsa in CSS- och JavaScript-filer (JS) kan minskas genom att separata filer sammanfogas, minimeras och paketeras i en enda fil.

>[!IMPORTANT]
>
>Adobe Commerce i molninfrastruktur körs alltid i produktionsläget och det går inte att ställa in det på något annat sätt. Därför måste du använda kommandoradsmetoden för att aktivera sammanfogning, miniatyr och paketering.

### Använda Admin

Om du vill aktivera CSS-sammanslagning eller -miniatyr går du till [!UICONTROL **Administratör** > **Lager** > **Inställning** > **Konfiguration** > **Avancerat** > **Utvecklare** > **CSS-inställningar**].

### Använda kommandoraden

Så här aktiverar du CSS-sammanslagning i Adobe Commerce i molninfrastruktur:

1. Kör det här kommandot lokalt:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Genomför ändringar i `app/etc/config.php` och distribuera om.

Så här aktiverar du CSS-miniatyr i Adobe Commerce i molninfrastruktur:

1. Kör det här kommandot lokalt:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Genomför ändringar i `app/etc/config.php` och distribuera om.

## Minimera JS-filer

### Använda Admin

På *Administratör* sidebar, gå till **Lager** > **Inställningar** > **Konfiguration** > **Avancerat** > **Utvecklare** > **JavaScript-inställningar**.

### Använda kommandoraden

Så här aktiverar du JS-miniatyr i Adobe Commerce i molninfrastruktur:

1. Kör det här kommandot lokalt:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Genomför ändringar i `app/etc/config.php` och distribuera om.

## Sammanfoga och bunta JS-filer

Du kan aktivera sammanslagning eller paketering i Commerce Admin (sammanslagning och paketering kan inte aktiveras samtidigt): [!UICONTROL **Lager** > **Inställningar** > **Konfiguration** > **Avancerat** > **Utvecklare** > **JavaScript-inställningar**].

Du kan även aktivera Adobe Commerce inbyggda paketering (grundläggande paketering) via kommandoraden:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Ytterligare information

- [Optimeringsinställningar på klientsidan](../../../performance/configuration.md#client-side-optimization-settings)
- [Användarhandbok: Optimera resursfiler](https://docs.magento.com/user-guide/system/file-optimization.html)
- [Utvecklarhandbok för Fornend: CSS-sammanslagning, miniatyrbilder och webbplatsprestanda](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Avancerad JavaScript-paketering](../../../performance/advanced-js-bundling.md)

