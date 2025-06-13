---
title: 'ACSD-46581: Den beräknade momssumman uppdateras inte när du har valt ett land i kundvagnen'
description: Använd patchen ACSD-46581 för att lösa problemet med Adobe Commerce där momssatsen inte uppdateras efter att landet bytt i kundvagnen.
feature: Orders, Shopping Cart
role: Admin
exl-id: 45800055-8556-4f87-8938-c6be5d82938d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-46581: Den beräknade momssumman uppdateras inte när du har valt ett land i kundvagnen

Denna ACSD-46581-korrigering löser problemet där skattesatsen inte uppdateras efter att landet bytt i kundvagnen. Den uppdateras först när du har valt leveranssätt. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21 har installerats. Korrigerings-ID är ACSD-46581. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.1-p1

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Momssatsen uppdateras inte när landet har bytt i kundvagnen.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]** i Adobe Commerce Admin.
1. Skapa en ny skattesats för **[!UICONTROL Country]** = _USA_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8.25_.
1. Skapa en ny skattesats för **[!UICONTROL Country]** = _Indien_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_.
1. Skapa en skatteregel med både skattesatser för USA och Indien.
1. Gå till **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** och aktivera mer än en leveransmetod (_Platt hastighet_ och _Fri frakt_ till exempel).
1. Skapa en enkel produkt med skatteklassen **[!UICONTROL Taxable Goods]**.
1. Lägg produkten i varukorgen på butikens framsida.
1. Öppna kundvagnen och kontrollera momsbeloppet.
1. Standardskatteinställningarna för USA används och momsen beräknas baserat på en 8,25-procentig skattesats.
1. Byt land till Indien.

<u>Förväntade resultat</u>:

Skattebeloppet ändrades till 10 % när landet bytte till Indien.

<u>Faktiska resultat</u>:

Momsbeloppet är detsamma i kundvagnens totala avsnitt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
