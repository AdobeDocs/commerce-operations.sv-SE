---
title: "Den [!UICONTROL Deploy] tab"
description: Läs mer om [!UICONTROL Deploy] flik för [!DNL Observation for Adobe Commerce].
source-git-commit: b95a35ee64cd8e844a51a9ff699eceb9c3a9266c
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 0%

---

# The [!UICONTROL Deploy] tab

Fliken är ett försök att snabbt isolera problem och orsaker till distributionsproblem.

## [!UICONTROL Deploy log Deployment Troubleshooter]

![Felsökare för distribution av logg](../../assets/tools/observation-for-adobe-commerce/deploy-tab-1.jpg)

The **[!UICONTROL Deploy log Deployment Troubleshooter]** bildrutan visar antalet distribuerade logghändelser som inträffade under den valda tidsbildrutan. Avsikten är att ge en överblick över distributionsaktiviteten och avgöra hur komplicerad distributionen är utifrån antalet. Ju mer loggade meddelanden, desto mer komplicerad är distributionen vanligtvis.

## [!UICONTROL Deploy State]

![Distribuera tillstånd](../../assets/tools/observation-for-adobe-commerce/deploy-tab-2.jpg)

The **[!UICONTROL Deploy State]** bildrutan visar de distributionshändelser som inträffade under den valda tidsramen. Tolkaren för den här bildrutan söker efter dessa specifika signaler:

* &#39;%OBS! Börja generera kommando%) som start_gen
* &#39;%git apply /app/vendor/magento/ece-tools/patches%&#39;) as &#39;apply_patches&#39;
* &#39;%Set flag: .static_content_deploy%) som SCD
* &#39;%OBS! Genereringskommandot slutfördes%) som gen_compl
* &#39;%OBS! Startar distributionen.%) som start_deploy
* &#39;%OBS! Distributionen slutfördes i %) som deploy_compl
* &#39;%OBS! Startar postdistribution.%) som start_pdeploy
* &#39;%OBS! Efterdistributionen är slutförd (%) som &#39;pdeploy&#39;
* %deploy-complete%) som cl_deploy_compl

## [!UICONTROL Deploy Log Detail]

![Distribuera logginformation](../../assets/tools/observation-for-adobe-commerce/deploy-tab-3.jpg)

The **[!UICONTROL Deploy Log Detail]** bildrutan visar sammanfattningsinformation för distributionsloggmeddelanden som inträffade under den valda tidsramen. Bildrutan tolkas för följande strängar i distributionsloggarna:

* &#39;%OBS! Startar distributionen.%) som start_dply
* &#39;%INFO: Startscenario(n): scenario/deploy.xml%) som start_scenario
* &#39;%OBS! Startar pre-deploy%) som start_predply
* &#39;% INFO: Återställer korrigeringsloggfilen %) som rstr_ptch_log
* &#39;%INFO: Uppdaterar cachekonfigurationen.%&#39;) as &#39;updt_cach_config&#39;
* &#39;%INFO: Ange Redis-slavanslutning (%) som redis_sec_conn_set
* &#39;%INFO: Distribuering av statiskt innehåll utfördes under byggkrok, rensa gammalt innehåll (%) som scd_build_hk
* &#39;%INFO: Rensa pub/static%) som clr_pub_static
* &#39;%NFO: Rensar Redis-cache:%) som clr_redis_cach
* &#39;%INFO: Rensar var/cache-katalogen%) som clr_var_cach
* &#39;% MEDDELANDE: Aktivera underhållsläget %) som enable_maint_mode
* &#39;%INFO: Inaktivera cron%) som disable_cron
* &#39;%INFO: Försöker döda körda cron-jobb och konsumentprocesser (%) som &#39;Kill_cron_try&#39;
* &#39;%INFO: Det gick inte att hitta Magento cron och konsumentprocesser.%&#39;) som no_cron_fnd,
* %OBS! Validerar konfiguration (%) som validate_config
* &#39;%Följande admindata krävs för att skapa en adminanvändare under den första installationen%&#39;) som &#39;no_admin&#39;
* &#39;%rekommenderad PHP-version som uppfyller villkoret%&#39;) som &#39;php_ver_constraint&#39;
* &#39;%VARNING! Korrigera konfigurationen med givna förslag:%) som fix_config_sugg
* &#39;%VARNING! [2003] Värdet för katalogkapslingsnivån för felrapportering har inte konfigurerats.%&#39;) as&#39;nest_err_reporting&#39;
* &#39;%OBS! End of validation%&#39;) as &#39;end_validation&#39;
* &#39;%OBS! Startar uppdatering.%) som start_update
* &#39;%INFO: Uppdaterar env.php.%) som update_php_env
* &#39;%INFO: Uppdaterar konfigurationen för env.php DB-anslutningen.%) som update_php_env_db
* &#39;%INFO: Uppdaterar env.php AMQP configuration%) as &#39;update_php_env_amqp&#39;
* &#39;%INFO: Ställ in sökmotorn på: elasticsearch7%) as &#39;set_elastic7&#39;
* %elasticsearch 6.5.4 har klarat EOL%) som elastic_ver_EOL
* &#39;%INFO: Ställ in sökmotorn på: elasticsearch6%) as &#39;set_elastic6&#39;
* &#39;%INFO: Uppdaterar säkra och osäkra URL:er (%) som update_urls
* &#39;%INFO: Installationsuppgradering körs.%) som setup_upgrade_run
* &#39;%INFO: Krok efter distribution aktiverad. Kronaktivering, cacherengöring och förvärvningsåtgärder skjuts upp (%) som post_krok_enabled
* &#39;%OBS! Underhållsläget är inaktiverat.%&#39;) as &#39;maint_mode_disabled&#39;
* &#39;%INFO: Scenario(er) klar%&#39;) som &#39;scenario_färdigt&#39;
* &#39;%VARNING! Kommandounderhåll:aktivera slutfört med ett fel. Skapa en underhålls-eflag (%&#39;) som&#39;enable_Maintenance_fails&#39;
* %MySQL-servern har gått bort%) som MySQL_has_away

## [!UICONTROL Post Deploy Log Detail]

![Loggdetaljer för postdistribution](../../assets/tools/observation-for-adobe-commerce/deploy-tab-4.jpg)

The **[!UICONTROL Post Deploy Log Detail]** bildrutan visar logginformation som har inträffat efter distributionen under den valda tidsramen. Den här bildrutan fokuserar på särskilda loggmeddelanden som innehåller följande strängar:

* %Disabled Maintenance mode%) as &#39;disabled_maint_mode&#39;
* &#39;%INFO: Startscenario(n): scenario/post-deploy.xml%) as &#39;start_pstdply_scenario&#39;
* &#39;% MEDDELANDE: Verifierar konfiguration%) som val_config
* &#39;% MEDDELANDE: End of validation%&#39;) as &#39;end_val_config&#39;
* &#39;%INFO: Aktivera cron%) som cron_enabled
* &#39;% INFO: Skapa säkerhetskopiering av viktiga filer.%) som file_backup
* &#39;%INFO: Säkerhetskopiering (%) har skapats som &#39;file_backup_success&#39;
* &#39;%INFO: Startar siduppvärmning (%) som pg_warmup_start
* &#39;%INFO: Uppvärmd sida:%) som warmed_up_pg
* &#39;%ERROR: Uppvärmningen misslyckades:%) som varmt_upp_pg_err
* &#39;% INFO: Scenario(er) klar%&#39;) som &#39;scenario_färdigt&#39;

## [!UICONTROL Cloud Log Detail]

![Information om molnlogg](../../assets/tools/observation-for-adobe-commerce/deploy-tab-5.jpg)

The **[!UICONTROL Cloud Log Detail]** bildrutan visar information om molnloggen som inträffade under den valda tidsramen. Följande strängar tolkas och returneras med AS-etiketten nedan:

* &#39;%DEBUG: /bin/bash -c &quot;set -o pipefail; php ./bin/magento setup:upgrade%) as &#39;start_update&#39;
* &#39;%Schema creation/updates:%&#39;) as &#39;schema_updates&#39;
* &#39;%Ingenting att importera.%&#39;) som mod_import_finish
* &#39;%OBS! Uppdateringen är klar.%) som update_completed
* &#39;%DEBUG: Körningssteg: deploy-static-content%) as &#39;scd_run&#39;
* &#39;% MEDDELANDE: Hoppar över statisk innehållsdistribution. SCD on demand är aktiverat.%&#39;) som scd_ondemand
* &#39;%INFO: Clear%&#39;) as&#39;clr_dirs&#39;
* &#39;%DEBUG: Steg&quot;deploy-static-content&quot; finish%&quot;) som&quot;scd_finish&quot;
* &#39;%OBS! Hoppar över statisk innehållskomprimering. SCD on demand är aktiverat.%&#39;) som scd_compression_run,
* &#39;%INFO: Rensar var/cache-katalogen%) som clr_var_cach
* &#39;%DEBUG: Steg &quot;compress-static-content&quot; finish%&quot;) som &quot;scd_compression_complete&quot;
* &#39;%DEBUG: Körningssteg: deploy-complete%) as &#39;deploy_complete&#39;
* &#39;%INFO: Krok efter distribution aktiverad. Kronaktivering, cacherengöring och åtgärder före uppvärmning skjuts upp till steget efter driftsättningen.%) som Post_deploy_krok_enabled
* &#39;%OBS! Underhållsläget är inaktiverat.%&#39;) as &#39;maint_mode_disabled&#39;
* &#39;%INFO: Scenario(er) klar%&#39;) som &#39;scenario_färdigt&#39;
* %post-deploy.xml%) som post_deploy_start
* &#39;%OBS! Validerar konfiguration (%) som validate_config
* &#39;%VARNING! [2003] Värdet för katalogkapslingsnivån för felrapportering har inte konfigurerats.%&#39;) as&#39;nest_err_reporting&#39;
* &#39;%OBS! End of validation%&#39;) as &#39;end_validation&#39;
* &#39;%INFO: Aktivera cron%) som enable_cron
* &#39;%INFO: Skapa säkerhetskopia av viktiga filer (%) som &#39;create_backup&#39;
* &#39;%DEBUG: Steg &quot;backup&quot; klar%&quot;) som &#39;backup_completed&#39;
* &#39;%INFO: Startar siduppvärmning (%) som &#39;warmup_start&#39;
* &#39;%ERROR: Uppvärmningen misslyckades:%) som&quot;heat_up_fails&quot;
* &#39;%DEBUG: Steg&quot;uppvärmning&quot; slutförd%) som &#39;warmup_finish&#39;
* &#39;% DEBUG: Stega&quot;time-to-first-byte&quot; (slutförd%) som&quot;tfb_finish&quot;
* &#39;%INFO: Scenario(er) klar%&#39;) som post_deploy_finish&#39;
* &#39;%DEBUG: Körningssteg: pre-build%) as &#39;run_pre-build&#39;
* &#39;%DEBUG: Flagga .static_content_deploy har redan tagits bort%) som scd_flag_del
* &#39;%DEBUG: Steg&quot;pre-build&quot; klar%&quot;) som&quot;pre-build_completed&quot;
* &#39;%OBS! Tillämpar patchar%) som apply_patches
* &#39;%har tillämpats%&#39;) som &#39;patches_applied&#39;
* &#39;%DEBUG: Steg &quot;apply-patches&quot; finish%&quot;) som &#39;apply_patches_complete&#39;
* &#39;%Distribuera med snabbstrategi%&#39;) som &#39;quick_strategy_deploy&#39;
* &#39;% MEDDELANDE: Kör DI-kompilering (%) som &#39;di_compliation_start&#39;
* &#39;%OBS! Slut på DI-kompilering (%) som &#39;di_compliation_complete&#39;
* &#39;%OBS! Genererar nytt statiskt innehåll (%) som gen_frsh_static_content
* &#39;%magento setup:static-content:distribuera%) som scd_exekvering
* &#39;%OBS! Slut på att generera nytt statiskt innehåll (%) som &#39;gen_frsh_static_cont_finish&#39;
* &#39;%INFO: Startscenario(n): scenario/build/transfer.xml%) as &#39;start_transferxml&#39;
* &#39;%INFO: Försöker avsluta körda cron-jobb (%) som &#39;klart_crons&#39;
* &#39;%INFO: Rensar Redis-cache:%) som clear_redis_cache
* &#39;%INFO: Kontrollera om db finns och hastables%&#39;) som db_check
* &#39;%VARNING! [2010] Tjänsten Elasticsearch är installerad på infrastrukturnivå men används inte som sökmotor.%&#39;) as&#39;es_not_used&#39;
* &#39;%OBS! Startar uppdatering.%&#39;) som &#39;starting_update&#39;
* &#39;%INFO: Ställ in sökmotorn på: mysql%) as &#39;mysql_search&#39;
* %SQLSTATE[HY000] [2006] MySQL-servern har gått bort%) som mysql_borta

## [!UICONTROL Count of modules imported during deploy]

![Antal moduler som importerats under distributionen](../../assets/tools/observation-for-adobe-commerce/deploy-tab-6.jpg)

The **[!UICONTROL Count of modules imported during deploy]** visas antalet moduler som importerats under distributionen under den valda tidsramen.

## [!UICONTROL Deployed module list]

![Distribuerad modullista](../../assets/tools/observation-for-adobe-commerce/deploy-tab-7.jpg)

The **[!UICONTROL Deployed module list]** bildrutan visar distribuerade moduler under den valda tidsramen.

