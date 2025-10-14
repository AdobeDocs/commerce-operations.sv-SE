---
title: 'ACSD-65913: [!DNL OpenSearch] returnerar ett invalid_argument_exception för kategorier med produkter med samma pris'
description: Använd korrigeringsfilen ACSD-65913 för att åtgärda Adobe Commerce-problemet där  [!DNL Opensearch]  genererar ett illegal_argument_exception ("[from] parameter cannot be negative") för de kategorier som innehåller alla produkter med samma pris.
feature: Search
role: Admin, Developer
type: Troubleshooting
exl-id: 984db32e-1a0d-4e0a-a83b-7fe909226ed3
source-git-commit: e24b62305ef97c5fff13582b4bb68f622dffb6d3
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-65913: [!DNL OpenSearch] returnerar `illegal_argument_exception` för kategorier med produkter med samma pris

Korrigeringen ACSD-65913 åtgärdar ett problem där [!DNL OpenSearch] kastade en `illegal_argument_exception` för kategorier med produkter med samma pris. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 har installerats. Korrigerings-ID är ACSD-65913. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!DNL OpenSearch] genererar en `illegal_argument_exception` (*[från]-parameter kan inte vara negativ*) vid inläsning av kategorier där alla produkter delade samma pris.

<u>Steg som ska återskapas</u>:

1. Installera [!DNL OpenSearch] version 2.19.1 och ange den som standardsökmotor.
1. Konfigurera produktattributet **[!UICONTROL Price]** så att det visas i lagernavigering:
   1. **[!UICONTROL Visible in Advanced Search]**: *Ja*
   1. **[!UICONTROL Comparable on Storefront]**: *Ja*
   1. **[!UICONTROL Use in Layered Navigation]**: *Filterbar (med resultat)*
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Layered Navigation]**. Ange **[!UICONTROL Price Navigation Step Calculation]** som *Automatisk (utjämna produktantal)*.
1. Skapa en kategori med sex produkter som alla har samma pris:
   1. SKU: product_super_0-1-1-1, Price: $150
   1. SKU: product_super_0-1-1, Price: $48
   1. SKU: product_super_0-1, Price: $48
   1. SKU: product_super_0, pris: $48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1-1-1-1, Price: $48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1, Price: $48
1. Kör följande kommando:
   `bin/magento indexer:reindex`
1. Öppna kategorisidan. Du kommer att se ett fel:
   Parametern *[from] kan inte vara negativ, hittades [-1]*

<u>Förväntade resultat</u>:

[!DNL OpenSearch] ska inte generera ett `illegal_argument_exception` när alla produkter i en kategori har samma pris.

<u>Faktiska resultat</u>:

* [!DNL OpenSearch] skickar ett `illegal_argument_exception` med meddelandet:
  Parametern *[from] kan inte vara negativ, hittades [-1]*

* Filen `var/log/exception.log` innehåller:

  ```
  [2025-05-14T22:39:33.595272+00:00] report.CRITICAL: [!DNL OpenSearch]\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"}],"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"},"status":400}
  ```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
