---
title: 'Hanterade varningar för Adobe Commerce: Diskvarning'
description: Den här artikeln innehåller felsökningssteg när du får en varning för Adobe Commerce i  [!DNL New Relic]. Det krävs omedelbara åtgärder för att åtgärda problemet.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 90ea4384-97aa-499d-93c1-b40c3a4eed42
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# Hanterade varningar för Adobe Commerce: Diskvarning

Den här artikeln innehåller felsökningssteg när du får en varning för Adobe Commerce på [!DNL New Relic]. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![Varningsmeddelande om diskutrymme som visar att tröskelvärdet för lagringsanvändning har överskridits](../../assets/managed-alerts/disk-warning-magento-managed.png){width="500"}

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, Pro-planarkitektur.

## Problem

Du får en avisering i [!DNL New Relic] om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar har utvecklats av Adobe för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u> **Gör!** </u>

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar om hur du gör detta finns i [Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i Commerce installationshandbok. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar om hur du gör detta finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) i Commerce installationshandbok.

<u> **Gör inte!** </u>

* lansera fler marknadsföringskampanjer som kan ge er plats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare stress på CPU eller disk.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen. Din webbplats kanske inte svarar (om du inte redan drabbas av ett avbrott i din webbplats) om du utför någon av åtgärderna&quot;Gör inte&quot; innan du har undersökt och löst orsaken till varningen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken:

1. Granska diskarna i [!DNL New Relic] för högsta användning. Anvisningar finns på fliken **[!UICONTROL Storage]** på sidan [[!DNL New Relic] Värdar för infrastrukturövervakning: [!UICONTROL Storage] tab](https://docs.newrelic.com/docs/infrastructure/infrastructure-data/infrastructure-ui-pages/infra-hosts-ui-page/#storage):
   * Om du ser en långsam ökning av diskanvändningen i [!DNL New Relic] kan du prova med följande alternativ:
      * Optimera diskutrymmet genom att justera utrymmesallokeringen. Anvisningar om hur du gör detta finns i [Hantera diskutrymme](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space) i handboken för Commerce on Cloud. Du kan också behöva be om mer diskutrymme (kontakta Adobe Account Team).
      * Frigör diskutrymme för MySQL. Gå till [MySQL-diskutrymmet är lågt](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud) för steg.
      * Om [!DNL New Relic] visar snabb ökning av diskanvändningen kan detta tyda på att det finns ett problem som har fått en fil att öka mycket snabbt i en katalog. Gör följande kontroller:
         1. Kontrollera det totala diskutrymmet för att identifiera problemet genom att köra följande kommando i CLI/Terminal: `df -h`
         1. När du har identifierat en katalog med oväntat stor och ökande diskanvändning måste du kontrollera det berörda filsystemet. I följande exempel visas hur du kontrollerar filkatalogen `pub/media/`. Det här är den katalog som Adobe Commerce använder för att lagra loggar och stora mediefiler. Du bör dock köra det här kommandot för alla kataloger som visar oväntad diskanvändning: `du -sch ~/pub/media/*`.

Om utdata från terminalen visar en fil i någon av dessa kataloger som snabbt ökar diskanvändningen och du vet att filens innehåll inte behövs, bör du ta bort filen. Om du inte är säker på att du kan utföra den här åtgärden [skickar du en Adobe Commerce-supportanmälan](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).
