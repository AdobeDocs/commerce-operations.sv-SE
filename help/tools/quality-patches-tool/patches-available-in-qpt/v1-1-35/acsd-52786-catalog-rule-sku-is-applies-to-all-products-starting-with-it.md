---
title: 'ACSD-52786: Katalogregeln *[!UICONTROL SKU is]* gäller alla produkter som börjar med SKU:n'
description: Använd ACSD-52786-korrigeringen för att åtgärda Adobe Commerce-problemet där katalogregelvillkoret *[!UICONTROL SKU is]* gäller för alla produkter som börjar med den angivna SKU:n.
feature: Price Rules
role: Admin
exl-id: 668d5f16-18a9-4054-aa6e-1fb8fa211373
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52786: Katalogregeln *[!UICONTROL SKU is]* gäller alla produkter som börjar med SKU:n

ACSD-52786-korrigeringen åtgärdar ett problem där katalogregelvillkoret *[!UICONTROL SKU is]* gäller för alla produkter som börjar med den angivna SKU:n. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 har installerats. Korrigerings-ID är ACSD-52786. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Katalogregelvillkoret *[!UICONTROL SKU is]* gäller alla produkter som börjar med den angivna SKU:n.

<u>Steg som ska återskapas</u>:

1. Skapa två produkter, en med SKU &quot;24&quot; och en annan med SKU &quot;24 MB01&quot;.
1. Navigera till **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Använd följande villkor:
   * *[!UICONTROL If **&#x200B; ALLA &#x200B;** av dessa villkor är **&#x200B; TRUE &#x200B;**]*: *[!UICONTROL SKU is 24]*
1. Ange ett rabattbelopp i funktionsmakron.
1. Klicka på **[!UICONTROL Save and Apply]**.
1. Töm cacheminnet.
1. Gå till butiken och kontrollera priset på 24 MB01.

<u>Förväntade resultat</u>:

Katalogregeln används endast för en enskild produkt med SKU 24.

<u>Faktiska resultat</u>:

Katalogregelvillkoret *[!UICONTROL SKU is]* gäller alla produkter som börjar med den angivna SKU:n.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
