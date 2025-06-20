---
title: 'ACSD-53636: Normalpris visas inte på sidan [!UICONTROL Product Listing]'
description: Använd korrigeringsfilen ACSD-53636 för att korrigera Adobe Commerce-problemet där normalpriset inte visas på *[!UICONTROL Product Listing]* sidor för konfigurerbara produkter som har underordnade produkter med specialpriser.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: e6d66ae4-2c21-466a-b03c-a1f486e7fa29
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-53636: Normalpris visas inte på sidan *[!UICONTROL Product Listing]*

Korrigeringen ACSD-53636 åtgärdar ett problem där det vanliga priset inte visas på *[!UICONTROL Product Listing]* sidor för konfigurerbara produkter som har underordnade produkter med specialpriser. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 har installerats. Korrigerings-ID är ACSD-53636. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Normalpriset visas inte på *[!UICONTROL Product Listing]* sidor för konfigurerbara produkter som har underordnade produkter med specialpriser.

<u>Steg som ska återskapas</u>:

1. Logga in på administratören och gå till **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** och skapa eller öppna en konfigurerbar produkt.
2. Öppna den underordnade produkten och lägg till ett specialpris för alla eller en av de underordnade produkterna och spara produkten.
3. Gå till frontend och öppna sidan **[!UICONTROL Product Detail]** för den konfigurerbara produkten. På färgrutorna för den underordnade produkten med specialpris visas *[!UICONTROL Regular price]* borttagen (förväntas).
4. Gå till frontend och öppna sidan **[!UICONTROL Product Listing]** för den konfigurerbara produkten med specialpris. Se till att det normala priset inte visas för den konfigurerbara produktfärgrutan, till skillnad från *[!UICONTROL Product Detail Page]* och andra enkla produkter.

<u>Förväntade resultat</u>:

På sidan *[!UICONTROL Product Listing]* visar den konfigurerbara produkten det normala priset för den underordnade produkten.

<u>Faktiska resultat</u>:

På sidan *[!UICONTROL Product Listing]* visar den konfigurerbara produkten inte det normala priset för den underordnade produkten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
