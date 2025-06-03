---
title: 'ACSD-65127: JavaScript-miniatyrer i produktionsläge orsakar  [!DNL TinyMCE] 6 fel i webbläsaren'
description: Använd korrigeringsfilen ACSD-65127 för att åtgärda Adobe Commerce-problemet där aktivering av JavaScript-miniatyr i produktionsläge orsakade  [!DNL TinyMCE] 6 att fel genererades i webbläsarkonsolen, vilket påverkade funktionaliteten och användarupplevelsen.
feature: Page Builder, Page Content
role: Admin, Developer
source-git-commit: c5b27b79dd2dc7f9b39e629756d3d5d01e019710
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# ACSD-65127: JavaScript-miniatyrer i produktionsläge orsakar [!DNL TinyMCE] 6 fel i webbläsaren

Korrigeringen ACSD-65127 åtgärdar ett problem där aktivering av JavaScript-miniatyrbilder i produktionsläge orsakade att [!DNL TinyMCE] 6 genererade fel i webbläsarkonsolen, vilket påverkar funktionaliteten och användarupplevelsen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 har installerats. Korrigerings-ID är ACSD-65127. Observera att detta problem har åtgärdats i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du paketet `magento/quality-patches` till den senaste versionen och kontrollerar kompatibiliteten på sidan [[!DNL Quality Patches Tool]: Sök efter korrigeringar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om JavaScript-miniatyrbilder aktiverades i produktionsläget genererade [!DNL TinyMCE] 6 fel i webbläsarkonsolen, vilket påverkade funktionaliteten och användarupplevelsen.

<u>Steg som ska återskapas</u>:

1. Ange konfigurationen genom att köra kommandona nedan:

```
bin/magento config:set --lock-config dev/js/minify_files 1
bin/magento config:set --lock-config dev/js/enable_js_bundling 1
bin/magento config:set --lock-config dev/js/merge_files 1
```

1. Aktivera produktionsläge.

```
bin/magento deploy:mode:set production
```

1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** på sidlisten Admin. Klicka på **[!UICONTROL Edit]** på en produkt i listan och bläddra nedåt till **[!UICONTROL Content]** och välj **[!UICONTROL Show Editor]**.

<u>Förväntade resultat</u>:

Inga JS-fel i webbläsarkonsolen.

<u>Faktiska resultat</u>:

*404* fel i webbläsarkonsolen för js `tiny_mce_6/plugins/help/js/i18n/keynav/en.js`.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
