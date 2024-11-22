---
title: "ACSD-58471: Dynamiskt innehåll läses inte in på produktinformationssidan när de associerade katalogprisreglerna var schemalagda"
description: Använd patchen ACSD-58471 för att åtgärda Adobe Commerce-problemet där dynamiskt innehåll inte kan läsas in på produktinformationssidan när de tillhörande katalogprisreglerna var schemalagda.
feature: Catalog Management
role: Admin, Developer
source-git-commit: a3afb779006de95ac70dff39a737360112220af8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# ACSD-58471: Dynamiskt innehåll läses inte in på produktinformationssidan när de associerade katalogprisreglerna var schemalagda

Korrigeringen ACSD-58471 löser problemet där dynamiskt innehåll inte kan läsas in på produktinformationssidan när de associerade katalogprisreglerna var schemalagda. Systemet visar nu dynamiskt innehåll som är kopplat till regler för katalogpris korrekt på produktinformationssidan. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 är installerad. Korrigerings-ID är ACSD-58471. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.5-p4

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Steg som ska återskapas</u>:

1. Skapa ett dynamiskt block i Commerce [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Dynamic Blocks]**.
1. Skapa ett statiskt block i [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Blocks]**. Använd widgetar för att lägga till innehåll.
1. Skapa en produkt och lägg till CMS-blocket i beskrivningen.
1. Skapa en katalogregel med en schemalagd uppdatering och tilldela produkten och det skapade dynamiska blocket i **[!UICONTROL Marketing]** > Kampanjer > **[!UICONTROL Catalog Products Rules]**.
1. Kör kron och kontrollera att sidan med produktinformation visar det dynamiska innehållet efter den schemalagda starttiden.
1. Skapa en katalogregel utan en schemalagd uppdatering och tilldela produkten och det skapade dynamiska blocket i **[!UICONTROL Marketing]** > Kampanjer > **[!UICONTROL Catalog Products Rules]**.
1. Kör kron och kontrollera om den produktdetaljerade sidan visar det dynamiska innehållet efter den schemalagda tiden.


<u>Förväntade resultat</u>:

Dynamiskt innehåll läses in efter den schemalagda starttiden.

<u>Faktiska resultat</u>:

Dynamiskt innehåll läses inte in.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
