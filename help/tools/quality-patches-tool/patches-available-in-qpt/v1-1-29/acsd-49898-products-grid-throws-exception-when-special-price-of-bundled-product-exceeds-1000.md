---
title: 'ACSD-49898: Produktstödrastret genererar ett undantag'
description: Använd patchen ACSD-49898 för att åtgärda problemet med Adobe Commerce där produktrutnätet genererar ett undantag när en paketerad produkt har ett specialpris som överstiger 1 000.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: adc8f12e-73e4-4ed5-8081-a9907ec13342
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-49898: Produktstödrastret genererar ett undantag

Korrigeringsfilen ACSD-49898 åtgärdar ett problem där stödrastret för produkter genererar ett undantag när en paketerad produkt har ett specialpris som överstiger 1 000. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 är installerad. Korrigerings-ID är ACSD-49898. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktstödrastret genererar ett undantag när en paketerad produkt har ett specialpris som överstiger 1 000. Problemet gäller användning av kommatecken i stället för punkter för decimaltal i vissa språkområden.

<u>Steg som ska återskapas</u>:

1. Skapa en paketerad produkt.
1. Ställ in specialpriset på 9999; spara och stäng.
1. Navigera till **[!UICONTROL Catalog]** > **[!UICONTROL Products]**

>[!NOTE]
>
>Sök efter SKU för paketerad produkt om den inte syns.

<u>Förväntade resultat</u>:

* Användaren kan filtrera/se den paketerade produkten till specialpriset.
* Specialpriset anges som en procentandel för paketerade produkter och som pris för andra produkttyper.

<u>Faktiska resultat</u>:

Följande fel inträffar: *Ett icke-numeriskt värde påträffades*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
