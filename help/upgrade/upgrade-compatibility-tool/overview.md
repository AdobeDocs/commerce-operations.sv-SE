---
title: Översikt över [!DNL Upgrade Compatibility Tool]
description: Läs mer om [!DNL Upgrade Compatibility Tool] och hur det kan hjälpa dig med ditt Adobe Commerce-projekt.
source-git-commit: fbe47245623469a93cce5cc5a83baf467a007bc4
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---


# Översikt över [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

The [!DNL Upgrade Compatibility Tool] är ett kommandoradsverktyg som kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla moduler och all kärnkod som är installerade i den. Den returnerar en lista med allvarliga problem, fel och varningar som måste åtgärdas innan du uppgraderar till den senaste versionen av Adobe Commerce. Den identifierar också potentiella problem som måste åtgärdas i koden innan du försöker uppgradera till en nyare version av Adobe Commerce.

The [!DNL Upgrade Compatibility Tool] gör att du kan identifiera när viktiga kodändringar har gjorts i anpassade funktioner. Se [Kör verktyget](../upgrade-compatibility-tool/run.md) för mer information.

Det distribueras som ett Composer-paket med varje version av Adobe Commerce. Se [Utvecklare](../upgrade-compatibility-tool/developer.md) för mer information.

Se [Installera](../upgrade-compatibility-tool/install.md) för de första stegen med [!DNL Upgrade Compatibility Tool].

## Arbetsflöde

I följande diagram visas det förväntade arbetsflödet vid körning av [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagram](../../assets/upgrade-guide/mvp-diagram-v3.png)

## The [!DNL Upgrade Compatibility Tool] användningsfall

Följande exempel beskriver den vanliga processen för en Adobe Commerce-partner att uppgradera en klientinstans:

1. Ladda ned [!DNL Upgrade Compatibility Tool] paket från Adobe Commerce-databasen (`https://repo.magento.com/`). Se [Ladda ned [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) för mer information.
1. Kör [!DNL Upgrade Compatibility Tool] under [beta](https://devdocs.magento.com/release/beta-program.html) fas av nyaste [Adobe Commerce release](https://devdocs.magento.com/release/).
1. Huvudkommandot är `upgrade:check`. Det här kommandot analyserar instansen och söker efter fel, varningar och kritiska problem i instansen. Så här optimerar du resultat:

   - Lägg till alternativ `--ignore-current-version-compatibility-issues` om du vill ignorera alla kända allvarliga problem, fel och varningar i den aktuella Adobe Commerce-versionen. Visar endast resultat av den önskade versionen.
   - Använd alternativ `--min-issue-level` för att ange minsta emissionsnivå. Hjälper dig att prioritera endast de viktigaste problemen med uppgraderingen. Om du bara vill analysera en viss leverantör, modul eller katalog kan du även ange sökvägen. Se [Kör verktyget](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/run.html?lang=en) om du vill ha mer information.

1. Generera en vanilj-instans för den specifika version av Adobe Commerce som är installerad. Se [Contributor Guide](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) för mer information om hur du använder `instance` för att generera en vaniljinstallation.

   >[!NOTE]
   >
   >En vanilj-instans är en ren installation av en angiven versionstagg eller gren för en specifik version.

1. The [!DNL Upgrade Compatibility Tool] Identifierar anpassade brutna områden. Programvaruteknikern kan förstå hur komplicerad uppgraderingen är och uppskatta uppgraderingens arbete. Denna information delas med intressenter.
1. En budget och en tidslinje kommer att definieras för uppgraderingen.
1. Programutvecklare kan sedan arbeta med nödvändiga kodändringar för att åtgärda de trasiga modulerna.
1. The [!DNL Upgrade Compatibility Tool] kan köras för att spåra uppgraderingsförloppet.
1. Allt som checkas ut och konstruktion kan nu föra ut koden till en staging-miljö där regressionstester bekräftar att alla tester är gröna, vilket gör att de kan släppa den senaste Adobe Commerce-versionen till produktion samma dag som Adobe Commerce-förhandsversionen släpps.

   ![[!DNL Upgrade Compatibility Tool] publik](../../assets/upgrade-guide/audience-uct-v3.png)

## Förbättra [!DNL Upgrade Compatibility Tool]

Ansluta till [!DNL Upgrade Compatibility Tool] team, kontakta oss på Engineering Slack channel [[!DNL Upgrade Compatibility Tool]](https://magentocommeng.slack.com/archives/C019Y143U9F). Vi vill gärna få synpunkter, problem och förslag som hjälper oss att förbättra verktyget.

The [!DNL Upgrade Compatibility Tool] använder regler som definierats i [Kodstandarder](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) för att säkerställa att ditt projekt följer Adobe Commerce bästa praxis och för att hjälpa dig att förbättra och utöka [!DNL Upgrade Compatibility Tool].

Se [Contribute](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  om du vill ha mer information om hur du bidrar till projektet.

## Resurser

Vi har tagit fram följande resurser som hjälper dig att förstå Adobe Commerce uppgraderingar:

- [Uppgraderingsguide](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [Kommande versioner](https://devdocs.magento.com/release/)
- [Community-resurser](https://devdocs.magento.com/community/resources/resources.html) sida för mer information.
