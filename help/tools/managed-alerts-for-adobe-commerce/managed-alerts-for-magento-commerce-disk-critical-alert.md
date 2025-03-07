---
title: 'Hanterade varningar för Adobe Commerce: Diskkritisk varning'
description: Den här artikeln innehåller felsökningssteg när du får en viktig diskvarning för Adobe Commerce i  [!DNL New Relic]. Det krävs omedelbara åtgärder för att åtgärda problemet.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: c1757dee33b22b5dae3c7f0eab9c1efe20d0a9a8
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---


# Hanterade varningar för Adobe Commerce: Diskkritisk varning

Den här artikeln innehåller felsökningssteg när du får en viktig diskvarning för Adobe Commerce i [!DNL New Relic]. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![Diskkritisk varning](../../assets/managed-alerts/disk-critical-magento-managed.png){width="500"}

## Berörda produkter och versioner

Adobe Commerce molninfrastruktur i Pro-planarkitekturen

## Problem

Du får en avisering i [!DNL New Relic] om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar har utvecklats av Adobe för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u> **Gör!** </u>

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar finns i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode). Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses).

**Gör inte!**

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare stress på CPU eller disk.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

Din webbplats kanske inte svarar (om du inte redan drabbas av ett avbrott i din webbplats) om du utför någon av åtgärderna&quot;Gör inte&quot; innan du har undersökt och löst orsaken till varningen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

>[!WARNING]
>
>Eftersom det här är en viktig varning rekommenderar vi att du slutför **steg 1** innan du försöker felsöka problemet (steg 2 och framåt).

1. Kontrollera om Adobe Commerce supportanmälan finns. Anvisningar finns i [Spåra supportärenden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) i Commerce Support Knowledge Base. Supporten kan ha fått en [!DNL New Relic]-tröskelvärdesvarning, skapat en biljett och börjat arbeta med problemet. Om det inte finns någon biljett skapar du en. Biljetten ska ha följande information:
   * Kontaktorsak: välj **[!UICONTROL New Relic CRITICAL alert received]**.
   * Beskrivning av aviseringen.
   * [[!DNL New Relic] Incidentlänk](https://docs.newrelic.com/docs/alerts/incident-management/view-event-details-incidents/). Detta ingår i dina [hanterade aviseringar för Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Granska diskarna i [!DNL New Relic] för högsta användning. Anvisningar finns på fliken **[!UICONTROL Storage]** på sidan [[!DNL New Relic] Värdar för infrastrukturövervakning: [!UICONTROL Storage] tab](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage):
   * Om du ser en långsam ökning av diskanvändningen i [!DNL New Relic] kan du prova med följande alternativ:
      * Optimera diskutrymmet genom att justera utrymmesallokeringen. Anvisningar om hur du gör detta finns i [Hantera diskutrymme](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) i handboken för Commerce on Cloud. Du kan också behöva be om mer diskutrymme (kontakta Adobe Account Team).
      * Frigör diskutrymme för MySQL. Mer information finns i [MySQL-diskutrymmet är lågt](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud) i Commerce Support Knowledge Base.
      * Om [!DNL New Relic] visar snabb ökning av diskanvändningen kan detta tyda på att det finns ett problem som har fått en fil att öka mycket snabbt i en katalog. Gör följande kontroller:
         1. Kontrollera det totala diskutrymmet för att identifiera problemet genom att köra följande kommando i CLI/Terminal: `df -h`
         1. När du har identifierat en katalog med oväntat stor och ökande diskanvändning måste du kontrollera det berörda filsystemet. I följande exempel visas hur du kontrollerar filkatalogen `pub/media/`. Det här är den katalog som Commerce använder för att lagra loggar och stora mediefiler. Du bör dock köra det här kommandot för alla kataloger som visar oväntad diskanvändning: `du -sch ~/pub/media/*`

Om utdata från terminalen visar en fil i någon av dessa kataloger som snabbt ökar diskanvändningen och du vet att filens innehåll inte behövs, bör du ta bort filen. Om du inte är säker på att du kan utföra den här åtgärden [skickar du en Adobe Commerce-supportanmälan](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).
