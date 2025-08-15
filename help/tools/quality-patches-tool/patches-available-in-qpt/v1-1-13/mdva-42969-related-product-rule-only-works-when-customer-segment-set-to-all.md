---
title: 'MDVA-42969: Relaterad produktregel fungerar bara när kundsegmentet är inställt på alla'
description: Korrigeringen MDVA-42969 åtgärdar ett problem där den relaterade produktregeln bara fungerar när kundsegmentet är inställt på alla. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 är installerat. Korrigerings-ID är MDVA-42969. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Customer Service, Marketing Tools, Products
role: Admin
exl-id: 121da040-4541-468a-aeaf-cf98094e1918
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-42969: Relaterad produktregel fungerar bara när kundsegmentet är inställt på alla

Korrigeringen MDVA-42969 åtgärdar ett problem där den relaterade produktregeln bara fungerar när kundsegmentet är inställt på alla. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 är installerat. Korrigerings-ID är MDVA-42969. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Relaterad produktregel fungerar bara när kundsegmentet är inställt på alla.

<u>Steg som ska återskapas</u>:

1. Gå till **Lager** > **Konfiguration** > **Katalog** > **Regelbaserade produktrelationer** och ange **Visa relaterade produkter** = **Regelbaserad endast**.
1. Gå till **Kunder** > **Segment** och skapa ett nytt segment: **Använd för** = **Besökare och registrerade kunder**.
1. Gå till **Marknadsföring** > **Relaterade produktregler** och skapa en ny regel.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Öppna den matchande produkten i butiken och kontrollera att Produkterna som ska visas visas.
1. Ändra regeln som skapades i steg tre och ange **kundsegment** = **Specifik** > **Segment** från steg två.
1. Öppna den matchande produkten i butiken.

<u>Förväntade resultat</u>:

Regelbaserade relaterade produkter visas i butiken för besökare i produkten eftersom kundsegmentet skapas med följande konfiguration:

**Gäller för** = **Besökare och registrerade kunder**

<u>Faktiska resultat</u>:

Inga relaterade produkter visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
