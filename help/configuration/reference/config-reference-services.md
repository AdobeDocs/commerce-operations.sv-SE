---
title: Referens för tjänstkonfigurationssökvägar
description: Visa en lista med tjänstens konfigurationsvärden.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# Referens för tjänstkonfigurationssökvägar

I det här avsnittet visas variabelnamn och konfigurationssökvägar som är tillgängliga för alternativ i Admin under **Lager** > Inställningar > **Konfiguration** > **Tjänster**.

The [`magento app:config:dump` kommando](../cli/export-configuration.md) skriver dessa värden i den delade konfigurationsfilen, `app/etc/config.php`, som bör vara i källkontroll. Om du vill åsidosätta konfigurationsinställningar eller ange känsliga inställningar läser du [Använd miljövariabler för att åsidosätta konfigurationsinställningar](override-config-settings.md#environment-variables). Det här avsnittet gör _not_ list [känsliga och systemspecifika värden](config-reference-sens.md).

## Webb-API-sökvägar för Commerce

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Tjänster** > **Webb-API**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Standardsvarsdiagram | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tillåt anonym gäståtkomst | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## OAuth-sökvägar

Dessa konfigurationsvärden är tillgängliga i Admin i **Lager** > Inställningar > **Konfiguration** > **Tjänster** > **OAuth**.

| Namn | Konfigurationssökväg | Endast handel? |
|--------------|--------------|--------------|
| Livstid för kundtoken (timmar) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Löptid för Admin Token (timmar) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sannolikhet för rensning | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Förfallotid | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Förfallotid | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth-konsumentreferenser HTTP Post maxredirects | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth-konsumentens autentiseringsuppgifter HTTP Post-timeout | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
