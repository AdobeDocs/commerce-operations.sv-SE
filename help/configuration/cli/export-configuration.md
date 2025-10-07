---
title: Exportera konfigurationsinställningar
description: Lär dig hur du exporterar Adobe Commerce konfigurationsinställningar till filer med hjälp av config dump. Identifiera driftsättning och konfigurationshantering för pipeline.
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Exportera konfigurationsinställningar

I Commerce 2.2 och senare [pipeline-distributionsmodell](../deployment/technical-details.md) kan du upprätthålla en konsekvent konfiguration över alla system. När du har konfigurerat inställningarna i Admin i utvecklingssystemet exporterar du inställningarna till konfigurationsfiler med följande kommando:

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ är en blankstegsavgränsad lista med konfigurationstyper som ska dumpas. Tillgängliga typer är `scopes`, `system`, `themes` och `i18n`. Om inga konfigurationstyper anges, kommer all systemkonfigurationsinformation att ignoreras.

I följande exempel dumpas endast omfattningar och teman:

```bash
bin/magento app:config:dump scopes themes
```

Som ett resultat av kommandokörningen uppdateras följande konfigurationsfiler:

- `app/etc/config.php`

  Det här är den delade konfigurationsfilen för alla dina Commerce-instanser.
Inkludera detta i källkontrollen så att det kan delas mellan utvecklings-, bygg- och produktionssystemen.

  Se [config.php-referens](../reference/config-reference-configphp.md).

- `app/etc/env.php`

  Det här är den miljöspecifika konfigurationsfilen.
Den innehåller känsliga och systemspecifika inställningar för enskilda miljöer.

  Ta _inte_ med den här filen i källkontrollen.

  Se [env.php-referens](../reference/config-reference-envphp.md).

## Känsliga eller systemspecifika inställningar

Använd kommandot `env.php` om du vill ange de känsliga inställningar som skrivits till [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values).

Konfigurationsvärden anges som antingen känsliga eller systemspecifika genom att referera till [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) i modulens [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific)-fil.

Om du vill exportera ytterligare systeminställningar när du använder `config_types` bör du använda kommandot [`bin/magento config:set`](set-configuration-values.md#set-values).
