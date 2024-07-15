---
title: Visa eller ändra Admin URI
description: Följ de här stegen för att visa och ändra URI:n för ditt Adobe Commerce Admin-program.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Visa eller ändra Admin URI

Innan du kör det här kommandot måste du [skapa eller uppdatera distributionskonfigurationen](deployment.md).

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

Du kan även visa Admin-URI i `<magento_root>/app/etc/env.php`. Ett utdrag följer:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Ändra Admin-URL

Använd kommandot [`magento setup:config:set`](deployment.md) om du vill ändra Admin URI.
