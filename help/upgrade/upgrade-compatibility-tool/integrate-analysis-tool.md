---
title: Integrera  [!DNL Site-Wide Analysis Tool]
description: Följ de här stegen för att hämta  [!DNL Upgrade Compatibility Tool] rapporten från  [!DNL Site-Wide Analysis Tool] dashboard i ditt Adobe Commerce-projekt.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Integrera [!DNL Site-Wide Analysis Tool]

[!DNL Site-Wide Analysis Tool] tillhandahåller prestandaövervakning, rapporter och rekommendationer i realtid dygnet runt, alla dagar, för att säkerställa säkerheten och användbarheten för Adobe Commerce-instanser.

[!DNL Upgrade Compatibility Tool] är nu integrerat med [!DNL Site-Wide Analysis Tool] för att ge icke-tekniska personer möjlighet att köra [!DNL Upgrade Compatibility Tool] och få en [rapport](../upgrade-compatibility-tool/reports.md) med en lista över problem för varje fil.

Mer information finns i [[!DNL Site-Wide Analysis Tool] användarhandboken](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access).

## Kör [!DNL Upgrade Compatibility Tool] från [!DNL Site-Wide Analysis Tool]

Navigera till [!DNL Site-Wide Analysis Tool]-instrumentpanelen för ditt projekt och leta upp [!DNL Upgrade Compatibility Tool]-widgeten.

![UCT SWAT widget - Initial](../../assets/upgrade-guide/uct-swat-initial.png)

Klicka på **[!UICONTROL Run Upgrade Scan]**. Sökningen kan ta lite tid beroende på projektets storlek. En rotationsruta anger att sökningen pågår.

![UCT SWAT-widget - Pågår](../../assets/upgrade-guide/uct-swat-progress.png)

När skanningen är klar visas de högnivåresultat som visas i widgeten.

![UCT SWAT widget - Resultat](../../assets/upgrade-guide/uct-swat-results.png)

Klicka på **[!UICONTROL Download Report]** för att hämta [!DNL Upgrade Compatibility Tool] [HTML-rapporten](../upgrade-compatibility-tool/reports.md#html-report) och granska informationen.


>[!NOTE]
>
> Om du kör [!DNL Upgrade Compatibility Tool] genom [!DNL Site-Wide Analysis Tool] optimeras dina resultat och du kan fokusera på problem som är nya och viktiga för måluppgraderingen. Den använder alternativet [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) och visar alltid resultat som jämför projektets version med den senaste versionen som släppts.
