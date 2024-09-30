---
title: '"MDVA-39482: Produkten slutar att vara i lager om den importeras med kvantiteten "0" och backorenheter är aktiverade"'
description: MDVA-39482 åtgärdar ett problem där produkten lämnar lagret om den importeras med "0"-kvantitet när MSI och efterbeställningar är aktiverade och där tröskelvärdet för lagerutleverans är inställt på ett minus-värde. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 är installerat. Korrigerings-ID är MDVA-39482. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 1fb76b8d648cbbe2a9f602d2b1a0149f1f4f0e46
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39482: Produkten slutar att vara i lager om den importeras med kvantiteten &quot;0&quot; med bakåtorder aktiverade

MDVA-39482 åtgärdar ett problem där produkten lämnar lagret om den importeras med &quot;0&quot;-kvantitet när MSI och efterbeställningar är aktiverade och där tröskelvärdet för lagerutleverans är inställt på ett minus-värde. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 har installerats. Korrigerings-ID är MDVA-39482. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.1-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produkten hamnar utanför lagret om den importeras med kvantiteten &quot;0&quot; när MSI och efterbeställningar är aktiverade och tröskelvärdet för lagerutleverans är inställt på ett minus-värde.

<u>Förutsättningar</u>:

1. MSI och exempeldata måste vara installerade.
1. Gå till **Lager** > **Konfigurationer** > **Katalog** > **Lager**:
   * Ställ in bakordrar till&quot;Tillåt kvantitet under 0&quot;
   * Ställ in ej lagrad tröskel till -10

<u>Steg som ska återskapas</u>:

1. Kontrollera att SKU:n är **I Stock** och har kvantiteten **24-MB01**.
1. Importera Stock Sources CSV. Se till att du väljer Stock Sources i Entity Type:

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Kontrollera produktens lagerstatus efter att Stock-källorna har importerats.

<u>Förväntade resultat</u>:

24 MB01 är **I Stock** i Storefront.

<u>Faktiska resultat</u>:

24 MB01 är **Utanför lager** i Storefront.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
