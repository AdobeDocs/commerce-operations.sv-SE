---
title: 'ACSD-63062: Felaktiga kundrabattberäkningar med flera överlappande regler'
description: Använd patchen ACSD-63062 för att åtgärda Adobe Commerce-problemet där felaktiga kundrabattberäkningar inträffar när flera överlappande regler tillämpas.
feature: Price Rules
role: Admin, Developer
source-git-commit: 06fbdf730c670065e3105c62ae9604307b296a45
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63062: Felaktiga kundrabattberäkningar med flera överlappande regler

Korrigeringsfilen ACSD-63062 åtgärdar ett problem där felaktiga kundrabattberäkningar inträffar när flera överlappande regler tillämpas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 har installerats. Korrigerings-ID är ACSD-63062. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felaktiga beräkningar av kundvagnsrabatt inträffar när flera överlappande regler tillämpas.

<u>Steg som ska återskapas</u>:

1. Installera en ny instans med exempeldata.
1. Skapa tre enkla produkter:

   * enkel1: $1080
   * simple2: $260
   * enkel3: $280

1. Skapa fyra *[!UICONTROL Cart Price Rules]* enligt följande:

   * Regel 1:

      * *[!UICONTROL Priority]*: 100
      * fliken *[!UICONTROL Conditions]*: Använd enkel2-produkt ($280) om den totala kvantiteten är lika med eller större än 3
      * Fliken *[!UICONTROL Actions]*: SKU är enkelt2
      * *[!UICONTROL Fixed Amount Discount]*: $80

   * Regel 2:

      * *[!UICONTROL Priority]*: 200
      * Fliken *[!UICONTROL Actions]*: SKU är enkelt2
      * *[!UICONTROL Percentage of Product Price Discount]*: 20 %

   * Regel 3:

      * *[!UICONTROL Priority]*: 300
      * Fliken *[!UICONTROL Conditions]*: Delsumman är lika med eller större än $1000
      * *[!UICONTROL Fixed Amount Discount]* för hela vagnen: $100

   * Regel 4:

      * *[!UICONTROL Priority]*: 400
      * fliken *[!UICONTROL Conditions]*: Använd enkel1 ($1080) produkt om den totala kvantiteten är lika med eller större än 2
      * Fliken *[!UICONTROL Actions]*: SKU är enkel1
      * *[!UICONTROL Fixed Amount Discount]* för hela vagnen: 960 dollar

1. Gå till butiken och lägg till följande produkter med angiven kvantitet i vagnen:

   * simple1 = 2
   * simple2 = 1
   * simple3 = 3

1. Kolla kundvagnen.

<u>Förväntade resultat</u>:

Rabatten är 1 352 dollar.

<u>Faktiska resultat</u>:

Rabatten är 1 525,33 USD.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
