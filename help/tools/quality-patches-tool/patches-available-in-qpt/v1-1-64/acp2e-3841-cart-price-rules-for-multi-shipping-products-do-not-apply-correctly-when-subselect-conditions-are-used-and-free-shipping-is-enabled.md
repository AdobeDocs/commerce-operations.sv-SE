---
title: 'AVS2E-3841: Kundprisregler för produkter med flera leveranser gäller inte korrekt när vissa villkor används och fri frakt är aktiverat'
description: Använd programfixen ACP2E-3841 för att åtgärda Adobe Commerce-problemet där kundprisreglerna för produkter som levereras flera gånger inte gäller korrekt när delvalsvillkoren används och fri frakt är aktiverat.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 73979b71-9b15-4a4b-a1c9-37d3213c177f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# AVS2E-3841: Kundprisregler för produkter med flera leveranser gäller inte korrekt när vissa villkor används och fri frakt är aktiverat

Programfixen ACP2E-3841 åtgärdar ett problem där kundvagnsregler för produkter med flera leveranser inte gäller korrekt när delvalsvillkor används och fri frakt är aktiverat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 har installerats. Korrigerings-ID är ACP2E-3841. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p9

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.7-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kundprisreglerna för produkter som levereras flera gånger gäller inte korrekt när vissa villkor används och fri frakt är aktiverat.

<u>Förutsättningar</u>:

**Inställningar:**
1. **[!UICONTROL Free Shipping]** = *Aktiverad*
1. **[!UICONTROL Minimum Order Amount]** = *99999999*

**Kategorier som behövs:**
1. Kategoriprovning 1
1. Kategoriprovning 2

**Nödvändiga produkter:**
1. Produkttest 1:
   1. Kategorier: Kategoriprovning 1
   1. Pris: 45 $
1. Produkttest 2:
   1. Kategorier: Kategoriprovning 2
   1. Pris: 56,25 $ 

      **(Priserna måste vara desamma som visas här för att testet ska fungera korrekt.)**

**Kundprisregel:**

Logga in som administratör och gå till **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add new rule]**. Använd dessa värden:

**[!UICONTROL Rule Information]:**
1. **[!UICONTROL Rule Name]**: Testa gratis leverans
1. **[!UICONTROL Active]**: *Ja*
1. **[!UICONTROL Websites]**: *Huvudwebbplats*
1. **[!UICONTROL Customer Groups]**: *INGEN INLOGGAD, ALLMÄN, Grossist, Återförsäljare*
1. **[!UICONTROL Coupon]**: *Ingen kupong*
1. **[!UICONTROL Uses per Customer]**: *0*
1. **[!UICONTROL Priority]**: *1*

**[!UICONTROL Conditions]:**

**[!UICONTROL If ALL of these conditions are TRUE:]**


**[!UICONTROL If total amount (incl. tax) equals or greater than 100 for a subselection of items in cart matching ALL of these conditions:]**


**[!UICONTROL Category is]** *5,12,13*

Funktionsmakron:

**[!UICONTROL Percent of product price discount]** = *10*

<u>Steg som ska återskapas</u>:

1. Logga in på butikens framsida.
2. Lägg till produkttest 1.
3. Lägg till två kvantiteter i produkttest 2.
4. Besök kundvagnen.
5. Välj **[!UICONTROL Check Out with Multiple Addresses]**.

<u>Förväntade resultat</u>:

Inga fel.

<u>Faktiska resultat</u>:

*500 fel*

*Meddelande: Funktioner som inte används: Implicit konvertering från flyttal 112.5 till heltal förlorar precision i /app/code/Magento/SalesRule/Model/Rule/Condition/Product/Subselect.php på rad 214*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
