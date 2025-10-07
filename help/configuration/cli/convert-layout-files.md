---
title: Konvertera layoutfiler
description: Lär dig hur du konverterar XML-layoutfiler med Adobe Commerce kommandoradsverktyg. Upptäck uppdateringar av XSLT-formatmallar och filkonverteringsprocesser.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '98'
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

- `{xml file}` - är den fullständiga sökvägen och filnamnet för en XML-layoutfil som ska konverteras (obligatoriskt)
- `{xslt stylesheet}` - är den fullständiga sökvägen och filnamnet för en XSLT-formatmallsfil som ska användas för konvertering (obligatoriskt)
- `-o|--overwrite` - inkludera det här alternativet om du vill skriva över den befintliga XML-filen
