---
title: 'ACSD-58325: Knappen [!UICONTROL Import] är tillgänglig även efter ett valideringsfel'
description: Använd ACSD-58325-korrigeringen för att åtgärda Adobe Commerce-problemet där knappen [!UICONTROL Import] är tillgänglig även efter ett valideringsfel.
feature: Data Import/Export
role: Admin, Developer
exl-id: 551a9ac7-9b7f-49b5-9255-2014c330fb07
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# ACSD-58325: Knappen [!UICONTROL Import] är tillgänglig även efter ett valideringsfel

ACSD-58325-korrigeringen åtgärdar ett problem där knappen **[!UICONTROL Import]** är tillgänglig även efter ett valideringsfel. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 är installerad. Korrigerings-ID är ACSD-58325. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Knappen [!UICONTROL Import] är tillgänglig även efter ett valideringsfel.

<u>Steg som ska återskapas</u>:

1. Skapa CSV-filen för produktimporten med ett felaktigt bildnamn i filen.
1. Skapa en schemalagd produktimport med den skapade CSV-filen.
1. Vänta tills den schemalagda importen har slutförts.
1. Kontrollera [!UICONTROL Last outcome] i **[!UICONTROL Scheduled Imports/Exports]**-rutnätet.

<u>Förväntade resultat</u>:

[!UICONTROL Last outcome] ska vara [!UICONTROL Failed].

<u>Faktiska resultat</u>:

[!UICONTROL Last outcome] är [!UICONTROL Successful].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
