---
title: Konfigurationsfiler för distribution
description: Förstå hur konfigurationsfilerna fungerar för installation av Commerce-programmet.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---


# Konfigurationsfiler för distribution

Adobe Commerce innehåller konfigurationsfiler som gör att du enkelt kan anpassa en komponent och skapa konfigurationstyper för att utöka standardfunktionerna. Distributionsprocessen består av den delade och systemspecifika konfigurationen för din installation. Distributionskonfigurationen för Commerce är uppdelad mellan [`app/etc/config.php`](../reference/config-reference-configphp.md) och [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` är _delad_ konfigurationsfil.
Den här filen innehåller en lista över installerade moduler, teman och språkpaket. och delade konfigurationsinställningar.

   Checka in den här filen om du vill ha källkontroll och använda den i dina utvecklings-, staging- och produktionssystem.

   Från och med version 2.2 `app/etc/config.php` filen är inte längre en post i `.gitignore` -fil.
Detta gjordes för att underlätta [distribution av pipeline](../deployment/technical-details.md).

- `app/etc/env.php` innehåller inställningar som är specifika för installationsmiljön.

Tillsammans `config.php` och `env.php` kallas handel _distributionskonfiguration_ eftersom filerna skapas under installationen och krävs för att starta Commerce-programmet.

>[!INFO]
>
>The [!DNL Commerce 2] distributionskonfigurationsersättningar `local.xml` in [!DNL Magento 1.x].

Till skillnad från andra [modulkonfigurationsfiler](../reference/module-files.md), Commerce-distributionskonfigurationen läses in i minnet under initieringen, sammanfogas inte med några andra filer och kan inte utökas. (`config.php` och `env.php` sammanfogas emellertid med varandra.)

## Information om distributionskonfigurationen

`config.php` och `env.php` är PHP-filer som returnerar [flerdimensionell associativ array](https://www.w3schools.com:443/php/php_arrays.asp), som i princip är en hierarkisk ordning av konfigurationsparametrar och -värden.

På den översta nivån i den här arrayen finns _konfigurationssegment_. Ett segment har godtyckligt innehåll (ett skalärvärde eller en kapslad array) som särskiljs av en godtycklig nyckel, där både nyckel- och värdepar definieras av Commerce Framework.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) ger dig bara åtkomst till dessa avsnitt, men du kan inte utöka dem.

På nästa hierarkinivå ordnas objekten i varje segment enligt [modul](https://glossary.magento.com/module) sekvensdefinition, som erhålls genom att sammanfoga alla modulers konfigurationsfiler, förutom inaktiverade moduler.

I följande avsnitt beskrivs strukturen och innehållet i distributionskonfigurationen:

- Hantera installerade moduler
- Systemspecifik konfiguration

## Hantera installerade moduler

The `config.php` filen innehåller en lista med installerade moduler. Adobe Commerce tillhandahåller både kommandoradsverktyg och webbaserade verktyg för att hantera moduler (installera, avinstallera, aktivera, inaktivera eller uppgradera).

Exempel:

- Avinstallera komponenter: [`bin/magento setup:uninstall`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall.html)
- Kontrollera komponenternas status: [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- Aktivera eller inaktivera komponenter: [`bin/magento module:disable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html#instgde-cli-subcommands-enable-disable), [`bin/magento module:enable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html#instgde-cli-subcommands-enable-disable).

> _config.php_

```php
return array (
  'modules' =>
  array (
    'Magento_Core' => 1,
    'Magento_Store' => 1,
    'Magento_Theme' => 1,
    'Magento_Authorization' => 1,
    'Magento_Directory' => 1,
    'Magento_Backend' => 1,
    'Magento_Backup' => 1,
    'Magento_Eav' => 1,
    'Magento_Customer' => 1,
...
  ),
);
```

Värdet `1` eller `0` anger om en modul är aktiverad eller inaktiverad.

Inaktiverade moduler känns inte igen av handelsprogrammet. med andra ord deltar de inte i sammanslagningskonfigurationen, i beroendeinjektioner, händelser, plugin-program och så vidare. Inaktiverade moduler ändrar inte [storefront](https://glossary.magento.com/storefront) eller [Administratör](https://glossary.magento.com/admin) och påverkar inte routningen.

Den enda praktiska skillnaden mellan en inaktiverad modul och en modul som inte finns i kodbasen är att en inaktiverad modul hittas av den automatiska inläsaren och dess klasser och konstanter är tillgängliga för återanvändning i annan kod.