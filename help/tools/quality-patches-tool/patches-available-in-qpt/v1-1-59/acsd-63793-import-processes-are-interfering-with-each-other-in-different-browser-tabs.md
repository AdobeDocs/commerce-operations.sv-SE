---
title: 'ACSD-63793: Importprocesser påverkar varandra på olika webbläsarflikar'
description: Använd patchen ACSD-63793 för att åtgärda Adobe Commerce-problemet där importprocesserna stör varandra på olika webbläsarflikar.
feature: Data Import/Export
role: Admin, Developer
exl-id: f6bed4c4-5ea2-47e7-97fa-d7717470297f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-63793: Importprocesser påverkar varandra på olika webbläsarflikar

Korrigeringen ACSD-63793 åtgärdar ett problem där importprocesserna stör varandra på olika webbläsarflikar. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 har installerats. Korrigerings-ID är ACSD-63793. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du importerar data via administratörsgränssnittet påverkas importen av data från en import, vilket innebär att de bearbetas i en annan.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**.
1. Ange **[!UICONTROL Entity Type]** till *[!UICONTROL Customers and Addresses](en fil)*.
1. Ange **[!UICONTROL Import Behavior]** till *[!UICONTROL Add/Update]*.
1. Välj en giltig fil att importera.
1. Klicka på knappen **[!UICONTROL Check Data]**.
1. Ha den här fliken öppen.
1. Öppna en ny flik och upprepa stegen med en fil som innehåller ogiltiga data (till exempel två identiska e-postmeddelanden för olika kunder).
1. Växla tillbaka till den första fliken.
1. Klicka på knappen **[!UICONTROL Import]** längst ned.

<u>Förväntade resultat</u>:

Importprocessen bör inte störa varandra.

<u>Faktiska resultat</u>:

Importen slutförs och rapportfilen är tillgänglig för hämtning. Det indikerar ett fel i den andra raden och data från en annan import bearbetas, även om den ursprungliga valideringen skickades utan fel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
