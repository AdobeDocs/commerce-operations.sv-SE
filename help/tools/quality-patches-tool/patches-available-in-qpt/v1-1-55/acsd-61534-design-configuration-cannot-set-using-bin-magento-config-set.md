---
title: 'ACSD-61534: Det går inte att ställa in designkonfigurationen med bin/magento config:set, och låsta värden kan ändras med formulärmanipulering'
description: Använd patchen ACSD-61534 för att åtgärda Adobe Commerce-problemet där designkonfigurationen inte kan ställas in med kommandot "bin/magento config:set" och låsta värden kan ändras genom formulärhantering.
feature: Configuration
role: Admin, Developer
source-git-commit: ef00c05593ad319caab8bb9e0f5090959786513f
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-61534: Det går inte att ange designkonfigurationen med `bin/magento config:set`, och låsta värden kan ändras via formulärhantering

Korrigeringen ACSD-61534 åtgärdar ett problem där designkonfigurationen inte kan anges med kommandot `bin/magento config:set` och låsta värden kan ändras med formulärhantering. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 är installerad. Korrigerings-ID är ACSD-61534. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att ange designkonfigurationen med kommandot `bin/magento config:set`, och låsta värden kan ändras med formulärhantering. Med den här korrigeringen kan låsta värden som angetts från kommandoradsverktyget (CLI) med `--lock-env` eller `--lock-conf` inte uppdateras.

<u>Steg som ska återskapas</u>:

1. Lås ett config-värde med en molnmiljövariabel, som `CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES`.
1. Gå till panelen *[!UICONTROL Admin]*.
1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Klicka på **[!UICONTROL Edit]** nära **[!UICONTROL Global/Main website]** på den andra raden.
1. Redigera tema för en butiksvy.
1. Öppna HTML i huvudet.
1. Aktivera det inaktiverade fältet **[!UICONTROL Scripts and Style Sheets]** med utvecklarverktygen.
1. Ändra värdet och spara det.

<u>Förväntade resultat</u>:

Det går inte att spara ett låst värde.

<u>Faktiska resultat</u>:

Tabellen `core_config_data` innehåller ett uppdaterat värde för `design/head/includes`.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
