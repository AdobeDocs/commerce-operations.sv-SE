---
title: 'ACSD-66082: Det går inte att uppdatera en produkts färgrutebild via produktimport'
description: Använd patchen ACSD-66082 för att åtgärda Adobe Commerce-problemet där överföringen av en CSV-fil med fältet swatch_image inställt på EMPTY_VALUE för att ta bort färgrutebilder gör att importen misslyckas med ett fel.
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: bdd15514c6b6ece6c7f33a41267357b4a24261f1
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-66082: Det går inte att uppdatera en produkts färgrutebild via produktimport

Korrigeringen ACSD-66082 åtgärdar ett problem där det inte gick att uppdatera färgrutebilden för en produkt genom produktimport. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 har installerats. Korrigerings-ID är ACSD-66082. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du överför en CSV-fil med fältet `swatch_image` inställt på `EMPTY_VALUE` för att ta bort färgrutebilder misslyckas importprocessen med ett fel.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]**. Klicka på nedpilen bredvid knappen **[!UICONTROL Add Product]** och välj **[!UICONTROL Simple Product]**. Ange **[!UICONTROL SKU]** som *ABC*.
1. Överför en PNG-bild med namnet *testing.png* till `var/import/images/`.
1. Skapa en CSV-fil med följande innehåll:

   ```
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. Gå till **[!UICONTROL System]** > **[!UICONTROL Import]** om du vill importera filen genom att justera följande inställningar:
   * **[!UICONTROL Entity type]**: *Produkter*
   * **[!UICONTROL Import Behavior]**: *Lägg till/uppdatera*
   * Klicka på **[!UICONTROL Choose File]** för att välja den CSV-fil som skapades i föregående steg som ska importeras. Importen är klar och färgrutan läggs till.
1. Uppdatera CSV-filen med följande innehåll:

   ```
   sku,swatch_image,swatch_image_label
   ABC,__EMPTY__VALUE__,__EMPTY__VALUE__
   ```

1. Upprepa importprocessen.

<u>Förväntade resultat</u>:

Färgrutebilden har tagits bort.

<u>Faktiska resultat</u>:

Importprocessen genererar ett fel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
