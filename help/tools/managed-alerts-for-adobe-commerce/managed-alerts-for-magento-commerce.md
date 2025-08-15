---
title: Hanterade aviseringar för Adobe Commerce
description: Om du använder en Adobe Commerce-plan på Cloud Infrastructure Pro-planarkitekturen kan du använda hanterade aviseringar för att förstå webbplatsens hälsa. Om du använder en Adobe Commerce-arkitektur för startplanens molninfrastruktur får du bara aviseringar om villkoren för  [!DNL Apdex] och felfrekvensen.
feature: Observability, Support, Tools and External Services
role: Admin
exl-id: 3fc4b07f-4e27-4833-97a9-cf9741ae5648
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# Hanterade aviseringar för Adobe Commerce


Vi har konfigurerat viktiga instrumentpaneler och aviseringar som hjälper dig att förstå när din webbplats når kritisk lagring och [!DNL Apdex] nivåer (användarnas tillfredsställelse med svarstid för program och tjänster). Detta kan hjälpa dig att vidta åtgärder innan du märker att svarstiderna tar lång tid eller att ett driftstopp inträffar. Du kan felsöka varningarna med artiklarna nedan. Innan du kan använda varningarna måste du först konfigurera meddelandekanaler. Se [[!DNL New Relic] Konfigurera meddelandekanaler](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/new-relic-service) i Commerce on Cloud Guide.

>[!NOTE]
>
>Om hanterade aviseringar för Adobe Commerce-aviseringsprincipen inte är tillgängliga kan det bero på att det här kontot nyligen har skapats eller att [!DNL New Relic] nyligen har konfigurerats. En process körs varje tisdag för att lägga till varningsprincipen till dessa konton. Varningspolicyn bör vara tillgänglig dagen efter att nästa process har körts. Om principen fortfarande saknas [skickar du en supportförfrågan](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) från Adobe Commerce och inkluderar ditt projekt-ID.

I tabellen nedan finns länkar till KB-artiklar med felsökningssteg för dessa aviseringar:

* Hanterade varningar för Adobe Commerce: CPU-varningsmeddelanden
* Hanterade aviseringar för Adobe Commerce: CPU Critical Alert
* Hanterade varningar för Adobe Commerce: minnesvarning
* Hanterade varningar för Adobe Commerce: minneskritisk varning
* Hanterade aviseringar för Adobe Commerce: [!DNL Apdex] varning
* Hanterade aviseringar för Adobe Commerce: [!DNL Apdex] kritisk avisering
* Hanterade varningar för Adobe Commerce: diskvarning
* Hanterade varningar för Adobe Commerce: Diskkritisk varning
* Hanterade aviseringar om Adobe Commerce: MariaDB-aviseringar
* Hanterade aviseringar på Adobe Commerce: [!DNL Redis] minnesvarning
* Hanterade aviseringar på Adobe Commerce: [!DNL Redis] minneskritisk avisering

>[!NOTE]
>
>De fastställda tröskelvärdena för både varningsmeddelanden och kritiska aviseringar baseras på forskning vi gör med hjälp av historiska resultatdata för hela vår kundbas, och representerar de senaste insikterna från Adobe Commerce support- och konstruktionsgrupper. Observera att dessa tröskelvärden kan ändras baserat på den senaste, pågående analysen. Det typiska varningsflödet är att få varningar som är mindre eller större vad gäller allvarlighetsgrad. Du kommer förmodligen få en varning innan du får en viktig varning. Mer information om felsökningsåtgärder finns i länkarna till artiklar.

| Allvarlighetsgrad | CPU | Minne | Skiva | [!DNL Apdex] | MariaDB | [!DNL Redis] minne | Felsökning av artikel |
|----------|-----|--------|------|-------|---------|--------------|-------------------------|
| Varning | ✅ |        |      |       |         |              | [Hanterade aviseringar för Adobe Commerce: CPU-varning](managed-alerts-for-magento-commerce-cpu-warning-alert.md) |
| Kritisk | ✅ |        |      |       |         |              | [Hanterade aviseringar för Adobe Commerce: CPU-kritisk avisering](managed-alerts-on-magento-commerce-cpu-critical-alert.md) |
| Varning |     | ✅ |      |       |         |              | [Hanterade aviseringar för Adobe Commerce: minnesvarning](managed-alerts-for-magento-commerce-memory-warning-alert.md) |
| Kritisk |     | ✅ |      |       |         |              | [Hanterade aviseringar för Adobe Commerce: minneskritisk avisering](managed-alerts-on-magento-commerce-memory-critical-alert.md) |
| Varning |     |        |      | ✅ |         |              | [Hanterade aviseringar för Adobe Commerce: [!DNL Apdex] varning](managed-alerts-for-magento-commerce-apdex-warning-alert.md) |
| Kritisk |     |        |      | ✅ |         |              | [Hanterade aviseringar för Adobe Commerce: [!DNL Apdex] Kritisk avisering](managed-alerts-for-magento-commerce-apdex-critical-alert.md) |
| Varning |     |        | ✅ |       |         |              | [Hanterade aviseringar för Adobe Commerce: diskvarning](managed-alerts-for-magento-commerce-disk-warning-alert.md) |
| Kritisk |     |        | ✅ |       |         |              | [Hanterade aviseringar för Adobe Commerce: Diskkritisk avisering](managed-alerts-for-magento-commerce-disk-critical-alert.md) |
| Varning och kritisk |     |        |      |       | ✅ |              | [Hanterade aviseringar på Adobe Commerce: MariaDB-aviseringar](managed-alerts-on-magento-commerce-mariadb-alerts.md) |
| Varning |     |        |      |       |         | ✅ | [Hanterade aviseringar på Adobe Commerce: [!DNL Redis] minnesvarning](managed-alerts-on-magento-commerce-redis-memory-warning-alert.md) |
| Kritisk |     |        |      |       |         | ✅ | [Hanterade aviseringar på Adobe Commerce: [!DNL Redis] minneskritisk avisering](managed-alerts-on-magento-commerce-redis-memory-critical-alert.md) |
