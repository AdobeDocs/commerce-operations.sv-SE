---
title: 'ACSD-67264: Paket- och nedladdningsbara produktsidlayouter är inte desamma på alla enheter'
description: Använd patchen ACSD-67264 för att åtgärda layoutproblem i Adobe Commerce-paketet och hämtningsbara sidor på grund av en omordning av produktinformationsmediablocket.
feature: Page Content, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9b6794366ba552d86cdfc6a3d6f699c307fcd8f6
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# ACSD-67264: Paket- och nedladdningsbara produktsidlayouter är inte desamma på alla enheter

Korrigeringen ACSD-67264 åtgärdar ett problem där layout för paket och hämtningsbara produktsidor är olika på olika enheter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACSD-67264. Observera att detta problem har åtgärdats i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Paketet med nedladdningsbara produktsidor fick layoutproblem på grund av en omorganisering av produktinformationsmediablocket.

<u>Steg som ska återskapas</u>:

1. Installera exempeldata.
1. Öppna produktsidan för paketet och kontrollera layouten på skrivbordet.
1. Lägg till produktsidan i önskelistan, navigera till önskelistan, klicka på redigeringsikonen och kontrollera layouten.
1. Upprepa steg 2 och 3 för en nedladdningsbar produkt.

<u>Förväntade resultat</u>:

Paketet PDP renderas utan problem.

<u>Faktiska resultat</u>:

Paketet PDP återges med slumpmässiga blanksteg.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool]
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i guiden för Commerce om molninfrastruktur

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken
