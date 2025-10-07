---
title: Varnish ESI block
description: Lär dig mer om varnish Edge Side Includes (ESI) och hur du bäddar in webbsidor för Adobe Commerce. Identifiera implementering och optimering av ESI-block.
badge: label="Medverkad av Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---

# Varnish ESI block

ESI (Edge Side Includes) är speciella direktiv som du kan använda för att inkludera webbsidor på andra webbsidor.

Ett exempel:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

Avvikelse hämtar innehåll från `http://domain.com/index.php/page_cache/block/esi/blocks` och ersätter taggen `<esi>` med den.

## Commerce och varnish ESI

Commerce-ramverket skapar en ESI-tagg när följande villkor är uppfyllda:

- Cachningsprogrammet är inställt på `Varnish Cache`
- Ett XML-layoutelement `block` har lagts till med ett `ttl`-attribut

### Exempel

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

I exemplet ovan lägger elementet `block` till innehåll från mallen `esi.phtml` på en hemsida och sedan uppdaterar det automatiskt var 30:e sekund.

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
