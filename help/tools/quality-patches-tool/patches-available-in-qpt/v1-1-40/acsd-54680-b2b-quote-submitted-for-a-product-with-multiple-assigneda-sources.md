---
title: "ACSD-54680: B2B-offert för en produkt med flera tilldelade källor kan inte bearbetas"
description: Använd patchen ACSD-54680 för att åtgärda Adobe Commerce-problemet där B2B-offerten för en produkt med flera tilldelade källor inte kan bearbetas.
feature: B2B
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-54680: B2B-offert för en produkt med flera tilldelade källor kan inte behandlas.

Korrigeringen ACSD-54680 åtgärdar ett problem där B2B-offerten för en produkt med flera tilldelade källor inte kan bearbetas. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.40 har installerats. Korrigerings-ID är ACSD-54680. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

B2B-offert för en produkt med flera tilldelade källor kan inte bearbetas.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** och skapa två nya källor: **Source 1** och **Source 2**.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** och skapa en ny Stock: **Stock A**, tilldela den till huvudwebbplatsen och tilldela **Source 1** och **Source 2** till den.
1. Skapa en enkel produkt, tilldela **Source 1** och **Source 2** och ange Kvantitet = *2* för varje källa. (produktens säljbara kvantitet bör därför vara *4*).
1. Skapa ett företag.
1. Gå till **[!UICONTROL Storefront]** och logga in på företagskontot.
1. Lägg den enkla produkten i kundvagnen med kvantitet = *4*.
1. Öppna *[!UICONTROL Shopping cart]* och klicka på knappen **[!UICONTROL Request a quote]**.
1. Lägg till en kommentar och ett citattecken och klicka på knappen **[!UICONTROL Send a Request]**.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Öppna nyligen skickad offert.

<u>Förväntade resultat</u>:

De angivna artiklarna innehåller den beställda produkten.

<u>Faktiska resultat</u>:

Sidavsnittet med citattecken är tomt och det går inte att bearbeta citattecknet.
`var/log/system.log` innehåller

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
