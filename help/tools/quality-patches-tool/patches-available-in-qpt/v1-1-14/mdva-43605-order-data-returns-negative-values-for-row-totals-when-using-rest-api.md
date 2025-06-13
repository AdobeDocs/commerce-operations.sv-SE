---
title: 'MDVA-43605: Orderdata returnerar negativa värden för radsummor när Rest API används'
description: Korrigeringen MDVA-43605 åtgärdar ett problem där orderdata returnerar negativa värden för radsummor när Rest API används. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 är installerat. Korrigerings-ID är MDVA-43605. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: REST, Orders
role: Admin
exl-id: f27439a6-eeee-4176-9ac9-98220752db3f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-43605: Orderdata returnerar negativa värden för radsummor när Rest API används

Korrigeringen MDVA-43605 åtgärdar ett problem där orderdata returnerar negativa värden för radsummor när Rest API används. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 är installerat. Korrigerings-ID är MDVA-43605. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.1 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Orderdata returnerar negativa värden för radsummor när Rest API används.

<u>Steg som ska återskapas</u>:

1. Möjliggör fri frakt.
1. Navigera till **Konfiguration** > **Katalog** > **Pris** > och ange Katalogens prisomfång = webbplats.
1. Navigera till **Konfiguration** > **Försäljning** > **Moms** och uppdatera:
   * Skatteklass för leverans = skattepliktiga varor
   * Beräkningsinställningar:
      * Katalogpris = inklusive moms
      * Leveranspris = inklusive pris
      * Tillämpar rabatt på priser = inklusive moms
   * Prisvisningsinställningar: Inklusive moms (alla fält)
   * Visningsinställningar för kundvagn: Inklusive moms (alla fält)
   * Beställningar, fakturor, kreditnotor:
      * Visa leveransbelopp = inklusive moms
1. Skapa en skattesats för USA (delstat = &#39;*&#39;), Rate Percent = 24.00
1. Skapa en momsregel med momssats ovan.
1. Skapa en kundvagnsprisregel med en viss kupong och Rabatt = $50 av det fasta beloppet för hela vagnen.
1. Skapa fyra produkter till följande priser: $8,90, $5,90, $6,90 och $5,95.
1. Skapa en administratörsorder som innehåller fyra av dessa produkter med kupongkoden som skapades i föregående steg. Fraktfritt.
1. Betalning bör inte krävas eftersom kupongkoden täcker kundvagnssumman.
1. Hämta den ordning som skapades via Rest API-slutpunkten:

   ```json
   GET rest/V1/orders/1
   ```

<u>Förväntade resultat</u>:

Värdena för `base_row_total` och `base_row_total_incl_tax` i svaret är noll.

<u>Faktiska resultat</u>:

Fälten `base_row_total` och `base_row_total_incl_tax` i svaret har negativa värden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
