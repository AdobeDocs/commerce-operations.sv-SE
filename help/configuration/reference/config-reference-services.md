---
title: Referens för konfigurationssökvägar för tjänster
description: Visa en lista med tjänstens konfigurationsvärden.
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Referens för konfigurationssökvägar för tjänster

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **Lagrar** > Inställningar > **Konfiguration** > **Tjänster**.

[`magento app:config:dump`-kommandot ](../cli/export-configuration.md) skriver dessa värden till den delade konfigurationsfilen `app/etc/config.php` som ska finnas i källkontrollen. Om du vill åsidosätta konfigurationsinställningar eller ange känsliga inställningar läser du [Använda miljövariabler för att åsidosätta konfigurationsinställningar](override-config-settings.md#environment-variables). Det här avsnittet listar _inte_ [känsliga och systemspecifika värden](config-reference-sens.md).

## Commerce Web API-sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > **Tjänster** > **Webb-API**.

| Namn | Konfigurationssökväg | Endast Commerce? |
|--------------|--------------|--------------|
| Standardsvarsdiagram | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåt anonym gäståtkomst | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## OAuth-sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Store** > Inställningar > **Konfiguration** > **Tjänster** > **OAuth**.

| Namn | Konfigurationssökväg | Endast Commerce? |
|--------------|--------------|--------------|
| Livstid för kundtoken (timmar) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Löptid för Admin Token (timmar) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sannolikhet för rensning | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Förfallotid | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Förfallotid | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth-konsumentreferenser HTTP Post maxredirects | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth-konsumentens inloggningsuppgifter HTTP Post-timeout | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
