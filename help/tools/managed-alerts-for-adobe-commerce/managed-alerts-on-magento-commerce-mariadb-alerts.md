---
title: 'Hanterade aviseringar om Adobe Commerce: MariaDB-aviseringar'
description: Den här artikeln innehåller felsökningssteg när du får MariaDB-aviseringar för Adobe Commerce i  [!DNL New Relic]. MariaDB-varningarna övervakar hög frågebelastning och överdrivna DML-frågor (Data Manipulation Language). Båda kan leda till en försämrad användarupplevelse eller till och med till driftstopp. Du kan få två typer av varningar.
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: ccf8b7c5ad1fbef2cfba05f65f05ab8af0375b4c
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---


# Hanterade aviseringar om Adobe Commerce: MariaDB-aviseringar

Den här artikeln innehåller felsökningssteg när du får MariaDB-aviseringar för Adobe Commerce i [!DNL New Relic]. MariaDB-varningarna övervakar hög frågebelastning och överdrivna DML-frågor (Data Manipulation Language). Båda kan leda till en försämrad användarupplevelse eller till och med till driftstopp. Du kan få två typer av varningar:

* Varning för DML-frågor
* Kritiska DML-frågor

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur Pro planarkitektur

## Problem

Du får en hanterad avisering i [!DNL New Relic] om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar har utvecklats av Adobe för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

**Gör!**

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar om hur du gör detta finns i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i Commerce installationshandbok. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses).
* Avsluta alla skript, t.ex. import, som kan vara orsaken till varningen om platsens prestanda påverkas.

**Gör inte!**

* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare stress för MariaDB.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

## Lösning

**DML-frågor (frågor som ändrar databasen med UPDATE, INSERT och DELETE)**

Om du får en viktig DML-frågerapport startar du steg ett. Om du får ett varningsmeddelande om DML-frågor startar du steg två.

1. Kontrollera om Adobe Commerce supportanmälan finns. Anvisningar finns i vår kunskapsbas [Spåra dina supportärenden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case). Supporten kan ha fått en [!DNL New Relic]-tröskelvärdesvarning, skapat en biljett och börjat arbeta med problemet. Om det inte finns någon biljett skapar du en. Biljetten ska ha följande information:
   * Kontaktorsak: välj **[!UICONTROL New Relic MariaDB alert received]**.
   * Beskrivning av aviseringen.
   * [[!DNL New Relic] Incidentlänk](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Detta ingår i dina [hanterade aviseringar för Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Identifiera orsaken till problemet genom att identifiera DML-frågorna:
   1. Granska databasåtgärderna genom att använda steg från New Relic [Databassida](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time).
   1. Sortera efter **[!UICONTROL CALL COUNT]** och sedan **[!UICONTROL OPERATION]**. Granska åtgärderna `INSERT`, `DELETE` och `UPDATE`.
   1. Håll utkik efter AVG.
   1. Klicka igenom för att hitta anropare för databasåtgärder. Detta identifierar transaktioner som använder den frågan efter tid.
   1. Se antingen kodoptimeringar eller operativa optimeringar:
      * Kodoptimeringar: Optimera frågor med massinfogningar/uppdateringar, minimera indexanvändning eller begränsa kod.
      * Operativa optimeringar: Avlasta resurskrävande dataändringar till lägre trafiktider.
      * Ytterligare optimeringar: Se till att du har den senaste versionen av ECE-Tools. Anvisningar om hur du gör detta finns i [Uppdatera versionen av e-postverktygen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) i handboken för Commerce on Cloud.
