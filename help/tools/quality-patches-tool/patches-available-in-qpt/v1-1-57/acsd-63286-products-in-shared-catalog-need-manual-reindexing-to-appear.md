---
title: 'ACSD-63286: Produkter som tilldelats en delad katalog måste kunna omindexeras manuellt för att visas'
description: Använd korrigeringsfilen ACSD-63286 för att åtgärda Adobe Commerce-problemet där produkter som tilldelats en delad katalog via API inte visas i butiken förrän en manuell omindexering har utförts.
feature: Products, REST
role: Admin, Developer
exl-id: 0435c06e-337e-4320-acc6-fa79a3b34008
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-63286: Produkter som tilldelats en delad katalog måste kunna omindexeras manuellt för att visas

Korrigeringen ACSD-63286 åtgärdar ett problem där produkter som tilldelats en delad katalog via API inte visas i butiken förrän en manuell omindexering har utförts. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 är installerad. Korrigerings-ID är ACSD-63286. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När produkter tilldelas till en delad katalog via API, visas de inte längst fram efter att den partiella indexeraren och konsumentkron har körts. De visas dock efter en manuell omindexering.

<u>Steg som ska återskapas</u>:

1. Konfigurera [!DNL RabbitMQ] som kötjänst.
1. Skapa en delad katalog och tilldela den till ett företag.
1. Skapa en enkel produkt och tilldela den till en kategori.
1. Kör partiell omindexering.

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Använd följande API-begäran för att tilldela den skapade produkten till den delade katalogen `pub/rest/all/V1/sharedCatalog/<id>/assignProducts`:

   ```
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Kör följande kron för att rensa köerna och köra den partiella omindexeringen.

   ```
   bin/magento cron:run --group=consumers
   ```

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Logga in som företagsanvändare på frontend.
1. Kontrollera kategorisidan för frontend. De nyligen tilldelade produkterna visas inte.
1. Gör en manuell omindexering:

   ```
   bin/magento index:reindex
   ```

<u>Förväntade resultat</u>:

Produkten visas på framsidan utan att indexeras om manuellt.

<u>Faktiska resultat</u>:

Produkten visas bara på framsidan efter manuell omindexering.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
