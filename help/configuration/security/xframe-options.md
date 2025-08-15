---
title: Förhindra clickjacking-attacker
description: Förhindra clickjacking-explosioner genom att använda rubriken "X-Frame-Options" för att styra sidåtergivningen.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Förhindra clickjacking-attacker

Förhindra [clickjacking](https://owasp.org/www-community/attacks/Clickjacking)-attacker genom att ta med HTTP-begärandehuvudet [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) i begäranden till butiken.

Med rubriken `X-Frame-Options` kan du ange om en webbläsare får återge en sida i en `<frame>`, `<iframe>` eller `<object>` enligt följande:

- `DENY`: Det går inte att visa sidan i en ram.
- `SAMEORIGIN`: (standard) Sidan kan bara visas i en ram med samma ursprung som själva sidan.

>[!WARNING]
>
>Alternativet `ALLOW-FROM <uri>` har tagits bort eftersom webbläsare som stöds av Commerce inte längre stöder det. Se [Webbläsarkompatibilitet](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Av säkerhetsskäl rekommenderar Adobe starkt att du inte kör Commerce Store i en bildruta.

## Implementera `X-Frame-Options`

Ange ett värde för `X-Frame-Options` i `<project-root>/app/etc/env.php`. Standardvärdet är följande:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Distribuera om för ändringar av filen `env.php` så att den träder i kraft.

>[!TIP]
>
>Det är säkrare att redigera filen `env.php` än att ange ett värde i administratören.

## Verifiera din inställning för `X-Frame-Options`

Kontrollera inställningarna genom att visa HTTP-rubrikerna på alla butikssidor. Det finns flera sätt att göra detta, bland annat genom att använda en webbläsarkontroll.

I följande exempel används curl, som du kan köra från vilken dator som helst som kan ansluta till din Commerce-server via HTTP-protokollet.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Leta efter värdet `X-Frame-Options` i rubrikerna.
