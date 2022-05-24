---
title: '"Integrera [!DNL Site-Wide Analysis Tool]"'
description: Följ de här stegen för att hämta [!DNL Upgrade Compatibility Tool] rapport från [!DNL Site-Wide Analysis Tool] dashboard i ditt Adobe Commerce-projekt.
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# Integrera [!DNL Site-Wide Analysis Tool]

The [!DNL Site-Wide Analysis Tool] tillhandahåller prestandaövervakning, rapporter och rekommendationer i realtid dygnet runt, alla dagar för att säkerställa säkerheten och användbarheten vid installation av Adobe Commerce.

The [!DNL Upgrade Compatibility Tool] är nu integrerat med [!DNL Site-Wide Analysis Tool] för att ge icke-tekniska personer möjlighet att [!DNL Upgrade Compatibility Tool] och få en [HTML rapport](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/run.html?lang=en#output) innehåller en lista med problem för varje fil som anger hur allvarlig den är, felkod och felbeskrivning.

Se [[!DNL Site-Wide Analysis Tool] användarhandbok](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) för mer information.

## Kör [!DNL Upgrade Compatibility Tool] från SWAT

Navigera till [!DNL Site-Wide Analysis Tool] kontrollpanel för ditt projekt och leta upp [!DNL Upgrade Compatibility Tool] widget.

![SWAT-widget - Initial](../../assets/upgrade-guide/uct-swat-initial.png)

Klicka på **[!UICONTROL Run Upgrade Scan]**. Sökningen kan ta lite tid beroende på projektets storlek. En rotationsruta anger att sökningen pågår.

![SWAT-widget - Pågår](../../assets/upgrade-guide/uct-swat-progress.png)

När skanningen är klar visas de högnivåresultat som visas i widgeten.

![SWAT-widget - Resultat](../../assets/upgrade-guide/uct-swat-results.png)

Klicka **[!UICONTROL Download Report]** för att hämta [!DNL Upgrade Compatibility Tool] HTML rapporterar och granskar detaljerna.
