---
title: 'ACSD-62971: Import av Stock-källor med icke-numeriska kvantitetsvärden resulterar i att kvantiteten ställs in på 0'
description: Använd patchen ACSD-62971 för att korrigera Adobe Commerce-problemet, där import av Stock-källor med icke-numeriska värden i kolumnen 'quantity' resulterar i att kvantiteten ställs in på 0.
feature: Data Import/Export, Inventory
role: Admin, Developer
source-git-commit: 5b54c0681b699303fff1bb058d434b6eb8b750b0
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# ACSD-62971: Import av Stock-källor med icke-numeriska kvantitetsvärden resulterar i att kvantiteten ställs in på 0

Korrigeringen ACSD-62971 åtgärdar ett problem där import av Stock-källor med icke-numeriska värden i kolumnen &#39;quantity&#39; resulterar i att kvantiteten ställs in på 0. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 har installerats. Korrigerings-ID är ACSD-62971. Observera att problemet var planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Korrigerar problemet där import av Stock-källor med icke-numeriska värden i kolumnen **[!UICONTROL Quantity]** resulterar i att kvantiteten ställs in på 0.

<u>Steg som ska återskapas</u>:

1. Skapa **[!UICONTROL Simple Product]** med kvantitet=100
1. Gör en **[!UICONTROL Stock Sources]**-import med filen som har ett felaktigt antal (&quot;abc&quot;)

   ```table
   source_code    sku    status    quantity
     default     simple    1         abc
   ```

1. Kontrollera kvantiteten efter importen.

<u>Förväntade resultat</u>:
Valideringen av importdata bör misslyckas.

<u>Faktiska resultat</u>:
Kvantiteten för enkel produkt har blivit 0 och produkten uppdateras som [!UICONTROL Out of Stock].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.

