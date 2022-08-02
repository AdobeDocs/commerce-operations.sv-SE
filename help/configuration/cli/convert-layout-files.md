---
title: Konvertera layoutfiler
description: Konvertera XML-layoutfiler.
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# Konvertera XML-layoutfiler

{{file-system-owner}}

Använd det här kommandot för att uppdatera XML-layoutfiler om du uppdaterar motsvarande XSLT-formatmall (Extensible Stylesheet Language Transformations).

- [Layoutinstruktioner](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/xml-instructions.html)
- [Layoutfiltyper](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/layout-types.html)

Kommandoalternativ:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Var:

- `{xml file}`—är den fullständiga sökvägen och filnamnet för en XML-layoutfil som ska konverteras (obligatoriskt)
- `{xslt stylesheet}`—är den fullständiga sökvägen och filnamnet för en XSLT-formatmallsfil som ska användas för konvertering (obligatoriskt)
- `-o|--overwrite`—include this option to overwrite the existing XML file
