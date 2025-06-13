---
title: 'MDVA-43201: Fel vid användning av DOB-fält med nationella inställningar för PT'
description: MDVA-43201-korrigeringen löser problemet där ett fel inträffar när DOB-kundattributet används i kundregistreringsformuläret för den portugisiska språkinställningen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 är installerat. Korrigerings-ID är MDVA-43201. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: B2B, Cache
role: Admin
exl-id: be087420-1ee3-40cc-8ff7-62c5641609cc
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-43201: Fel vid användning av DOB-fält med nationella inställningar för PT

MDVA-43201-korrigeringen löser problemet där ett fel inträffar när DOB-kundattributet används i kundregistreringsformuläret för den portugisiska språkinställningen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 är installerat. Korrigerings-ID är MDVA-43201. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När DOB-kundattribut läggs till i kundregistreringsformuläret för portugisiska, ger formuläret felet *Argument 1 som skickas till iterator_to_array() att implementera gränssnitt som kan skickas, null angivet*.

<u>Förutsättningar</u>:

B2B-moduler är installerade.

<u>Steg som ska återskapas</u>:

1. Gå till Admin > **Butiker** > **Konfiguration** > **Allmänt** > **Språkalternativ**, ange Språk till **Portugisiska (Portugal)** och klicka på **Spara**.
1. Indexera om och rensa cache.
1. Gå till **Store** > **Attribut** > **Kund**.
1. Öppna DOB-kundattributet och ange **Visa på Storefront** till **Ja**.
1. Välj alla från **Formulär att använda i**.
1. Spara attributet.
1. Gå till sidan Skapa nytt konto i förgrunden.

<u>Förväntade resultat</u>:

Kundregistreringsformuläret för den portugisiska butiken ger inget fel när DOB-attributet läggs till.

<u>Faktiska resultat</u>:

Kundregistreringsformuläret för den portugisiska butiken returnerar ett fel när DOB-attributet läggs till.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
