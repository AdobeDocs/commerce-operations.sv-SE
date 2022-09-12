---
title: Hantera cacheminnet
description: Hantera cachetyper och visa cachestatus.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---


# Hantera cacheminnet

{{file-system-owner}}

## Cachetyper

Commerce 2 har följande cachetyper:

| Eget namn för cachetyp | Namn på cachetypkod | Beskrivning |
|--- |--- |--- |
| Konfiguration | config | Commerce samlar in konfiguration från alla moduler, sammanfogar den och sparar det sammanfogade resultatet i cachen. Cachen innehåller även lagringsinställningar som lagras i filsystemet och databasen. Rensa eller tömma den här cachetypen efter att konfigurationsfilerna har ändrats. |
| Layout | layout | Kompilerade sidlayouter (d.v.s. layoutkomponenter från alla komponenter). Rensa eller tömma den här cachetypen efter att du har ändrat layoutfiler. |
| Blockera utdata för HTML | block_html | HTML sidfragment per block. Rengör eller tömma den här cachetypen efter att du har ändrat visningslagret. |
| Samlingsdata | samlingar | Resultat av databasfrågor. Om det behövs rensar Commerce cachen automatiskt, men tredjepartsutvecklare kan placera alla data i valfritt segment i cachen. Rensa eller tömma den här cachetypen om den anpassade modulen använder logik som resulterar i cacheposter som inte kan rensas. |
| DDL | db_ddl | Databasschema. Om det behövs rensar Commerce cachen automatiskt, men tredjepartsutvecklare kan placera alla data i valfritt segment i cachen. Rensa eller tömma den här cachetypen efter att du har gjort anpassade ändringar i databasschemat. (Med andra ord, uppdateringar som Commerce inte gör sig själv.) Ett sätt att uppdatera databasschemat automatiskt är att använda `magento setup:db-schema:upgrade` -kommando. |
| Kompilerad konfiguration | compiled_config | Kompileringskonfiguration |
| Entity attribute value (EAV) | eav | Metadata relaterade till EAV-attribut (t.ex. butiksetiketter, länkar till relaterad PHP-kod, attributåtergivning, sökinställningar osv.). Vanligtvis behöver du inte rensa eller tömma den här cachetypen. |
| Sidcache | full_page | Skapade HTML-sidor. Om det behövs rensar Commerce cachen automatiskt, men tredjepartsutvecklare kan placera alla data i valfritt segment i cachen. Rensa eller tömma den här cachetypen efter att du har ändrat kodnivån som påverkar utdata från HTML. Vi rekommenderar att du låter cacheminnet vara aktiverat eftersom cachelagring i HTML förbättrar prestandan avsevärt. |
| Reflektion | reflektion | Tar bort ett beroende mellan Webapi-modulen och kundmodulen. |
| Översättningar | translate | När översättningar från alla moduler har sammanfogats rensas sammanslagningscachen. |
| Integrationskonfiguration | config_integration | Kompilerade integreringar. Rensa eller tömma det här cacheminnet när du har ändrat eller lagt till integreringar. |
| API-konfiguration för integrering | config_integration_api | Kompilerade API:er för integrering av butikens integreringar. |
| Konfiguration av webbtjänster | config_webservice | Cachelagra webb-API-strukturen. |
| Kundmeddelande | customer_notification | Tillfälliga meddelanden som visas i användargränssnittet. |

## Visa cachestatus

Om du vill visa cachestatus anger du

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

Ett exempel följer:

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
                           eav: 1
         customer_notification: 1
                     full_page: 1
            config_integration: 1
        config_integration_api: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

## Aktivera eller inaktivera cachetyper

Med det här kommandot kan du aktivera eller inaktivera alla cachetyper eller endast de som du anger. Det är praktiskt att inaktivera cachetyper under utvecklingen eftersom du ser resultatet av ändringarna utan att behöva tömma cachen. Att inaktivera cachetyper påverkar dock prestandan negativt.

>[!INFO]
>
>Från och med version 2.2 kan du bara aktivera eller inaktivera cachetyper med kommandoraden när du kör Commerce i produktionsläge. Om du kör Commerce i utvecklarläge kan du aktivera eller inaktivera cachetyper med kommandoraden eller manuellt. Innan du gör det måste du göra `<magento_root>/app/etc/env.php` skrivbar av [ägare av filsystem](../../installation/prerequisites/file-system/overview.md).

Du kan rengöra (kallas även _flush_ eller _uppdatera_) cachetyper med antingen kommandoraden eller administratören.

Kommandoalternativ:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Om utelämnande `[type]` aktiverar eller inaktiverar alla cachetyper samtidigt. The `type` är en blankstegsavgränsad lista med cachetyper.

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

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>Om du aktiverar en cachetyp rensas cachetypen automatiskt.

>[!INFO]
>
>Från och med version 2.3.4 cachelagrar Commerce alla EAV-attribut i systemet när de hämtas. Cachelagring av EAV-attribut på det här sättet förbättrar prestandan eftersom det minskar mängden insert/select-begäranden till databasen. Men även cachens nätverksstorlek ökar. Utvecklare kan cachelagra anpassade EAV-attribut genom att köra `bin/magento config:set dev/caching/cache_user_defined_attributes 1` -kommando. Detta kan även göras från administratören när du [Utvecklarläge](../bootstrap/application-modes.md) efter inställning **Lager** > Inställningar **Konfiguration** > **Avancerat** > **Utvecklare** > **Inställningar för cachelagring** > **Cachelagra användardefinierade attribut** till **Ja**.

## Rensa och tömma cachetyper

Om du vill ta bort inaktuella objekt från cacheminnet kan du _ren_ eller _flush_ cachetyper:

- Om du rensar en cachetyp tas endast alla objekt bort från de aktiverade Commerce-cachetyperna. Det här alternativet påverkar alltså inte andra processer eller program eftersom det bara rensar den cache som används i Commerce.

   Inaktiverade cachetyper rensas inte.

   >[!TIP]
   >
   >Rensa alltid cacheminnet efter att du uppgraderat versioner av Magento Open Source eller Adobe Commerce, uppgraderat från Magento Open Source till Adobe Commerce eller installerat B2B för Adobe Commerce eller någon modul.

- När du tömmer en cachetyp rensas cachelagringen, vilket kan påverka andra processer som använder samma lagring.

Rensa cachetyper om du redan har försökt rensa cachen och fortfarande har problem som du inte kan isolera.

Kommandoanvändning:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Plats `[type]` är en blankstegsavgränsad lista med cachetyper. Utelämnar `[type]` rensar eller tömmer alla cachetyper samtidigt. Om du till exempel vill tömma alla cachetyper anger du

```bash
   bin/magento cache:flush
```

Exempelresultat:

```terminal
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
   config_webservice
   translate
```

>[!TIP]
>
>Du kan även rensa och tömma cachetyper i Admin. Gå till **System** > **verktyg** > **Cachehantering**. **Lagring av tömningscache** motsvarar `bin/magento cache:flush`. **Rensa Magento-cache** motsvarar `bin/magento cache:clean`.
