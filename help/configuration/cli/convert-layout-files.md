---
title: Konvertera layoutfiler
description: Konvertera XML-layoutfiler.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# Konvertera XML-layoutfiler

{{file-system-owner}}

Använd det här kommandot för att uppdatera XML-layoutfiler om du uppdaterar motsvarande XSLT-formatmall (Extensible Stylesheet Language Transformations).

- [Layoutinstruktioner](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [Layoutfiltyper](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

Kommandoalternativ:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Var:

- `{xml file}`—är den fullständiga sökvägen och filnamnet för en XML-layoutfil som ska konverteras (obligatoriskt)
- `{xslt stylesheet}`—är den fullständiga sökvägen och filnamnet för en XSLT-formatmallsfil som ska användas för konvertering (obligatoriskt)
- `-o|--overwrite`—include this option to overwrite the existing XML file
