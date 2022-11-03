---
title: Bästa praxis för uppdateringstjänster
description: Lär dig hur du uppdaterar din Adobe Commerce i molninfrastruktursstacken.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Bästa praxis för uppdateringstjänster

I den här artikeln finns rekommendationer om hur du kan uppdatera din Adobe Commerce i molninfrastruktursstacken och länkar till användbara resurser.

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur 2.4.x och senare

## Uppdatera tjänster

Uppgradera de tjänster och komponenter som används av Adobe Commerce innan de når eller är i närheten av sista giltighetsdatum. Detta bidrar till att hålla jämna steg med PCI-kompatibiliteten och minska säkerhetsproblemen.

Kunder som har Starter-planer kan själva tjäna på uppgraderingar av tjänster. Se [Ändra tjänstversion](https://devdocs.magento.com/cloud/project/services.html#change-service-version) om du vill ha mer information om hur du gör detta.

Kunder som har Pro-planer kan bara själva få uppgraderingar av sina tjänster [Integreringsmiljö](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md). För uppgraderingar av tjänster i produktionen måste du [skicka en supportanmälan](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) begär uppgraderingen.

>[!WARNING]
>
>Uppgraderingar av tjänster kan inte föras över till produktionsmiljön utan att vårt infrastrukturteam får 48 arbetstimmar i förväg. Detta är nödvändigt eftersom vi måste se till att det finns en infrastruktursupporttekniker tillgänglig som kan uppdatera din konfiguration inom en önskad tidsram med minimala driftavbrott i din produktionsmiljö.

Du kan visa en lista över tjänstversioner och slutdatum i följande fil: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Den här filen kan inte betraktas som en enda sanningskälla. Kontakta leverantörens officiella webbplatser om du är osäker.

## Ytterligare information

[Systemkrav](../../../installation/system-requirements.md)
