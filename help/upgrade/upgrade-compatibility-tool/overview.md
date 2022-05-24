---
title: Översikt över [!DNL Upgrade Compatibility Tool]
description: Läs mer om [!DNL Upgrade Compatibility Tool] och hur det kan hjälpa dig med ditt Adobe Commerce-projekt.
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# Guide overview

Handboken är avsedd för administratörer och programvaruutvecklare i Adobe Commerce. Den innehåller detaljerad information om installationen av [!DNL Upgrade Compatibility Tool], samt konfiguration och hantering. Det förutsätter en grundläggande förståelse för kärnhandelns konfiguration och funktioner.

## Översikt över [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

The [!DNL Upgrade Compatibility Tool] är ett kommandoradsverktyg som kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla moduler och all kärnkod som är installerade i den. Den returnerar en lista med allvarliga problem, fel och varningar som måste åtgärdas innan du uppgraderar till en nyare version av Adobe Commerce.

Se [Kör verktyget](../upgrade-compatibility-tool/run.md) för mer information.

Se [Installera](../upgrade-compatibility-tool/install.md) för de första stegen med [!DNL Upgrade Compatibility Tool].

Se det här [videosjälvstudiekurs](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) om du vill veta mer om [!DNL Upgrade Compatibility Tool].

### Arbetsflöde

I följande diagram visas möjliga arbetsflöden när du kör [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagram](../../assets/upgrade-guide/uct-diagram-v5.png)

### The [!DNL Upgrade Compatibility Tool] användningsfall

Följande exempel beskriver den vanliga processen för en Adobe Commerce-partner att uppgradera en klientinstans:

1. Ladda ned [!DNL Upgrade Compatibility Tool] paket från Adobe Commerce-databasen (`https://repo.magento.com/`). Se [Ladda ned [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) för mer information.
1. Kör [!DNL Upgrade Compatibility Tool] under [beta](https://devdocs.magento.com/release/beta-program.html) fas av nyaste [Adobe Commerce release](https://devdocs.magento.com/release/).
1. Generera en vanilj-instans för den specifika version av Adobe Commerce som är installerad. Se [Contributor Guide](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) för mer information om hur du använder `instance` för att generera en vaniljinstallation.

   >[!NOTE]
   >
   >En vanilj-instans är en ren installation av en angiven versionstagg eller gren för en specifik version.

1. The [!DNL Upgrade Compatibility Tool] Identifierar uppgraderingsproblem som kan hjälpa programvaruutvecklare att förstå hur komplicerad uppgraderingen är och uppskatta uppgraderingens arbete.
1. Denna information delas med intressenter.
1. En budget och en tidslinje kommer att definieras för uppgraderingen.
1. Programutvecklare kan sedan arbeta med nödvändiga kodändringar för att åtgärda de trasiga modulerna.
1. The [!DNL Upgrade Compatibility Tool] kan köras för att spåra uppgraderingsförloppet.
1. Allt som checkas ut och konstruktion kan nu föra ut koden till en staging-miljö där regressionstester bekräftar att alla tester är gröna, vilket gör att de kan släppa den senaste Adobe Commerce-versionen till produktion samma dag som Adobe Commerce-förhandsversionen släpps.

   ![[!DNL Upgrade Compatibility Tool] publik](../../assets/upgrade-guide/audience-uct-v3.png)

### Förbättra [!DNL Upgrade Compatibility Tool]

Om du behöver information eller har frågor som inte ingår i den här handboken använder du följande resurser:

Ansluta till [!DNL Upgrade Compatibility Tool] team, kontakta oss på Engineering Slack channel [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Vi vill gärna få synpunkter, problem och förslag som hjälper oss att förbättra verktyget.

The [!DNL Upgrade Compatibility Tool] använder regler som definierats i [Kodstandarder](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) för att säkerställa att ditt projekt följer Adobe Commerce bästa praxis och för att hjälpa dig att förbättra och utöka [!DNL Upgrade Compatibility Tool].

Se [Contribute](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  för mer information om bidragande kodningsstandarder.

### Resurser

Vi har tagit fram följande resurser som hjälper dig att förstå Adobe Commerce uppgraderingar:

- [Uppgraderingsguide](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [Kommande versioner](https://devdocs.magento.com/release/)
- [Community-resurser](https://devdocs.magento.com/community/resources/resources.html) sida för mer information.
- [Relaterade verktyg](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/related-tools.html)
