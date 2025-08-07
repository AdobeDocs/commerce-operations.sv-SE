---
title: 'ACSD-66084: "row_total_incl_tax" returnerar ett restvärde nära noll i stället för 0,00 för fullt rabatterade artiklar i order-API-svaret'
description: Använd patchen ACSD-66084 för att åtgärda Adobe Commerce-problemet där "row_total_incl_tax" returnerade ett restvärde nära noll istället för 0,00 för fullt rabatterade objekt i order-API-svaret.
feature: Orders, REST, Taxes, Payments, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: 01f7059e53590c4ff6602c41eb980ac7c141af33
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---


# ACSD-66084: `row_total_incl_tax` returnerar ett restvärde nära noll i stället för 0,00 för fullständigt rabatterade objekt i order-API-svaret

Korrigeringen ACSD-66084 åtgärdar ett problem där `row_total_incl_tax` returneras som ett nästan noll restvärde i order-API-svaret i stället för 0,00 för fullständigt rabatterade artiklar. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 har installerats. Korrigerings-ID är ACSD-66084. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`row_total_incl_tax` returneras som ett nästan-noll restvärde i order-API-svaret i stället för 0,00 för fullständigt rabatterade artiklar.

<u>Steg som ska återskapas</u>:

1. Skapa en produkt till ett pris och till ett specialpris. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > Klicka på **[!UICONTROL Add Product]** > ange **[!UICONTROL Price]** till $25 och **[!UICONTROL Special Price]** till $16.99 under **[!UICONTROL Advanced Pricing]**.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Zones and Rates]** och lägg till en 20-procentig frekvens. Gå sedan till **[!UICONTROL Tax Rules]** och skapa en regel och tilldela
   **[!UICONTROL Taxable Goods]** som produktskatteklass.
1. Skapa en försäljningsregel med 100 % rabatt och kupong. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** och lägg till en regel med 100 % rabatt. Använd sedan **[!UICONTROL Specific Coupon]** och ange koden.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > och konfigurera skatteinställningar.
1. Möjliggör fri frakt. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL Free Shipping]**. Ange **[!UICONTROL Enabled]** till **[!UICONTROL Yes]** och justera inställningarna.
1. Gå till produktsidan och välj **[!UICONTROL Add to Cart]**. Gå till kundvagnen och ange kupongkoden.
1. Lägg ordern i den tillämpliga skattezonen.
1. Generera en administratörstoken (API) via REST API.
1. Hämta orderinformation via REST API.
1. Kontrollera `row_total_incl_tax` i svaret.

<u>Förväntade resultat</u>:

`row_total_incl_tax` ska returnera ett valutakänsligt värde som `0.00` när objektet är helt rabatterat.

<u>Faktiska resultat</u>:

`row_total_incl_tax` returnerar ett flyttalsvärde som är nästan noll som `3.5527136788005e-15`, vilket inte är lämpligt för visning av valuta.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
