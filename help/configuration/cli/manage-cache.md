---
title: Hantera cachen
description: Hantera cachetyper och visa cachestatus från kommandoraden med Commerce CLI
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Hantera cachen

{{file-system-owner}}

## Cache-typer

Du kan använda Adobe Commerce cachehanteringssystem för att förbättra prestanda för din plats. I det här avsnittet beskrivs hur systemadministratörer och utvecklare med åtkomst till Commerce programserver kan hantera cacheminnen från kommandoraden.

>[!NOTE]
>
>
>Administratörer för företagswebbplatser kan hantera cacheminnet från administratören med hjälp av verktyget Cachehanteringssystem. Se [Cachehantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) i _handboken för administratörssystem_.


## Visa cachestatus

På kommandoraden för Commerce-programservern kan du visa status för cachen med hjälp av Commerce CLI-kommandot `cache:status`.

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

Ett exempel följer:

```
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
             webhooks_response: 1
                           eav: 1
         customer_notification: 1
 graphql_query_resolver_result: 1
            config_integration: 1
        config_integration_api: 1
                  admin_ui_sdk: 1
                     full_page: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

>[!TIP]
>
>En detaljerad beskrivning av de standardcachetyper som stöds av Adobe Commerce finns i [Caches](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#caches) i _Admin Systems Guide_.


## Aktivera eller inaktivera cachetyper

Med det här kommandot kan du aktivera eller inaktivera alla cachetyper eller endast de som du anger. Att inaktivera cachetyper är användbart under utvecklingen eftersom du ser resultatet av dina ändringar utan att behöva tömma cachen. Inaktivering av cachetyper kan dock påverka prestandan negativt.

>[!INFO]
>
>Från och med version 2.2 kan du bara aktivera eller inaktivera cachetyper med kommandoraden när du kör Commerce i produktionsläge. Om du kör Commerce i utvecklarläge kan du aktivera eller inaktivera cachetyper med kommandoraden eller manuellt. Innan du gör det måste du manuellt göra `<magento_root>/app/etc/env.php` skrivbar av [filsystemets ägare](../../installation/prerequisites/file-system/overview.md).

Du kan rensa (kallas även _flush_ eller _refresh_) cachetyper med kommandoraden eller Admin.

Kommandoalternativ:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Om `[type]` utelämnas aktiveras eller inaktiveras alla cachetyper samtidigt. Alternativet `type` är en blankstegsavgränsad lista med cachetyper.

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

Så här visar du cachetyper och deras status:

```bash
bin/magento cache:status
```

Så här inaktiverar du helsidescachen och DDL-cachen:

```bash
bin/magento cache:disable db_ddl full_page
```

Exempelresultat:

```
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>Om du aktiverar en cachetyp rensas cachetypen automatiskt.

>[!INFO]
>
>Från och med version 2.3.4 sparar Commerce alla EAV-attribut i systemet när de hämtas. Cachelagring av EAV-attribut på det här sättet förbättrar prestandan eftersom det minskar mängden insert/select-begäranden till databasen. Men även cachens nätverksstorlek ökar. Utvecklare kan cachelagra anpassade EAV-attribut genom att köra kommandot `bin/magento config:set dev/caching/cache_user_defined_attributes 1`. Detta kan även göras från administratören i [utvecklarläget](../bootstrap/application-modes.md) genom att ställa in **Lager** > Inställningar **Konfiguration** > **Avancerat** > **Utvecklare** > **Cachelagringsinställningar** > **Cachelagra användardefinierade attribut** på **Ja**.

## Rensa och tömma cachetyper

>[!NOTE]
>
>Cacheminnet för flera sidor kan ogiltigförklaras samtidigt och automatiskt **_utan_** redigering av dessa entiteter. Till exempel när en produkt i katalogen har tilldelats en kategori eller när någon [!UICONTROL related product rule] har ändrats.

Om du vill rensa inaktuella objekt från cacheminnet kan du _rensa_ eller _tömma_ cachetyper:

- Om du rensar en cachetyp tas endast alla objekt bort från de aktiverade cachetyperna i Commerce. Det här alternativet påverkar alltså inte andra processer eller program eftersom det bara rensar den cache som används i Commerce.

  Inaktiverade cachetyper rensas inte.

  >[!TIP]
  >
  >Rensa alltid cacheminnet när du har uppgraderat versioner av Adobe Commerce, uppgraderat från Magento Open Source till Adobe Commerce eller installerat B2B för Adobe Commerce eller någon modul.

- När du tömmer en cachetyp rensas cachelagringen, vilket kan påverka andra processer som använder samma lagring.

Rensa cachetyper om du redan har försökt rensa cachen och fortfarande har problem som du inte kan isolera.

Kommandoanvändning:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Där `[type]` är en blankstegsavgränsad lista med cachetyper. Om `[type]` utelämnas rensas eller rensas alla cachetyper samtidigt. Om du till exempel vill tömma alla cachetyper anger du

```bash
   bin/magento cache:flush
```

Exempelresultat:

```
   Flushed cache types:
   config
   layout
   block_html
   collections
   reflection
   db_ddl
   compiled_config
   eav
   customer_notification
   config_integration
   config_integration_api
   full_page
   graphql_query_resolver_results
   config_webservice
   translate
```

>[!TIP]
>
>Du kan även rensa och tömma cachetyper i Admin. Gå till **System** > **Verktyg** > **Cachehantering**. **Lagring av rensningscache** motsvarar `bin/magento cache:flush`. **Töm Magento-cache** motsvarar `bin/magento cache:clean`.
