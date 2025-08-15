---
title: 'ACSD-64118: Begäran om samtidig produktsparande för samma produkt orsakar inkonsekventa data och dubblettposter'
description: Använd patchen ACSD-64118 för att åtgärda Adobe Commerce-problemet där samtidig begäran om att spara och uppdatera samma produkt resulterar i inkonsekventa data eller duplicerade produkter.
feature: REST
role: Admin, Developer
type: Troubleshooting
exl-id: e014645e-72b2-4b3d-8b44-3daca502c950
source-git-commit: 5c84dc5c27f6e57b4116bc1a3d4fb001b55b63f1
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-64118: Begäran om samtidig produktsparande för samma produkt orsakar inkonsekventa data och dubblettposter

Korrigeringen ACSD-64118 åtgärdar ett problem där samtidig begäran om att spara och uppdatera samma produkt resulterar i inkonsekventa data eller duplicerade produkter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 har installerats. Korrigerings-ID är ACSD-64118. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p7

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p10

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Samtidiga begäranden om att spara och uppdatera samma produkt resulterar i inkonsekventa data eller dubblerade produkter.

<u>Steg som ska återskapas</u>:

1. Konfigurera flera processer för konsumenter i `env.php`:

   ```
   'multiple_processes' =>
       array (
           'async.operations.all' => 4,
       ),
   ```

1. Lägg till ytterligare en butik och en ny butik på huvudwebbplatsen.
1. Skicka en satsvis API-begäran till standardslutpunkten för butiksgranskning `/rest/default/async/bulk/V1/products` med följande nyttolast för att skapa en produkt:

   ```
   [
     {
       "product": {
         "sku": "Test_Prod",
         "name": "Test Product",
         "attribute_set_id": 4
       }
     }
   ]
   ```

1. Använd samma nyttolast för att skicka en satsnings-API-begäran till den nya slutpunkten för butiksgranskning `/rest/store/async/bulk/V1/products` för att uppdatera produkten.
1. Töm cacheminnet.
1. Kör cron-jobb.
1. Kontrollera tabellen `catalog_product_entity` för att se om det finns poster i produkten från föregående steg.

<u>Förväntade resultat</u>:

* Det ska finnas en enda post för produktens SKU i tabellen `catalog_product_entity`.
* Den första REST API-begäran ska skapa en databaspost och alla efterföljande begäranden ska uppdatera den databasposten.

<u>Faktiska resultat</u>:

Det finns flera poster för samma SKU i tabellen `catalog_product_entity`.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
