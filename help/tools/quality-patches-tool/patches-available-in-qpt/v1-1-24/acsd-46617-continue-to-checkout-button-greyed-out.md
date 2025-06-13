---
title: 'ACSD-46617: **[!UICONTROL Continue to Checkout]**-knapp nedtonad när delsumman är större än det konfigurerade minimiorderbeloppet'
description: Använd korrigeringsfilen ACSD-46617 för att lösa Adobe Commerce-problemet där knappen **[!UICONTROL Continue to Checkout]** är nedtonad även om delsumman är större än det konfigurerade minimiantalet order.
feature: Checkout, Orders
role: Admin
exl-id: 8e808fce-d31c-49ef-94e5-f5c89fffaa73
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-46617: Knappen [!UICONTROL Continue to Checkout] är nedtonad när delsumman överstiger [!UICONTROL Minimum Order Amount]

Den här ACSD-46617-korrigeringen löser problemet där knappen **[!UICONTROL Continue to Checkout]** är nedtonad även om delsumman är större än den konfigurerade minimiordermängden. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 har installerats. Korrigerings-ID är ACSD-46617. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Knappen **[!UICONTROL Continue to Checkout]** är nedtonad även om delsumman är större än det konfigurerade minimiorderbeloppet.

<u>Steg som ska återskapas</u>:

1. Gå till Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** och ange följande:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * &#x200B;

     [!UICONTROL Minimum Amount]: *2*

1. Skapa en [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * &#x200B;

        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Skapa en produkt till priset av 25 USD.
1. Lägg produkten i kundvagnen.
1. Gå till kundvagnen, välj metoden $5 **[!UICONTROL Flat Rate shipping]** och använd kupongkoden.
1. Gå till kassan, slutför leveransen och navigera till avsnittet **[!UICONTROL Paytment]**.
1. Gå tillbaka till kundvagnen.

<u>Förväntade resultat</u>:

Det finns inget fel relaterat till minimiorderbeloppet eftersom totalsumman på $2.4 är större än vad som krävs på $2.

<u>Faktiska resultat</u>:

* Det finns ett fel relaterat till minimiorderbeloppet även när totalsumman på $2.4 är större än minimiorderbeloppet på $2.
* Knappen **[!UICONTROL Continue to Checkout]** är nedtonad.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
