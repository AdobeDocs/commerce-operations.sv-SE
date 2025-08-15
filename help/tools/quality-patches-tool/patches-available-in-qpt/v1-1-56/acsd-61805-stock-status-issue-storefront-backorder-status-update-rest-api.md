---
title: 'ACSD-61805: Åtgärdar lagerproblem på butiken efter statusuppdatering för restorder via REST API'
description: Använd patchen ACSD-61805 för att åtgärda Adobe Commerce-problemet där produkterna ligger utanför lagret efter att ha uppdaterat backorder-statusen via REST API
feature: REST, Catalog Management, Inventory
role: Admin, Developer
exl-id: ff85e747-6394-43db-a02a-87b1e5e59f00
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61805: Åtgärdar lagerproblem på butiken efter statusuppdatering för restorder via REST API

Korrigeringen ACSD-61805 åtgärdar ett problem där produkter ligger utanför lagret efter att ha uppdaterat backorder-statusen via REST API. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 har installerats. Korrigerings-ID är ACSD-61805. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produkterna finns inte i lager när man har uppdaterat backorder-statusen via REST API.

<u>Steg som ska återskapas</u>:

1. Installera en ren instans med exempeldata.
1. Skapa en ny lagerkälla.
1. Skapa ett nytt lager och tilldela den nya källan till det.
1. Tilldela den nya källan till produkt 24 MB01.
1. Ange **[!UICONTROL Source Item Status]** till `In Stock` för båda produktkällorna.
1. Ange kvantiteten (**[!UICONTROL QTY]**) till *för båda produktkvantiteterna.*
1. Spara produkten.
1. Hämta administratörstoken från den här slutpunkts-URL: `/rest/default/V1/integration/admin/token`

   ```json
   {
     "username":"admin", 
     "password":"password" 
   }
   ```

1. Uppdatera produkten med slutpunkten: `/rest/default/V1/products`

   ```json
   {
     "product":{
       "sku": "24-MB01",
       "extension_attributes": {
           "stock_item": {
               "stock_id": "1",
               "is_in_stock": "0",
               "use_config_backorders": "false",
               "backorders": "0"
           }
       }
     }
   }
   ```

1. Kör cron-jobben två gånger (en gång för att skapa scheman och en gång för att köra schemat):

   ```bash
   bin/magento cron:run
   ```

1. Gå till frontend och kontrollera produkten.

<u>Förväntade resultat</u>:

Produkten ska vara *i Stock*.

<u>Faktiska resultat</u>:

Produkten har *slut på Stock*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
