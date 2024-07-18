---
title: Skapa länkar till LESS-filer
description: Lär dig hur du skapar länkar till LESS-filer.
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
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
>Under utvecklingen skapar det här kommandot symboler för LESS-filer i mapparna `var/view_preprocessed` och `pub/static`. Den här processen kompilerar inte LESS-filer till CSS-filer.

I följande tabell förklaras det här kommandots parametrar och värden.

| Parameter | Värde | Obligatoriskt? |
| --------- | ----- | --------- |
| `--type` | Typ av källfiler: [less] (standard: &quot;less&quot;)<br>För närvarande är LESS den enda filtyp som stöds. | Nej |
| `--locale` | Språkkod.<br>Om du vill visa en lista med språkkoder anger du `bin/magento info:language:list` | Nej |
| `--area` | Område (`adminhtml` för administrationsområdet, `frontend` för butiken). | Nej |
| `--theme` | Temanamn i formatet `<VendorName>/<theme-name>`. Till exempel `Magento/blank` eller `Magento/backend`. | Nej |
| `<file>` | Blankstegsavgränsad lista med CSS-filer som ska konverteras till LESS utan CSS-tillägget. (Standard är `css/styles-m css/styles-l`, för adminhtml-typen `css/styles css/styles-old`) | Nej |

Om du till exempel vill skapa LESS-filer för det överordnade temat med namnet `VendorName/themeName` i `en_US` med en CSS-fil med namnet `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css` anger du följande kommando:

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

Följande meddelanden visas för att bekräfta att åtgärden lyckades:

```
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

Så här skapar du LESS-filer för administratören:

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
