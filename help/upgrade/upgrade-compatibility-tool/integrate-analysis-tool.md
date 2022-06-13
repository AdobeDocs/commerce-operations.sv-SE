---
title: '"Integrera [!DNL Site-Wide Analysis Tool]"'
description: Följ de här stegen för att hämta [!DNL Upgrade Compatibility Tool] rapport från [!DNL Site-Wide Analysis Tool] dashboard i ditt Adobe Commerce-projekt.
source-git-commit: 0d4ccc8c2e1a470b5fb3a7d59e81230e8986c257
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---


# Integrera [!DNL Site-Wide Analysis Tool]

The [!DNL Site-Wide Analysis Tool] tillhandahåller prestandaövervakning, rapporter och rekommendationer i realtid dygnet runt, alla dagar för att säkerställa säkerheten och användbarheten för Adobe Commerce-instanser.

The [!DNL Upgrade Compatibility Tool] är nu integrerat med [!DNL Site-Wide Analysis Tool] för att ge icke-tekniska personer möjlighet att [!DNL Upgrade Compatibility Tool] och få en [rapport](../upgrade-compatibility-tool/reports.md) innehåller en lista med problem för varje fil.

Se [[!DNL Site-Wide Analysis Tool] användarhandbok](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) för mer information.

## Kör [!DNL Upgrade Compatibility Tool] från [!DNL Site-Wide Analysis Tool]

Navigera till [!DNL Site-Wide Analysis Tool] kontrollpanel för ditt projekt och leta upp [!DNL Upgrade Compatibility Tool] widget.

![SWAT-widget - Initial](../../assets/upgrade-guide/uct-swat-initial.png)

Klicka på **[!UICONTROL Run Upgrade Scan]**. Sökningen kan ta lite tid beroende på projektets storlek. En rotationsruta anger att sökningen pågår.

![SWAT-widget - Pågår](../../assets/upgrade-guide/uct-swat-progress.png)

När skanningen är klar visas de högnivåresultat som visas i widgeten.

![SWAT-widget - Resultat](../../assets/upgrade-guide/uct-swat-results.png)

Klicka **[!UICONTROL Download Report]** för att hämta [!DNL Upgrade Compatibility Tool] [HTML rapport](../upgrade-compatibility-tool/reports.md#html-report) och granska detaljerna.

När du kör [!DNL Upgrade Compatibility Tool] via [!DNL Site-Wide Analysis Tool] rapporten visar resultat som jämför projektets version med den senaste versionen.
