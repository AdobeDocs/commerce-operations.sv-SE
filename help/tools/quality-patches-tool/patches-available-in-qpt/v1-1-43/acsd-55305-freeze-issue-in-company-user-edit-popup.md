---
title: 'ACSD-55305: Popup-frysning under redigering av företagsanvändare i [!UICONTROL My Account]'
description: Använd ACSD-55305-korrigeringen för att åtgärda Adobe Commerce-problemet där [!UICONTROL Edit Company User]-popup på [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] -sidan fryser med en inläsare på skärmen.
feature: Companies, B2B
role: Admin, Developer
exl-id: eeb2b136-022f-42d5-85e2-85537f4677d6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-55305: Popup-frysning under redigering av företagsanvändare i [!UICONTROL My Account]

ACSD-55305-korrigeringen åtgärdar ett problem där [!UICONTROL Edit Company User]-popup på [!UICONTROL My Account]> [!UICONTROL Company Structure]-sidan fryser med en inläsare på skärmen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 har installerats. Korrigerings-ID är ACSD-55305. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel inträffar vid försök att använda popup-fönstret *[!UICONTROL Edit Company User]* på sidan *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* eftersom det slutar svara när en inläsare visas på skärmen.

<u>Steg som ska återskapas</u>:

1. Skapa ett B2B-företag.
1. Skapa ett flervalsattribut för kunder.
1. Tilldela ett värde till det nya attributet för företagsadministratören.
1. Logga in som företagsadministratör.
1. Gå till [!UICONTROL account dashboard] och navigera till **[!UICONTROL Company Structure]**.
1. Markera användaren.
1. Klicka på **[!UICONTROL Edit Selected]**.

<u>Förväntade resultat</u>:

Formulärets popup-fönster visas korrekt, med möjlighet att redigera företagsinformation.

<u>Faktiska resultat</u>:

Formulärets popup-fönster visas utan möjlighet att redigera.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
