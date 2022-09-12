---
title: Visa eller ändra Admin URI
description: Följ de här stegen för att visa och ändra URI:n för ditt Adobe Commerce- eller Magento Open Source Admin-program.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Visa eller ändra Admin URI

Innan du kör det här kommandot måste du [Skapa eller uppdatera distributionskonfigurationen](deployment.md).

## Visa Admin-URI

I det här avsnittet beskrivs hur du använder kommandoraden för att visa [Administratör](https://glossary.magento.com/admin) Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

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
