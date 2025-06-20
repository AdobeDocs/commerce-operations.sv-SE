---
title: 'ACSD-62670: [!UICONTROL Ordered Products Report]-export till CSV och XML genererar fel'
description: Använd korrigeringsfilen ACSD-62670 för att åtgärda Adobe Commerce-problemet när export av [!UICONTROL Ordered Products Report] till CSV och XML genererar ett fel.
feature: Reporting, Admin Workspace, Data Import/Export
role: Admin, Developer
exl-id: 99d77ddd-4fb3-4eda-8771-62c0e25f49d1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# ACSD-62670: *[!UICONTROL Ordered Products Report]*-export till CSV och XML genererar fel

Korrigeringen ACSD-62670 åtgärdar ett problem där export av *[!UICONTROL Ordered Products Report]* till CSV och XML genererar ett fel. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) 1.1.56 är installerad. Korrigerings-ID är ACSD-62670. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Export av *[!UICONTROL Ordered Products Report]* till CSV och XML genererar ett fel.

<u>Steg som ska återskapas</u>:

1. Gå till panelen *Admin* och navigera till **[!UICONTROL Reports]** > **[!UICONTROL Products]** > **[!UICONTROL Ordered]**.
1. Försök exportera antingen CSV- eller Excel-filer.

<u>Förväntade resultat</u>:

Rapporterna exporteras utan fel.

<u>Faktiska resultat</u>:

Export av *[!UICONTROL Ordered Products Report]* resulterar i fel 404.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
