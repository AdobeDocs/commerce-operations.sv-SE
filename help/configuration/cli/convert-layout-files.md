---
title: Konvertera layoutfiler
description: Konvertera XML-layoutfiler.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
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
