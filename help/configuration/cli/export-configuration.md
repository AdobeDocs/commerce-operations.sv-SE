---
title: Exportera konfigurationsinställningar
description: Exportera Adobe Commerce konfigurationsinställningar till konfigurationsfiler, som också kallas config dump.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# Exportera konfigurationsinställningar

I Commerce 2.2 och senare [distributionsmodell för pipeline](../deployment/technical-details.md)kan du ha en konsekvent konfiguration över alla system. När du har konfigurerat inställningarna i Admin i utvecklingssystemet exporterar du inställningarna till konfigurationsfiler med följande kommando:

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ är en blankstegsavgränsad lista med konfigurationstyper som ska dumpas. Tillgängliga typer inkluderar `scopes`, `system`, `themes`och `i18n`. Om inga konfigurationstyper anges, kommer all systemkonfigurationsinformation att ignoreras.

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

   Gör _not_ inkludera den här filen i källkontrollen.

   Se [env.php reference](../reference/config-reference-envphp.md).

## Känsliga eller systemspecifika inställningar

Ställa in känsliga inställningar skrivna till `env.php`, använder du [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) -kommando.

Konfigurationsvärden anges antingen som känsliga eller systemspecifika genom referens [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) i modulen [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) -fil.

Exportera ytterligare systeminställningar när du använder `config_types`kan du använda [`bin/magento config:set`](set-configuration-values.md#set-values) -kommando.
