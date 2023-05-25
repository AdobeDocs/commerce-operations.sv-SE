---
title: Översikt över [!DNL Upgrade Compatibility Tool]
description: Läs mer om [!DNL Upgrade Compatibility Tool] och hur det kan hjälpa dig med ditt Adobe Commerce-projekt.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: ad7f05eaa5f144b5a8616307d65be635a0c499eb
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Guide overview

{{commerce-only}}

Handboken är avsedd för administratörer och programvaruutvecklare i Adobe Commerce. Den innehåller detaljerad information om installationen av [!DNL Upgrade Compatibility Tool], samt konfiguration och hantering. Det förutsätter en grundläggande förståelse för kärnhandelns konfiguration och funktioner.

## Översikt över [!DNL Upgrade Compatibility Tool]

The [!DNL Upgrade Compatibility Tool] är ett verktyg som kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla moduler och all kärnkod som är installerade i den. Den returnerar en lista med allvarliga problem, fel och varningar som måste åtgärdas innan du uppgraderar till en nyare version av Adobe Commerce.

## Använd [!DNL Upgrade Compatibility Tool]

Du kan använda [!DNL Upgrade Compatibility Tool] via:

- Som fristående [kommandoradsgränssnitt](../upgrade-compatibility-tool/run.md) verktyg. En fullständig lista över tillgängliga kommandon finns i [`bin/uct` referens](/help/reference/uct.md).
- Integrera [!DNL Upgrade Compatibility Tool] med [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- En körningskonfiguration i [Magento PHPStorm-plugin](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Arbetsflöde

I följande diagram visas möjliga arbetsflöden när du kör [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagram](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] demo

I den här videon får du veta mer om [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Förbättra [!DNL Upgrade Compatibility Tool]

Om du behöver information eller har frågor som inte ingår i den här handboken använder du följande resurser:

Ansluta till [!DNL Upgrade Compatibility Tool] team, kontakta oss på Engineering Slack channel [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Vi vill gärna få synpunkter, problem och förslag som hjälper oss att förbättra verktyget.

The [!DNL Upgrade Compatibility Tool] använder regler som definierats i [Kodstandarder](https://developer.adobe.com/commerce/php/coding-standards/) för att säkerställa att ditt projekt följer Adobe Commerce bästa praxis och för att hjälpa dig att förbättra och utöka [!DNL Upgrade Compatibility Tool].

Se [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) för mer information om bidragande kodningsstandarder.

## Resurser

Se följande resurser som hjälper dig att förstå Adobe Commerce uppgraderingar:

- The [uppgraderingsguide](../overview.md) ger en översikt över den typiska uppgraderingsresan för Adobe Commerce eller Magento Open Source och de bästa sätten att följa under den resan.
- The [kommande versioner](https://devdocs.magento.com/release/) sidan innehåller datum för schemalagda och kommande versioner.
- The [communityresurser](https://developer.adobe.com/commerce/contributor/community/) ska du placera för att starta diskussioner eller hitta mer information.
- Kontrollera [relaterade verktyg](../upgrade-compatibility-tool/related-tools.md) sida där du hittar användbara verktyg under den normala uppgraderingsresan.
