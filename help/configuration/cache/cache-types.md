---
title: Cache-typer
description: Associera cachegränser med cachetyper.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Cache-typer

I följande steg går du igenom associeringen av cachefiltret frontend med en cachetyp.

## Steg 1: Definiera en cacheförskjutning

Commerce-programmet har en `default`-cacheklientstruktur som du kan använda för alla [cachetyper](../cli/manage-cache.md#clean-and-flush-cache-types). I det här avsnittet beskrivs hur du kan definiera en cachefiltr med ett annat namn, vilket är bättre om du tänker anpassa filtret.

>[!INFO]
>
>Om du vill använda cachetypen `default` behöver du inte ändra `env.php` alls. Du måste ändra Commerce globala `di.xml`. Se [Alternativ för lågnivåcache](cache-options.md).

Du måste ange en anpassad cacheklientmapp, antingen `app/etc/env.php` eller Commerce global `app/etc/di.xml`.

I följande exempel visas hur du definierar den i filen `env.php`, som åsidosätter filen `di.xml`:

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<unique frontend id>' => [
             <cache options>
        ],
    ],
    'type' => [
         <cache type 1> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
    'type' => [
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

Där `<unique frontend id>` är ett unikt namn som identifierar din klientstruktur och `<cache options>` är alternativ som beskrivs i avsnitten som är specifika för varje cachelagringstyp (databas, Redis och så vidare).

## Steg 2: Konfigurera cachen

Du kan ange konfigurationsalternativ för klientcache och serverdelscache i `env.php` eller `di.xml`. Den här uppgiften är valfri.

`env.php`-exempel:

```php?start_inline=1
'frontend' => <frontend_type>,
'frontend_options' => [
    <frontend_option> => <frontend_option_value>,
    ...
],
'backend' => <backend_type>,
'backend_options' => [
    <backend_option> => <backend_option_value>,
    ...
],
```

där

- `<frontend_type>` är klientcachetypen på låg nivå. Ange namnet på en klass som är kompatibel med `Zend\Cache\Core`.
Om du utelämnar `<frontend_type>` används [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php).

- `<frontend_option>`, `<frontend_option_value>` är namnet och värdet på de alternativ som Commerce-ramverket skickar som en associativ array till klientcacheobjektet när det skapas.
- `<backend_type>` är serverdelens lågnivåcache. Ange namnet på en klass som är kompatibel med `Zend_Cache_Backend` och som implementerar `Zend_Cache_Backend_Interface`.
- `<backend_option>` och `<backend_option_value>` är namnet och värdet på de alternativ som Commerce-ramverket skickar som en associativ array till serverdelscachen när det skapas.

Den senaste Zend-informationen finns i [Laminas-dokumentationen](https://docs.laminas.dev/).
