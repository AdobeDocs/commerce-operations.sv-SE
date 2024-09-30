---
title: 'ACSD-54067: Produktvideon spelas inte upp på den mobila enheten'
description: Använd patchen ACSD-54067 för att åtgärda Adobe Commerce-problemet där en produktvideo inte spelas upp på en mobil enhet.
feature: Media, Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54067: Produktvideo spelas inte upp på en mobil enhet

Korrigeringen ACSD-54067 åtgärdar ett problem där en produktvideo inte spelas upp på en mobil enhet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 är installerad. Korrigerings-ID är ACSD-54067. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En produktvideo kan inte spelas upp på en mobil enhet.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce.
1. Kör kommandot:
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Gå till sidan **[!UICONTROL Admin product list]** och filtrera efter *[!UICONTROL SKU product_dynamic_120]*.
1. Öppna produktsidan och gå till **[!UICONTROL Images and Videos]** > lägg till en video > fyll i URL:en: https://vimeo.com/347119375 och spara.
1. Gå till butiken och öppna produktsidan för *[!UICONTROL product_dynamic_120]*.
1. Ställ in webbläsaren på *mobil enhet* med bredden *320px* och uppdatera.
1. Markera videon i gallerireglaget och klicka för att spela upp den.

<u>Förväntade resultat</u>:

Produktvideon spelas upp.

<u>Faktiska resultat</u>:

Produktvideon spelas inte upp.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
