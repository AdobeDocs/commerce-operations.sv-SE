---
title: 'ACSD-48587: produktwidgeten fungerar inte med SKU:er som innehåller HTML-tecken'
description: Använd patchen ACSD-48587 för att åtgärda Adobe Commerce-problemet där HTML-specialtecken i matchningsreglerna för produktwidgeten förhindrar att de visar matchande produkter.
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48587: produktwidgeten fungerar inte med SKU:er som innehåller HTML-tecken

Korrigeringen ACSD-48587 åtgärdar ett problem där HTML-specialtecken i matchningsreglerna för produktwidgetar förhindrar att de visar matchande produkter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 har installerats. Korrigerings-ID är ACSD-48587. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktwidgeten fungerar inte med SKU:er som innehåller *-&amp;*-symboler.

<u>Steg som ska återskapas</u>:

1. Skapa en produkt som innehåller *&amp;* i SKU:n (t.ex. s000&amp;01).
1. Redigera innehållet på en CMS-sida på *Page Builder*.
1. Lägg till en produktwidget.
1. Redigera widgeten och ange **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. Ange SKU:n som innehåller *&amp;* i produktfältet.
1. Spara innehållet och CMS-sidan.
1. Kontrollera *CMS Page* -innehållet för *Page Builder-förhandsvisningen* och produktbutiken.

<u>Förväntade resultat</u>:

Produkten med *&quot;&amp;&quot;*&quot; i SKU:n visas i förhandsvisningen i Page Builder och i butiken.

<u>Faktiska resultat</u>:

Produkten med *&amp;* i SKU:n visas inte i förhandsvisningen i Page Builder.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
