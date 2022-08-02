---
title: Skapa länkar till LESS-filer
description: Lär dig hur du skapar länkar till LESS-filer.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Skapa länkar till LESS-filer

{{file-system-owner}}

Så här skapar du länkar till LESS-filer:

Kommandoalternativ:

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>Under utvecklingen skapar det här kommandot länkar för LESS-filer i `var/view_preprocessed` och `pub/static` mappar. Den här processen kompilerar inte LESS-filer till CSS-filer.

I följande tabell förklaras det här kommandots parametrar och värden.

| Parameter | Värde | Obligatoriskt? |
| --------- | ----- | --------- |
| `--type` | Typ av källfiler: [mindre] (standard: &quot;less&quot;)<br>För närvarande är LESS den enda filtypen som stöds. | Nej |
| `--locale` | Språkkod.<br>Om du vill visa en lista med språkkoder anger du `bin/magento info:language:list` | Nej |
| `--area` | Område (`adminhtml` för det administrativa området, `frontend` för butiken). | Nej |
| `--theme` | Temanamn i `<VendorName>/<theme-name>` format. Till exempel: `Magento/blank` eller `Magento/backend`. | Nej |
| `<file>` | Blankstegsavgränsad lista med CSS-filer som ska konverteras till LESS utan CSS-tillägget. (Standard är `css/styles-m css/styles-l`, för adminhtml-typ `css/styles css/styles-old`) | Nej |

Om du till exempel vill skapa LESS-filer för fronttemat med namnet `VendorName/themeName` i `en_US` nationella inställningar med hjälp av en CSS-fil med namnet `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`anger du följande kommando:

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

Följande meddelanden visas för att bekräfta att åtgärden lyckades:

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

Så här skapar du LESS-filer för administratören:

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
