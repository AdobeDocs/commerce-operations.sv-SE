---
title: Cachetyper
description: Associera cachegränser med cachetyper.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Cachetyper

I följande steg går du igenom associeringen av cachefiltret frontend med en cachetyp.

## Steg 1: Definiera en cacheklientdel

Commerce-programmet har en `default` cachefrontend som du kan använda för alla [cachetyp](../cli/manage-cache.md#clean-and-flush-cache-types). I det här avsnittet beskrivs hur du kan definiera en cachefiltr med ett annat namn, vilket är bättre om du tänker anpassa filtret.

>[!INFO]
>
>Så här använder du `default` cachetyp, du behöver inte ändra `env.php` över huvud taget, du ändrar Commerce&#39;s global `di.xml`. Se [Cachealternativ på låg nivå](cache-options.md).

Du måste ange en anpassad cacheförgrund antingen `app/etc/env.php` eller Commerce&#39;s global `app/etc/di.xml`.

I följande exempel visas hur du definierar det i `env.php` som åsidosätter `di.xml` fil:

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

Plats `<unique frontend id>` är ett unikt namn som identifierar din front och `<cache options>` är alternativ som behandlas i de ämnen som är specifika för varje cachelagringstyp (databas, Redis och så vidare).

## Steg 2: Konfigurera cacheminnet

Du kan ange konfigurationsalternativ för klientcache och serverdelscache i `env.php` eller `di.xml`. Denna uppgift är valfri.

`env.php` exempel:

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

- `<frontend_type>` är klientens lågnivå-cachetyp. Ange namnet på en klass som är kompatibel med [Zend\Cache\Core](https://framework.zend.com/apidoc/1.7/Zend_Cache/Zend_Cache_Core.html).

   Om du utelämnar `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) används.

- `<frontend_option>`, `<frontend_option_value>` är namnet på och värdet på de alternativ som skickas som en associativ array till klientcache när den skapas.
- `<backend_type>` är serverdelens lågnivåcache. Ange namnet på en klass som är kompatibel med [Zend_Cache_Backend](https://framework.zend.com/apidoc/1.7/Zend_Cache/Zend_Cache_Backend/Zend_Cache_Backend.html) och som implementerar [Zend_Cache_Backend_Interface](https://framework.zend.com/apidoc/1.6/Zend_Cache/Zend_Cache_Backend/Zend_Cache_Backend_Interface.html).
- `<backend_option>` och `<backend_option_value>` är namnet på och värdet på de alternativ som Commerce Framework skickar som en associativ array till serverdelscachen när det skapas.
