---
title: Konfigurationsfiler för distribution
description: Förstå hur konfigurationsfilerna fungerar för installation av Commerce-programmet.
feature: Configuration, Deploy
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: b40d2bd4d466782ba5bc1b29ee8681756d9e85cc
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Konfigurationsfiler för distribution

Adobe Commerce innehåller konfigurationsfiler som gör att du enkelt kan anpassa en komponent och skapa konfigurationstyper för att utöka standardfunktionerna. Distributionsprocessen består av den delade och systemspecifika konfigurationen för din installation. Commerce distributionskonfiguration är uppdelad mellan [`app/etc/config.php`](../reference/config-reference-configphp.md) och [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` är konfigurationsfilen _shared_.
Den här filen innehåller en lista över installerade moduler, teman och språkpaket samt delade konfigurationsinställningar.

  Checka in den här filen om du vill ha källkontroll och använda den i dina utvecklings-, staging- och produktionssystem.

- `app/etc/env.php` innehåller inställningar som är specifika för installationsmiljön.

Tillsammans kallas `config.php` och `env.php` för Commerce _distributionskonfiguration_ eftersom filerna skapas under installationen och krävs för att starta Commerce-programmet.

>[!INFO]
>
>Distributionskonfigurationen [!DNL Commerce 2] ersätter `local.xml` i [!DNL Magento 1.x].

Till skillnad från andra [modulkonfigurationsfiler](../reference/module-files.md) läses Commerce distributionskonfiguration in i minnet under initieringen, sammanfogas inte med andra filer och kan inte utökas. (`config.php` och `env.php` sammanfogas emellertid med varandra.)

## Information om distributionskonfigurationen

`config.php` och `env.php` är PHP-filer som returnerar en [flerdimensionell associativ array](https://www.w3schools.com:443/php/php_arrays.asp), vilket i princip är en hierarkisk struktur av konfigurationsparametrar och -värden.

Den översta nivån i den här arrayen är _konfigurationssegment_. Ett segment har godtyckligt innehåll (ett skalärvärde eller en kapslad array) som särskiljs av en godtycklig nyckel, där både nyckel- och värdepar definieras av Commerce-ramverket.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) ger dig bara åtkomst till de här avsnitten, men du kan inte utöka dem.

På nästa hierarkinivå ordnas objekt i varje segment enligt modulsekvensdefinitionen, som hämtas genom att alla modulers konfigurationsfiler sammanfogas, förutom inaktiverade moduler.

I följande avsnitt beskrivs strukturen och innehållet i distributionskonfigurationen:

- Hantera installerade moduler
- Systemspecifik konfiguration

## Hantera installerade moduler

Filen `config.php` innehåller en lista med installerade moduler. Adobe Commerce tillhandahåller både kommandoradsverktyg och webbaserade verktyg för att hantera moduler (installera, avinstallera, aktivera, inaktivera eller uppgradera).

Exempel:

- Avinstallera komponenter: [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- Kontrollera komponenternas status: [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- Aktivera eller inaktivera komponenter: [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md), [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md).

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

Inaktiverade moduler känns inte igen av Commerce-programmet, vilket innebär att de inte deltar i sammanslagningskonfigurationen, i beroendeinjektioner, händelser, plugin-program osv. Inaktiverade moduler ändrar inte butiken eller administratören och påverkar inte routningen.

Den enda praktiska skillnaden mellan en inaktiverad modul och en modul som inte finns i kodbasen är att en inaktiverad modul hittas av den automatiska inläsaren och dess klasser och konstanter är tillgängliga för återanvändning i annan kod.
