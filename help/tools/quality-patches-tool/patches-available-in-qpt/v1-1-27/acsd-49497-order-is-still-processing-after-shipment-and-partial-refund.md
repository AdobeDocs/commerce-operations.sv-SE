---
title: 'ACSD-49497: Beställning som fortfarande bearbetas efter leverans och partiell återbetalning'
description: Använd patchen ACSD-49497 för att åtgärda Adobe Commerce-problemet där orderstatusen kvarstår som behandling efter leverans och en partiell återbetalning tillämpas.
feature: Admin Workspace, Orders, Shipping/Delivery
role: Admin
exl-id: e2e3d2b3-24be-4827-a735-aebfc6f475ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-49497: Beställning som fortfarande bearbetas efter leverans och partiell återbetalning

Korrigeringsfilen ACSD-49497 åtgärdar ett problem där orderstatusen kvarstår som behandling efter leverans och en partiell återbetalning tillämpas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 är installerad. Korrigerings-ID är ACSD-49497. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Statusen för en ny order ligger kvar i läget *[!UICONTROL Processing]* även efter leverans och en partiell återbetalning tillämpas.

<u>Steg som ska återskapas</u>:

1. Skapa en order med flera artiklar.
1. Skapa en faktura för ordern från **[!UICONTROL Admin]**.
1. Från **[!UICONTROL Admin]** skapar du en kreditnota och återbetalar endast delvis en artikel.
1. Från **[!UICONTROL Admin]**, begär frakt för återstående artiklar i ordern.
1. Observera orderstatus.

<u>Förväntade resultat</u>:

Orderns status ska vara *[!UICONTROL Complete]*.

<u>Faktiska resultat</u>:

Orderns status är fortfarande *[!UICONTROL Processing]*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
