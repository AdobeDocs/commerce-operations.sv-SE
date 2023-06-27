---
title: Visa eller ändra Admin URI
description: Följ de här stegen för att visa och ändra URI:n för ditt Adobe Commerce- eller Magento Open Source Admin-program.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Visa eller ändra Admin URI

Innan du kör det här kommandot måste du [Skapa eller uppdatera distributionskonfigurationen](deployment.md).

## Visa Admin-URI

I det här avsnittet beskrivs hur du använder kommandoraden för att visa Admin Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

Kommandoalternativ:

```bash
bin/magento info:adminuri
```

Ett exempelresultat följer:

```terminal
Admin Panel URI: /admin_1wgrah
```

Du kan även visa Admin URI i `<magento_root>/app/etc/env.php`. Ett utdrag följer:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Ändra Admin-URL

Om du vill ändra Admin URI använder du [`magento setup:config:set`](deployment.md) -kommando.
