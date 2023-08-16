---
title: Varnish ESI block
description: Lär dig mer om Edge Side Includes och hur du kan använda dem för att bädda in webbsidor.
badge: label="Medverkad av Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Varnish ESI block

Edge Side Includes (ESI) är speciella direktiv som du kan använda för att inkludera webbsidor på andra webbsidor.

Ett exempel:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

Finska hämtar innehåll från `http://domain.com/index.php/page_cache/block/esi/blocks` och ersätta `<esi>` tagga med den.

## Commerce och Varnish ESI

I Commerce Framework skapas en ESI-tagg när följande villkor är uppfyllda:

- Cachelagringsprogrammet är inställt på `Varnish Cache`
- En XML-layout `block` element läggs till med `ttl` attribute

### Exempel

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

I exemplet ovan är `block` elementet lägger till innehåll från `esi.phtml` till en hemsida så uppdateras det automatiskt var 30:e sekund av Varannan mall.

## Begränsningar

För närvarande stöder inte engelska ESI över HTTPS, vilket innebär att det automatiskt växlar till HTTP.

`Magento\PageCache\Observer\ProcessLayoutRenderElement`:

```php
    private function _wrapEsi(
        \Magento\Framework\View\Element\AbstractBlock $block,
        \Magento\Framework\View\Layout $layout
    ) {
    ....
        // Varnish does not support ESI over HTTPS must change to HTTP
        $url = substr($url, 0, 5) === 'https' ? 'http' . substr($url, 5) : $url;
        return sprintf('<esi:include src="%s" />', $url);
    }
```
