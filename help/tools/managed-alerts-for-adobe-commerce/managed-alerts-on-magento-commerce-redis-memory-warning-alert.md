---
title: 'Hanterade aviseringar på Adobe Commerce: [!DNL Redis] minnesvarning'
description: I den här artikeln finns felsökningssteg för när du får en [!DNL Redis] varningsvarning för Adobe Commerce i [!DNL New Relic]. Omedelbar åtgärd krävs.
feature: Categories, Marketing Tools, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: e91ed9e95677790001fcfa3acca75a709c003c39
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---


# Hanterade aviseringar på Adobe Commerce: [!DNL Redis] minnesvarning

Den här artikeln innehåller felsökningssteg för när du får en [!DNL Redis]-varning för Adobe Commerce i [!DNL New Relic]. Du måste vidta omedelbara åtgärder för att lösa problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt:

![new_relic_redis_memory_warning.png](../../assets/managed-alerts/new_relic_redis_memory_warning.png)

## Berörda produkter och versioner

Alla versioner av Adobe Commerce på Cloud Infrastructure Pro-planarkitekturen.

## Problem

Du får en avisering i [!DNL New Relic] om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar har utvecklats av Adobe för att ge säljarna en standarduppsättning med hjälp av insikter från support och tekniker.

**<u>Gör!</u>**

* Vi rekommenderar att du avbryter alla schemalagda distributioner tills den här aviseringen har rensats.
* Om din webbplats inte svarar eller inte svarar alls ska du omedelbart försätta platsen i underhållsläge. Anvisningar om hur du gör detta finns i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i Commerce installationshandbok.
* Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar om hur du gör detta finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) i Commerce installationshandbok.

**<u>Gör inte!</u>**

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare stress på CPU eller disk.
* Utför alla större administrativa uppgifter (dvs. större åtgärder i Commerce Admin, t.ex. import/export av data, tömning av media, sparande av kategorier med ett stort antal tilldelade produkter och massuppdateringar).
* Rensa cachen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

1. Kontrollera om [!DNL Redis] använt minne ökar eller minskar genom att gå till sidan [one.newrelic.com](https://login.newrelic.com/login) > **Infrastruktur** > **Tjänster från tredje part** och välj [!DNL Redis]-instrumentpanelen. Om det är stabilt eller ökar [skickar du en supportanmälan](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) så att klustret storleksändras, eller ökar `maxmemory`-gränsen till nästa nivå.
1. Om du inte kan identifiera orsaken till den ökade minnesförbrukningen för [!DNL Redis] kan du granska de senaste trenderna för att identifiera problem med de senaste koddistributionerna eller konfigurationsändringarna (till exempel nya kundgrupper och stora ändringar i katalogen). Vi rekommenderar att du granskar de senaste sju dagarnas aktivitet för att se eventuella samband i koddistributioner eller ändringar.
1. Kontrollera om det finns tillägg från tredje part som inte fungerar som de ska:
   * Försök att hitta ett samband med nyligen installerade tillägg från tredje part och när problemet uppstod.
   * Granska tillägg som kan påverka cacheminnet i Adobe Commerce och få cacheminnet att växa snabbt. Exempel: anpassade layoutblock, åsidosätta cachefunktioner och lagra stora mängder data i cache.
1. Om det inte finns några tecken på att tillägg fungerar som de ska kan du [installera de senaste korrigeringsfilerna för att åtgärda [!DNL Redis] problem för Adobe Commerce i molninfrastrukturen](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues). Om ovanstående steg inte hjälper dig att identifiera eller felsöka problemkällan bör du överväga att aktivera L2-cache för att minska nätverkstrafiken mellan appen och [!DNL Redis]. Allmän information om vad som är L2-cache finns i [L2-cachning i Adobe Commerce-programmet](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cache/level-two-cache) i Commerce Configuration Guide. Så här aktiverar du L2-cache för molninfrastruktur:
   * Uppgradera ECE-verktygen om de är under version 2002.1.2.
   * Konfigurera L2-cache genom att använda [Använd REDIS\_BACKEND-variabeln](https://experienceleague.adobe.com/sv/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend) och uppdatera `.magento.env.yaml`-filen:

   ```yaml
   stage:
      deploy:
          REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
