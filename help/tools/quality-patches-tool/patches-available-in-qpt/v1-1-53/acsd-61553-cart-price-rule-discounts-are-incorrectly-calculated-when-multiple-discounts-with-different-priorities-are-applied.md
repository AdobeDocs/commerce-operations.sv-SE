---
title: 'ACSD-61553: [!UICONTROL Cart Price Rule] beräknas felaktigt när flera rabatter med olika prioriteter används'
description: Använd ACSD-61553-korrigeringen för att lösa Adobe Commerce-problemet där [!UICONTROL Cart Price Rule] inte beräknas korrekt när flera rabatter med olika prioriteter tillämpas.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 0fb7a988-d391-49e5-a59d-62315a16132c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-61553: [!UICONTROL Cart Price Rule] beräknas felaktigt när flera rabatter med olika prioriteter används

Korrigeringen ACSD-61553 åtgärdar ett problem där [!UICONTROL Cart Price Rule] inte beräknas korrekt när flera rabatter med olika prioriteter tillämpas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.53 är installerad. Korrigerings-ID är ACSD-61553. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.5-p8

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!UICONTROL Cart Price Rule] beräknas felaktigt när flera rabatter med olika prioriteter används.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt till priset 9 000 USD.
1. Skapa en [!UICONTROL Cart Price Rule]: Regel A med en fast rabatt på 700 USD utan villkor och utan att efterföljande regler ignoreras.
1. Skapa ytterligare [!UICONTROL Cart Price Rule]: Regel B med en fast rabatt på 1 000 USD utan villkor och utan att efterföljande regler ignoreras.
1. Lägg produkten med kvantiteten 13 i kundvagnen.
1. Uppdatera reglerna med något av följande scenarier:

   scenario 01

       Regel A
       Prioritet: 1
       Maximal mängdrabatt används för: 1
       
       Regel B
       Prioritet: 0
        Maximal mängdrabatt används för: 0
   
   Scenario 02

       Regel A
       Prioritet: 0
       Maximal mängdrabatt används för: 0
       
       Regel B
       Prioritet: 1
        Maximal mängdrabatt används för: 1
   
   scenario 03

       Regel A
       Prioritet: 0
       Maximal mängdrabatt används för: 0
       
       Regel B
       Prioritet: 0
        Maximal mängdrabatt används för: 1
   
1. Klicka på knappen **[!UICONTROL Update Shopping Cart]** om du vill räkna om rabatterna.

<u>Förväntade resultat</u>:

Följande totalrabatt visas för olika scenarier:

    Scenario 01: $13,700
    Scenario 02: $10,100
    Scenario 03: $10,100

<u>Faktiska resultat</u>:

I alla tre scenarierna är den totala rabatten 9 000 dollar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!DNL Quality Patches Tool].

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
