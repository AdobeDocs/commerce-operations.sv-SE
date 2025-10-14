---
title: Teknisk information
description: Läs om teknisk information om distribution av pipeline, olika konfigurationstyper och rekommenderade arbetsflöden.
exl-id: a396d241-f895-4414-92af-3abf3511e62a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# Teknisk information

Det här avsnittet handlar om teknisk implementeringsinformation om pipeline-distribution i Commerce 2.2 och senare. Förbättringar kan delas in i följande områden:

- [Konfigurationshantering](#configuration-management)
- [Ändringar i administratören](#changes-in-the-admin)
- [Installera och ta bort cron](#install-and-remove-cron)

I det här avsnittet beskrivs även det [rekommenderade arbetsflödet](#recommended-workflow) för pipeline-distribution och några exempel som hjälper dig förstå hur det fungerar.

Granska [Förutsättningarna för ditt utvecklings-, bygg- och produktionssystem](../deployment/prerequisites.md) innan du börjar.

## Konfigurationshantering

Använd följande åsidosättningsschema om du vill synkronisera och underhålla konfigurationen för dina utvecklings- och produktionssystem.

![Hur konfigurationsvariabelvärden bestäms](../../assets/configuration/override-flow-diagram.png)

Som diagrammet visar används konfigurationsvärdena i följande ordning:

1. Miljövariabler åsidosätter alla andra värden, om de finns.
1. Från de delade konfigurationsfilerna `env.php` och `config.php`. Värden i `env.php` åsidosätter värden i `config.php`.
1. Från värden som lagras i databasen.
1. Om det inte finns något värde i någon av dessa källor används standardvärdet eller NULL.

### Hantera den delade konfigurationen

Den delade konfigurationen lagras i `app/etc/config.php`, som ska vara i källkontrollen.

Ange den delade konfigurationen i Admin i utvecklingssystemet (eller Adobe Commerce i molninfrastruktursystemet _integration_) och skriv konfigurationen till `config.php` med [`magento app:config:dump` command](../cli/export-configuration.md) .

### Hantera den systemspecifika konfigurationen

Den systemspecifika konfigurationen lagras i `app/etc/env.php`, som _inte_ ska finnas i källkontrollen.

Ange den systemspecifika konfigurationen i Admin i utvecklingssystemet (eller Adobe Commerce i molninfrastruktursintegreringen) och skriv konfigurationen till `env.php` med [`magento app:config:dump` command](../cli/export-configuration.md).

Det här kommandot skriver även känsliga inställningar till `env.php`.

### Hantera den känsliga konfigurationen

Den känsliga konfigurationen lagras också i `app/etc/env.php`.

Du kan hantera den känsliga konfigurationen på något av följande sätt:

- Miljövariabler
- Spara den känsliga konfigurationen i `env.php` i produktionssystemet med hjälp av kommandot [`magento config:set:sensitive` &#x200B;](../cli/set-configuration-values.md)

### Konfigurationsinställningarna är låsta i administratören

Alla konfigurationsinställningar i `config.php` eller `env.php` är låsta i Admin, vilket innebär att dessa inställningar inte kan ändras i Admin.
Använd kommandot [`magento config:set` eller `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) om du vill ändra inställningarna i `config.php`- eller `env.php`-filerna.

## Commerce Admin

Admin visar följande beteende i produktionsläge:

- Du kan inte aktivera eller inaktivera cachetyper i Admin
- Utvecklarinställningarna är inte tillgängliga (**Store** > Inställningar > **Konfiguration** > Avancerat > **Utvecklare**), inklusive:

   - Minify CSS, JavaScript och HTML
   - Slå samman CSS och JavaScript
   - LESS-kompilering på serversidan eller klientsidan
   - Textbundna översättningar
   - Som tidigare nämnts är alla konfigurationsinställningar i `config.php` eller `env.php` låsta och kan inte redigeras i administratören.
   - Du kan bara ändra administratörens språkområde till språk som används av distribuerade teman

     I följande bild visas ett exempel på listan **Kontoinställning** > **Språkinställning för gränssnitt** i Admin som endast visar två distribuerade språkinställningar:

     ![Du kan bara ändra administratörens språkområde till distribuerade språkområden](../../assets/configuration/split-deploy-admin-locale.png)

- Du kan inte ändra språkkonfigurationer för något omfång med Admin.

  Vi rekommenderar att du gör dessa ändringar innan du går över till produktionsläget.

  Du kan fortfarande konfigurera språkområdet med hjälp av miljövariabler eller CLI-kommandot `config:set` med sökvägen `general/locale/code`.

## Installera och ta bort cron

I version 2.2 för första gången hjälper vi dig att konfigurera ditt cron-jobb genom att ange [`magento cron:install`-kommandot &#x200B;](../cli/configure-cron-jobs.md). Det här kommandot anger en crontab som användaren som kör kommandot.

Du kan även ta bort crontab med kommandot `magento cron:remove`.

## Rekommenderat arbetsflöde för pipeline-distribution

I följande diagram visas hur vi rekommenderar att du använder pipeline-distribution för att hantera konfigurationen.

![Rekommenderat arbetsflöde för pipeline-distribution](../../assets/configuration/split-deploy-workflow.png)

### Utvecklingssystem

I utvecklingssystemet gör du konfigurationsändringar i Admin och genererar den delade konfigurationen `app/etc/config.php` och den systemspecifika konfigurationen `app/etc/env.php`. Kontrollera Commerce-koden och den delade konfigurationen i källkontrollen och skicka den till byggservern.

Du bör också installera tillägg och anpassa Commerce-kod i utvecklingssystemet.

I ditt utvecklingssystem:

1. Ange konfigurationen i Admin.

1. Använd kommandot `magento app:config:dump` för att skriva konfigurationen till filsystemet.

   - `app/etc/config.php` är den delade konfigurationen, som innehåller alla inställningar _utom_, känsliga och systemspecifika inställningar. Den här filen bör vara i källkontroll.
   - `app/etc/env.php` är den systemspecifika konfigurationen, som innehåller inställningar som är unika för ett visst system (till exempel värdnamn och portnummer). Filen ska _inte_ finnas i källkontrollen.

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
>Var försiktig med ovanstående tillvägagångssätt. Om du tar bort filen `.htacces` i mappen `generated` eller `pub` kan det orsaka problem.

### Bygg system

Build-systemet kompilerar kod och genererar statiska visningsfiler för teman som är registrerade i Commerce. Den behöver ingen anslutning till Commerce-databasen, den behöver bara Commerce-kodbas.

På ditt byggsystem:

1. Dra den delade konfigurationsfilen från källkontrollen.
1. Använd kommandot `magento setup:di:compile` för att kompilera kod.
1. Använd kommandot `magento setup:static-content:deploy -f` för att uppdatera statiska filvisningsfiler.
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
1. Använd kommandot `magento app:config:import` om du vill importera konfigurationsändringar i produktionssystemet.
1. Om du har installerat komponenter som ändrat databasschemat kör du `magento setup:upgrade --keep-generated` för att uppdatera databasschemat och data och bevarar genererade statiska filer.
1. Om du vill ange systemspecifika inställningar använder du kommandot `magento config:set` eller miljövariablerna.
1. Om du vill ange känsliga inställningar använder du kommandot `magento config:sensitive:set` eller miljövariablerna.
1. Rengör (kallas även _flush_) cachen.
1. Avsluta underhållsläge.

## Konfigurationshanteringskommandon

Vi tillhandahåller följande kommandon som hjälper dig att hantera konfigurationen:

- [`magento app:config:dump`](../cli/export-configuration.md) för att skriva administratörskonfigurationsinställningar till `config.php` och `env.php` (förutom för känsliga inställningar)
- [`magento config:set`](../cli/set-configuration-values.md) om du vill ange värden för systemspecifika inställningar i produktionssystemet.

  Använd det valfria alternativet `--lock` för att låsa alternativet i Admin (d.v.s. göra inställningen icke-redigerbar). Om en inställning redan är låst använder du alternativet `--lock` för att ändra inställningen.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) om du vill ange värden för känsliga inställningar i produktionssystemet.
- [`magento app:config:import`](../cli/import-configuration.md) om du vill importera konfigurationsändringar från `config.php` och `env.php` till produktionssystemet.

## Exempel på konfigurationshantering

I det här avsnittet visas exempel på hur du hanterar konfigurationen så att du kan se hur ändringar görs i `config.php` och `env.php`.

### Ändra standardspråk

I det här avsnittet visas ändringen som gjorts i `config.php` när du ändrar standardviktenheten med Admin (**Lagrar** > Inställningar > **Konfiguration** > Allmänt > **Allmänt** > **Språkalternativ**).

När du har gjort ändringen i Admin kör du `bin/magento app:config:dump` för att skriva värdet till `config.php`. Värdet skrivs till `general`-arrayen under `locale`, vilket visas i följande utdrag från `config.php`:

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

- Lägga till en webbplats-, butik- och butiksvy (**Lagrar** > Inställningar > **Alla butiker**)
- Ändra standarddomänen för e-post (**Lagrar** > Inställningar > **Konfiguration** > Kunder > **Kundkonfiguration**)
- Anger användarnamn och API-lösenord för PayPal-API (**Lagrar** > Inställningar > **Konfiguration** > Försäljning > **Betalningsmetoder** > **PayPal** > **Nödvändiga PayPal-inställningar**)

När du har gjort ändringen i Admin kör du `bin/magento app:config:dump` på utvecklingssystemet. Den här gången skrivs inte alla ändringar till `config.php`. Det är faktiskt bara webbplatsvyn, butiksvyn och butiksvyn som skrivs till den filen som följande utdrag visar.

### config.php

`config.php` innehåller:

- Ändringar av webbplatsen, butiken och butiksvyn.
- Icke-systemspecifika sökmotorinställningar
- Icke-känsliga PayPal-inställningar
- Kommentarer som informerar dig om känsliga inställningar som har utelämnats från `config.php`

`websites`-matris:

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

`groups`-matris:

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

`stores`-matris:

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

`payment`-matris:

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

Standardinställningen för systemspecifik konfiguration för e-postdomän har skrivits till `app/etc/env.php`.

PayPal-inställningarna skrivs till ingen av filerna eftersom kommandot `bin/magento app:config:dump` inte skriver känsliga inställningar. Du måste ange PayPal-inställningarna i produktionssystemet med följande kommandon:

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
