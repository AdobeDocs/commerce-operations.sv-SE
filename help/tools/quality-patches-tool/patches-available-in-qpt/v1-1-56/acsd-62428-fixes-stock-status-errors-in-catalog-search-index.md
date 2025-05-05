---
title: 'ACSD-62428: Stock-statusfel i katalogsökningsindex'
description: Använd patchen ACSD-62428 för att åtgärda problemet där värdet "is_out_of_stock" i katalogsökningsindexet inte har angetts korrekt när SKU inte är ett sökbart attribut.
feature: Inventory, Catalog Management
role: Admin, Developer
source-git-commit: 633aa46886d65f45e8b503e3892e47bb24e40fc0
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62428: Stock-statusfel i katalogsökningsindex

Korrigeringen ACSD-62428 åtgärdar ett problem där `is_out_of_stock`-värden i katalogsökindexet har ett felaktigt värde när SKU-attributet inte har angetts som sökbart. Den här korrigeringen är tillgänglig med [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. Korrigerings-ID är ACSD-62428. Observera att problemet var planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.6-p5

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Värdet `is_out_of_stock` i katalogsökindexet har ett felaktigt värde när SKU inte har konfigurerats som ett sökbart attribut, vilket leder till felaktig arkivrepresentation.

<u>Steg som ska återskapas</u>:

1. Skapa en anpassad [!UICONTROL Source] och anpassad [!UICONTROL Stock].
1. Skapa tre enkla produkter och tilldela deras lager till den anpassade [!UICONTROL Source]. Tilldela dessa produkter till en kategori.
1. Ange *[!UICONTROL Inventory (MSI) Indexer]* till *[!UICONTROL Update on Save]* för enklare replikering.
1. Ange *[!UICONTROL Source Item Status]* till *[!UICONTROL In Stock]* och tilldela *[!UICONTROL Quantity]*.
1. Spara produkten.
1. Navigera till **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** och öppna attributet **[!UICONTROL SKU]**.
1. Ange *[!UICONTROL Use In]* till *[!UICONTROL No]*.
1. Ändra produktkvantiteten (se till att den inte är inställd på 0).
1. Spara produkten.

<u>Förväntade resultat</u>:

Värdet `is_out_of_stock` återspeglar produktens Stock-status korrekt, även när SKU:n inte är ett sökbart attribut.

<u>Faktiska resultat</u>:

Värdet `is_out_of_stock` är felaktigt inställt på 1 och SKU-attributet saknas i indexerade data.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
