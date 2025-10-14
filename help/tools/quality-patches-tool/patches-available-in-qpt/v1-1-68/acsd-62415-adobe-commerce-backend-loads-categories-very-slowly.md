---
title: 'ACSD-62415: Adobe Commerce-backend läser in [!UICONTROL Categories] mycket långsamt'
description: Använd korrigeringsfilen ACSD-62415 för att åtgärda Adobe Commerce-problemet där prestandan för sidan [!UICONTROL Categories] på panelen [!UICONTROL Admin] läses in mycket långsamt när det finns ett stort antal ankarkategorier.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8040414630cf3c992e0d68d5693990f8f50fdbcb
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# ACSD-62415: Adobe Commerce-backend läser in **[!UICONTROL Categories]** mycket långsamt när ankarkategorier finns

Korrigeringen ACSD-62415 åtgärdar ett problem där prestandan för sidan **[!UICONTROL Categories]** på panelen **[!UICONTROL Admin]** läses in mycket långsamt när ett stort antal ankarkategorier finns. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 har installerats. Korrigerings-ID är ACSD-62415. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sidan **[!UICONTROL Categories]** på panelen **[!UICONTROL Admin]** läses in mycket långsamt när det finns ett stort antal ankarkategorier.

<u>Steg som ska återskapas</u>:

1. Generera 3K-ankarkategorier.
1. Öppna **[!UICONTROL Catalog]** > sidan **[!UICONTROL Categories]** på panelen **[!UICONTROL Admin]**.

<u>Förväntade resultat</u>:

Sidan **[!UICONTROL Categories]** läses in snabbt och frågan ska inte upprepas 1K gånger.

<u>Faktiska resultat</u>:

Inläsningen tar 7 till 20 sekunder och frågan körs mer än 1 kB gånger.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
