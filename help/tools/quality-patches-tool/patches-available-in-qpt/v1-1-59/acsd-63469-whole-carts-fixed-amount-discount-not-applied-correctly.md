---
title: 'ACSD-63469: Kundrabatter med fast belopp tillämpas inte korrekt med flera regler'
description: Använd patchen ACSD-63469 för att åtgärda Adobe Commerce-problemet där rabatter med fast belopp för hela kundvagnen inte gäller korrekt när mer än en regel används.
feature: Price Rules
role: Admin, Developer
source-git-commit: 3699a9f64198558fcf1ffe53753f035d22c2d301
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---


# ACSD-63469: Kundrabatter med fast belopp tillämpas inte korrekt med flera regler

Korrigeringsfilen ACSD-63469 åtgärdar ett problem där rabatter med fast belopp för hela vagnen inte gäller korrekt när mer än en regel tillämpas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 har installerats. Korrigerings-ID är ACSD-63469. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När flera **[!UICONTROL Fixed amount discount for whole cart]**-regler används samtidigt och produkterna har rabatterade eller specialpriser, beräknas rabattvärdet felaktigt.

<u>Steg som ska återskapas</u>:

1. Skapa två produkter med priset 850 USD och 85 USD och ange specialpriset till 765 USD respektive 68 USD.
1. Skapa två **[!UICONTROL Cart Price Rules]** enligt följande:
   * Regel 1
      * **[!UICONTROL Conditions]**: För produkten $850 anger du *Kvantitet* till *lika med eller större än 2*
      * **[!UICONTROL Actions]**: Använd **[!UICONTROL Fixed amount discount for whole cart]** av *$153*
   * Regel 2
      * **[!UICONTROL Conditions]**: För produkten $85 anger du *Kvantitet* till *lika med eller större än 2*
      * **[!UICONTROL Actions]**: Använd **[!UICONTROL Fixed amount discount for whole cart]** av *$14*
1. Lägg båda produkterna i varukorgen, var och en med en kvantitet på 2.

<u>Förväntade resultat</u>:

Rabatten i kundvagnen är 167 dollar.

<u>Faktiska resultat</u>:

Rabatten i kundvagnen är 41 dollar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Ytterligare steg krävs efter installationen av korrigeringsfilen

(Det här avsnittet är valfritt. Det kan finnas åtgärder som krävs efter att du har implementerat korrigeringen för att åtgärda problemet.) 

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.

