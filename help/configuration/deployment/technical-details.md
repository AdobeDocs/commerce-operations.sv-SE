---
title: Teknisk information
description: Läs om teknisk information om distribution av pipeline, olika konfigurationstyper och rekommenderade arbetsflöden.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---


# Teknisk information

I det här avsnittet diskuteras teknisk implementeringsinformation om pipeline-distribution i Commerce 2.2 och senare. Förbättringar kan delas in i följande områden:

- [Konfigurationshantering](#configuration-management)
- [Ändringar i administratören](#changes-in-the-admin)
- [Installera och ta bort cron](#install-and-remove-cron)

I det här avsnittet diskuteras även [rekommenderat arbetsflöde](#recommended-workflow) för driftsättning av pipeline och ger några exempel som hjälper dig att förstå hur det fungerar.

Innan du börjar bör du granska [Krav för dina utvecklings-, bygg- och produktionssystem](../deployment/prerequisites.md).

## Konfigurationshantering

Använd följande åsidosättningsschema om du vill synkronisera och underhålla konfigurationen för dina utvecklings- och produktionssystem.

![Hur konfigurationsvariabelvärden bestäms](../../assets/configuration/override-flow-diagram.png)

Som diagrammet visar används konfigurationsvärdena i följande ordning:

1. Miljövariabler åsidosätter alla andra värden, om de finns.
1. Från de delade konfigurationsfilerna `env.php` och `config.php`. Värden i `env.php` åsidosätt värden i `config.php`.
1. Från värden som lagras i databasen.
1. Om det inte finns något värde i någon av dessa källor används standardvärdet eller NULL.

### Hantera den delade konfigurationen

Den delade konfigurationen lagras i `app/etc/config.php`, som bör vara i källkontroll.

Ange den delade konfigurationen i Admin i din utveckling (eller Adobe Commerce i molninfrastrukturen) _integration_) och skriva konfigurationen till `config.php` med [`magento app:config:dump` kommando](../cli/export-configuration.md).

### Hantera den systemspecifika konfigurationen

Den systemspecifika konfigurationen lagras i `app/etc/env.php`som bör _not_ vara i källkontrollen.

Ange den systemspecifika konfigurationen i Admin i utvecklingssystemet (eller Adobe Commerce i molninfrastruktursintegreringen) och skriv konfigurationen till `env.php` med [`magento app:config:dump` kommando](../cli/export-configuration.md).

Det här kommandot skriver även känsliga inställningar till `env.php`.

### Hantera den känsliga konfigurationen

Den känsliga konfigurationen lagras också i `app/etc/env.php`.

Du kan hantera den känsliga konfigurationen på något av följande sätt:

- Miljövariabler
- Spara den känsliga konfigurationen i `env.php` i produktionssystemet med [`magento config:set:sensitive` kommando](../cli/set-configuration-values.md)

### Konfigurationsinställningarna är låsta i administratören

Alla konfigurationsinställningar i `config.php` eller `env.php` är låsta i administratören, det innebär att dessa inställningar inte kan ändras i Admin.
Använd [`magento config:set` eller `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) om du vill ändra inställningarna i `config.php` eller `env.php` filer.

## Commerce Admin

Admin visar följande beteende i produktionsläge:

- Du kan inte aktivera eller inaktivera cachetyper i Admin
- Inställningar för utvecklare är inte tillgängliga (**Lager** > Inställningar > **Konfiguration** > Avancerat > **Utvecklare**), inklusive:

   - Minska CSS, JavaScript och HTML
   - Sammanfoga CSS och JavaScript
   - LESS-kompilering på serversidan eller klientsidan
   - Textbundna översättningar
   - Som tidigare nämnts finns alla konfigurationsinställningar i `config.php` eller `env.php` är låst och kan inte redigeras i Admin.
   - Du kan bara ändra administratörens språkområde till språk som används av distribuerade teman

      I bilden nedan visas ett exempel på **Kontoinställning** > **Språk för gränssnitt** i Admin som endast visar två distribuerade språk:

      ![Du kan bara ändra administratörens språkområde till distribuerade språkområden](../../assets/configuration/split-deploy-admin-locale.png)

- Du kan inte ändra språkkonfigurationer för något omfång med Admin.

   Vi rekommenderar att du gör dessa ändringar innan du går över till produktionsläget.

   Du kan fortfarande konfigurera språkområdet med hjälp av systemvariabler eller `config:set` CLI-kommando med sökväg `general/locale/code`.

## Installera och ta bort cron

I version 2.2 för första gången hjälper vi dig att konfigurera ditt cron-jobb genom att tillhandahålla [`magento cron:install` kommando](../cli/configure-cron-jobs.md). Det här kommandot anger en crontab som användaren som kör kommandot.

Du kan även ta bort fliken crontab med `magento cron:remove` -kommando.

## Rekommenderat arbetsflöde för pipeline-distribution

I följande diagram visas hur vi rekommenderar att du använder pipeline-distribution för att hantera konfigurationen.

![Rekommenderat arbetsflöde för pipeline-distribution](../../assets/configuration/split-deploy-workflow.png)

### Utvecklingssystem

I utvecklingssystemet gör du konfigurationsändringar i Admin och genererar den delade konfigurationen, `app/etc/config.php` och systemspecifik konfiguration, `app/etc/env.php`. Kontrollera Commerce-koden och den delade konfigurationen i källkontrollen och skicka den till byggservern.

Du bör även installera tillägg och anpassa Commerce-kod i utvecklingssystemet.

I ditt utvecklingssystem:

1. Ange konfigurationen i Admin.

1. Använd `magento app:config:dump` för att skriva konfigurationen till filsystemet.

   - `app/etc/config.php` är den delade konfigurationen, som innehåller alla inställningar _utom_ känsliga och systemspecifika inställningar. Den här filen bör vara i källkontroll.
   - `app/etc/env.php` är den systemspecifika konfigurationen, som innehåller inställningar som är unika för ett visst system (till exempel värdnamn och portnummer). Den här filen bör _not_ vara i källkontrollen.

1. Lägg till den ändrade koden och den delade konfigurationen i källkontrollen.

1. Om du vill ta bort genererad PHP-kod och statiska resursfiler under utvecklingen kör du följande kommandon:

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

När du har kört kommandona för att rensa resurserna genererar Commerce arbetsfiler.

>[!WARNING]
>
>Var försiktig med ovanstående tillvägagångssätt. Ta bort `.htacces`som i `generated` eller `pub` kan orsaka problem.

### Bygg system

Build-systemet kompilerar kod och genererar statiska vyfiler för teman som är registrerade i Commerce. Den behöver inte vara ansluten till handelsdatabasen. behöver bara Commerce-kodbasen.

På ditt byggsystem:

1. Dra den delade konfigurationsfilen från källkontrollen.
1. Använd `magento setup:di:compile` för att kompilera kod.
1. Använd `magento setup:static-content:deploy -f` om du vill uppdatera statiska filvisningsfiler.
1. Kontrollera uppdateringarna i källkontrollen.

>[!INFO]
>
>Se [Distributionsstrategier för statiska vyfiler](../cli/static-view-file-strategy.md).

### Produktionssystem

I produktionssystemet (dvs. i livebutiken) hämtar du genererade resurser och koduppdateringar från källkontrollen och anger systemspecifika och känsliga konfigurationsinställningar med kommandoraden eller miljövariablerna.

I produktionssystemet:

1. Starta underhållsläge.
1. Hämta kod- och konfigurationsuppdateringar från källkontrollen.
1. Om du använder Adobe Commerce ska du stoppa köarbetarna.
1. Använd `magento app:config:import` för att importera konfigurationsändringar i produktionssystemet.
1. Om du har installerat komponenter som ändrat databasschemat kör du `magento setup:upgrade --keep-generated` för att uppdatera databasschemat och data och bevara genererade statiska filer.
1. Om du vill ange systemspecifika inställningar använder du antingen `magento config:set` kommando eller miljövariabler.
1. Om du vill ange känsliga inställningar använder du antingen `magento config:sensitive:set` kommando eller miljövariabler.
1. Rent (kallas även _flush_) cacheminnet.
1. Avsluta underhållsläge.

## Konfigurationshanteringskommandon

Vi tillhandahåller följande kommandon som hjälper dig att hantera konfigurationen:

- [`magento app:config:dump`](../cli/export-configuration.md) för att skriva administratörskonfigurationsinställningar till `config.php` och `env.php` (förutom för känsliga inställningar)
- [`magento config:set`](../cli/set-configuration-values.md) för att ange värden för systemspecifika inställningar i produktionssystemet.

   Använd det valfria `--lock` om du vill låsa alternativet i Admin (d.v.s. göra inställningen icke-redigerbar). Om en inställning redan är låst använder du `--lock` om du vill ändra inställningen.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) för att ange värden för känsliga inställningar i produktionssystemet.
- [`magento app:config:import`](../cli/import-configuration.md) för att importera konfigurationsändringar från `config.php` och `env.php` till produktionssystemet.

## Exempel på konfigurationshantering

I det här avsnittet visas exempel på hur du hanterar konfigurationen så att du kan se hur ändringar görs i `config.php` och `env.php`.

### Ändra standardspråk

I det här avsnittet visas ändringarna i `config.php` när du ändrar standardviktenheten med Admin (**Lager** > Inställningar > **Konfiguration** > Allmänt > **Allmänt** > **Nationella inställningar**).

När du har gjort ändringen i Admin ska du köra `bin/magento app:config:dump` att skriva värdet till `config.php`. Värdet skrivs till `general` array under `locale` som följande utdrag från `config.php` visar:

```php
'general' =>
    array (
        'locale' =>
        array (
            'code' => 'en_US',
            'timezone' => 'America/Chicago',
            'weight_unit' => 'kgs'
        )
    )
```

### Ändra flera konfigurationsinställningar

I det här avsnittet beskrivs hur du gör följande konfigurationsändringar:

- Lägga till en webbplats-, butik- och butiksvy (**Lager** > Inställningar > **Alla butiker**)
- Ändra standarddomänen för e-post (**Lager** > Inställningar > **Konfiguration** > Kunder > **Kundkonfiguration**)
- Ange användarnamn och API-lösenord för PayPal-API (**Lager** > Inställningar > **Konfiguration** > Försäljning > **Betalningsmetoder** > **PayPal** > **Nödvändiga PayPal-inställningar**)

När du har gjort ändringen i Admin ska du köra `bin/magento app:config:dump` i ditt utvecklingssystem. Nu skrivs inte alla ändringar `config.php`; Faktum är att det bara är webbplatsvyn, butiksvyn och butiksvyn som skrivs till den filen som följande utdrag visar.

### config.php

`config.php` innehåller:

- Ändringar av webbplatsen, butiken och butiksvyn.
- Icke-systemspecifika sökmotorinställningar
- Icke-känsliga PayPal-inställningar
- Kommentarer som informerar dig om känsliga inställningar som har utelämnats från `config.php`

`websites` array:

```php
      'new' =>
      array (
        'website_id' => '2',
        'code' => 'new',
        'name' => 'New website',
        'sort_order' => '0',
        'default_group_id' => '2',
        'is_default' => '0',
      ),
```

`groups` array:

```php
      2 =>
      array (
        'group_id' => '2',
        'website_id' => '2',
        'code' => 'newstore',
        'name' => 'New store',
        'root_category_id' => '2',
        'default_store_id' => '2',
      ),
```

`stores` array:

```php
     'newview' =>
      array (
        'store_id' => '2',
        'code' => 'newview',
        'website_id' => '2',
        'group_id' => '2',
        'name' => 'New store view',
        'sort_order' => '0',
        'is_active' => '1',
      ),
```

`payment` array:

```php
      'payment' =>
      array (
        'paypal_express' =>
        array (
          'active' => '0',
          'in_context' => '0',
          'title' => 'PayPal Express Checkout',
          'sort_order' => NULL,
          'payment_action' => 'Authorization',
          'visible_on_product' => '1',
          'visible_on_cart' => '1',
          'allowspecific' => '0',
          'verify_peer' => '1',
          'line_items_enabled' => '1',
          'transfer_shipping_options' => '0',
          'solution_type' => 'Mark',
          'require_billing_address' => '0',
          'allow_ba_signup' => 'never',
          'skip_order_review_step' => '1',
        ),
```

### env.php

Den standardinställda systemspecifika konfigurationsinställningen för e-postdomänen skrivs till `app/etc/env.php`.

PayPal-inställningarna skrivs till ingen av filerna eftersom `bin/magento app:config:dump` -kommandot skriver inte känsliga inställningar. Du måste ange PayPal-inställningarna i produktionssystemet med följande kommandon:

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
