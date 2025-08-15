---
title: Översikt över  [!DNL Upgrade Compatibility Tool]
description: Lär dig mer om  [!DNL Upgrade Compatibility Tool]  och hur det kan hjälpa dig med ditt Adobe Commerce-projekt.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Guide overview

{{commerce-only}}

Handboken är avsedd för administratörer och programvaruutvecklare i Adobe Commerce. Den innehåller detaljerad information om installationen av [!DNL Upgrade Compatibility Tool] samt dess konfiguration och hantering. Det förutsätter en grundläggande förståelse för Commerce grundläggande konfiguration och funktioner.

## Översikt över [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool] är ett verktyg som kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla moduler och all kärnkod som är installerade i den. Den returnerar en lista med allvarliga problem, fel och varningar som måste åtgärdas innan du uppgraderar till en nyare version av Adobe Commerce.

## Använd [!DNL Upgrade Compatibility Tool]

Du kan använda [!DNL Upgrade Compatibility Tool] via:

- Som ett fristående [kommandoradsverktyg ](../upgrade-compatibility-tool/run.md). En fullständig lista över tillgängliga kommandon finns i [`bin/uct`-referensen](../../tools/reference/uct.md).
- Integrerar [!DNL Upgrade Compatibility Tool] med [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- En körningskonfiguration i [Magento PHPStorm-plugin](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Arbetsflöde

I följande diagram visas möjliga arbetsflöden när [!DNL Upgrade Compatibility Tool] körs:

![[!DNL Upgrade Compatibility Tool] Diagram ](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] demo

Titta på den här videon om du vill veta mer om [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Hjälp till att förbättra [!DNL Upgrade Compatibility Tool]

Om du behöver information eller har frågor som inte ingår i den här handboken använder du följande resurser:

Kontakta oss på Slack-kanalen [!DNL Upgrade Compatibility Tool]#upgrade-compatibility-tool[ för att få kontakt med ](https://magentocommeng.slack.com/archives/C019Y143U9F)-teamet. Vi vill gärna få synpunkter, problem och förslag som hjälper oss att förbättra verktyget.

[!DNL Upgrade Compatibility Tool] använder regler som definierats i våra [kodningsstandarder](https://developer.adobe.com/commerce/php/coding-standards/) för att se till att ditt projekt följer Adobe Commerce bästa praxis och för att hjälpa dig att förbättra och utöka [!DNL Upgrade Compatibility Tool].

Mer information om att bidra med kodningsstandarder finns i avsnittet [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/).

## Resurs

Se följande resurser som hjälper dig att förstå Adobe Commerce uppgraderingar:

- [Uppgraderingsguiden](../overview.md) ger en översikt över den typiska uppgraderingsresan för Adobe Commerce och de bästa metoderna att följa under den resan.
- Sidan [Kommande versioner](https://experienceleague.adobe.com/sv/docs/commerce-operations/release/planning/schedule) innehåller datum för schemalagda och kommande versioner.
- Sidan [Community-resurser](https://developer.adobe.com/commerce/contributor/community/) är till för att starta diskussioner eller hitta mer information.
- Gå till sidan för [relaterade verktyg](../upgrade-compatibility-tool/related-tools.md) för att se om det finns användbara verktyg på den vanliga uppgraderingsresan.
