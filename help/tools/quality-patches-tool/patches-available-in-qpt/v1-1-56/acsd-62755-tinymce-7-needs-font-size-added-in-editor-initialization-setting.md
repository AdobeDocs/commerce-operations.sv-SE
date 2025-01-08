---
title: 'ACSD-62755: [!DNL TinyMCE] 7 behöver teckenstorlek och teckensnitt som har lagts till i initieringsinställningarna för redigeraren'
description: Använd patchen ACSD-62755 för att åtgärda Adobe Commerce-problemet där  [!DNL TinyMCE]  7 kräver att *teckensnittsstorlek* och *teckensnittsfamilj* specifikt läggs till i initieringsinställningarna för redigeraren.
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
source-git-commit: 4aba81ea12cc08370881d3cc108e94ba410a2198
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# ACSD-62755: [!DNL TinyMCE] 7 behöver teckenstorlek och teckensnitt som har lagts till i initieringsinställningarna för redigeraren

Korrigeringen ACSD-62755 åtgärdar ett problem där [!DNL TinyMCE] 7 kräver att väljarna för *teckensnittsstorlek* och *teckensnittsfamilj* specifikt läggs till i initieringsinställningarna för redigeraren. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 är installerad. Korrigerings-ID är ACSD-62755. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.5-p10

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!DNL TinyMCE] 7 kräver att väljarna *font size* och *font family* specifikt läggs till i initieringsinställningarna för redigeraren.

<u>Steg som ska återskapas</u>:

Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]** och välj *[!UICONTROL Show Editor]*.

<u>Förväntade resultat</u>:

Väljarna för *teckensnittsstorlek* och *teckensnittsfamilj* visas i WYSIWYG Editor.

<u>Faktiska resultat</u>:

*Teckensnittsstorleksväljaren* saknas i WYSIWYG Editor.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
