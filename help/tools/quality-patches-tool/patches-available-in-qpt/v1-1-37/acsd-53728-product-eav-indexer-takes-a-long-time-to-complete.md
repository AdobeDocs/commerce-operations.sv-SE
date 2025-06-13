---
title: 'ACSD-53728: Produktens EAV-indexerare tar lång tid att slutföra'
description: Använd korrigeringsfilen ACSD-53728 för att åtgärda problemet med Adobe Commerce där det tar lång tid att slutföra produktindexeraren.
feature: Products, Attributes
role: Admin, Developer
exl-id: 6cf3e401-ec28-4f80-b628-d1584f771c45
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-53728: Produktens EAV-indexerare tar lång tid att slutföra

Korrigeringen ACSD-53728 åtgärdar ett problem där det tar lång tid att slutföra produktens EAV-indexerare. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.37 har installerats. Korrigerings-ID är ACSD-53728. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktens EAV-indexerare tar lång tid att slutföra.

<u>Steg som ska återskapas</u>:

1. Skapa ett stort antal produkter (till exempel omkring 1 300 konfigurerbara produkter).
1. Kör EAV-omindexering för produkt och mät tiden:

   `run bin/magento index:reindex catalog_product_attribute`

<u>Förväntade resultat</u>:

Omindexering tar en rimlig tid.

<u>Faktiska resultat</u>:

Omindexering tar lång tid.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
