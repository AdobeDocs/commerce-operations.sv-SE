---
title: Rubriken X-Frame-Options
description: Använd X-Frame-Options för att styra sidåtergivningen.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Rubriken X-Frame-Options

För att förhindra [Klickjacking](https://owasp.org/www-community/attacks/Clickjacking) explosioner, vi har lagt till ett alternativ för att använda [X-frame-options](https://datatracker.ietf.org/doc/html/rfc7034) HTTP-begärandehuvud i begäranden till butiken.

The `X-Frame-Options` Med kan du ange om en webbläsare ska kunna återge en sida i en `<frame>`, `<iframe>`, eller `<object>` enligt följande:

- `DENY`: Det går inte att visa sidan i en ram.
- `SAMEORIGIN`: (standard) Sidan kan bara visas i en ram med samma ursprung som själva sidan.

>[!WARNING]
>
>The `ALLOW-FROM <uri>` eftersom webbläsare som stöds i Commerce inte längre stöder det. Se [Webbläsarkompatibilitet](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Av säkerhetsskäl rekommenderar Adobe starkt att du inte kör Commerce Store i en bildruta.

## Implementera `X-Frame-Options`

Ange ett värde för `X-Frame-Options` in `<magento_root>/app/etc/env.php`. Följande är standardvärdet:

```php
'x-frame-options' => 'SAMEORIGIN',
```

>[!TIP]
>
>Det är säkrare att redigera `env.php` än det är för att ange ett värde i Admin.

## Verifiera inställningarna för `X-Frame-Options`

Kontrollera inställningarna genom att visa HTTP-rubriker på alla butikssidor. Det finns flera sätt att göra detta, bland annat genom att använda en webbläsarkontroll.

I följande exempel används curl, som du kan köra från alla datorer som kan ansluta till din Commerce-server via HTTP-protokollet.

Använd följande kommando:

```bash
curl -I -v --location-trusted '<your storefront URL>'
```

Leta efter `X-Frame-Options` i rubrikerna.
