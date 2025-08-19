---
title: 'ACP2E-3964: Konfigurerbara underordnade produkter med video som inte listas via REST API'
description: Använd korrigeringen ACP2E-3964 för att åtgärda Adobe Commerce-problemet där underordnade produkter i konfigurerbara produkter med en video i [!UICONTROL Media Gallery] inte listas via REST API.
feature: Products, Media, REST, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f48ced28035c65db561f4700113652574d302ec9
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# ACP2E-3964: Konfigurerbara underordnade produkter med video som inte listas via REST API

Korrigeringen ACP2E-3964 åtgärdar ett problem där underordnade produkter för konfigurerbara produkter med en video i **[!UICONTROL Media Gallery]** inte listas via REST API. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACP2E-3964. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Underordnade produkter för konfigurerbara produkter med en video i **[!UICONTROL Media Gallery]** kan inte listas via REST API, vilket resulterar i ett felsvar.

<u>Steg som ska återskapas</u>:

1. Skapa en ny konfigurerbar produkt och lägg till en underordnad produkt.
1. Redigera den underordnade produkten och lägg till en video under **[!UICONTROL Images and Videos]** (till exempel [https://vimeo.com/1084537](https://vimeo.com/1084537)).
1. Spara den underordnade produkten.
1. Skicka en GET-begäran till REST API-slutpunkten: `rest/v1/configurable-products/%sku%/children` med hjälp av en administratörsbärartoken.

<u>Förväntade resultat</u>:

REST API ska returnera underordnade produktdata utan fel, inklusive videoinformationen i **[!UICONTROL Media Gallery]**.

<u>Faktiska resultat</u>:

REST API returnerar ett fel:

```
Error: Call to a member function getVideoProvider() on null in vendor/magento/module-product-video/Model/Product/Attribute/Media/ExternalVideoEntryConverter.php:87
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
