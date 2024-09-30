---
title: 'ACSD-50527: Fel vid sparande av en sida med tomt dynamiskt block'
description: Använd korrigeringsfilen ACSD-50527 för att åtgärda Adobe Commerce-problemet när ett fel inträffar när en sida sparas med ett tomt dynamiskt block.
feature: Page Content
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-50527: Fel vid sparande av en sida med tomt dynamiskt block

Korrigeringen ACSD-50527 åtgärdar ett problem där ett fel inträffar när en sida sparas med ett tomt dynamiskt block. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 är installerad. Korrigerings-ID är ACSD-50527. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel inträffar när en sida med ett tomt dynamiskt block sparas.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Dynamic Block]** och skapa ett nytt dynamiskt block med tomt innehåll.
1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Create or Edit a new page]**.
1. Lägg till två radelement i innehållet. Lägg sedan till det nya dynamiska blocket som skapas ovan.

<u>Förväntade resultat</u>:

Inget fel visas för ett dynamiskt block med tomt innehåll i [!DNL Page Builder].

<u>Faktiska resultat</u>:

Platshållaren [!UICONTROL Dynamic Block] visar felet:

>[!ERROR]
>
>Ett okänt fel uppstod. Försök igen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
