---
title: 'ACSD-64753: Det förvalda arkivet i Pickup in Store uppdateras inte när leveransadressen ändras'
description: Använd patchen ACSD-64753 för att åtgärda Adobe Commerce-problemet där den förvalda butiken inte uppdaterades när en ny leveransadress angavs utanför den valda butikens serviceradie.
feature: Inventory
role: Admin, Developer
exl-id: 4efc99d6-88a3-43f9-88d4-dedb9d8a269e
type: Troubleshooting
source-git-commit: 036c1b81d9ec8f55f002446a8ea6078c6f8014d9
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-64753: Det förvalda arkivet i Pickup in Store uppdateras inte när leveransadressen ändras

Korrigeringen ACSD-64753 åtgärdar ett problem där den valda butiken inte uppdaterades när en ny leveransadress angavs utanför den valda butikens serviceradie. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 har installerats. Korrigerings-ID är ACSD-64753. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den valda butiken uppdaterades inte när en ny leveransadress angavs utanför den valda butikens serviceradie.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL In-Store Delivery]** genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Ange en giltig [!DNL Google] API-nyckel för [!DNL Google Distance Provider]. Om du vill göra det går du till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**.
1. Lägg till en ny källa (**[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**) och ange följande värden:
   * **[!UICONTROL Latitude]**: *-41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *Ja*
   * **[!UICONTROL Country United]**: *Lägen*
   * **[!UICONTROL State]**: *Illinois*
   * **[!UICONTROL City]**: *Carol Stream*
   * **[!UICONTROL Postcode]**: *60188*
1. Lägg till en ny Stock (**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** > **[!UICONTROL Add New Stock]**), tilldela den nya källan och huvudwebbplatsen till den.
1. Redigera valfri produkt, tilldela produkten till nya Source, In Stock och kvantitet > *0*.
1. Vänta tills indexeringen är klar.
1. I butiken skapar du en ny kund och lägger sedan till en adress i Kalifornien som standardfaktura och leverans.
1. Lägg till en annan icke-standardadress till den här kunden.
1. Lägg produkten i kundvagnen och fortsätt till kassan.
1. Välj fraktadressen för Kalifornien och välj **[!UICONTROL Pick in Store]** leveranssätt. Klicka på **[!UICONTROL Next]**.

<u>Förväntade resultat</u>:

Eftersom Kaliforniens adress ligger utanför den maximala sökradien (200 km) bör inte Illinois Source vara tillgänglig för kunden.

<u>Faktiska resultat</u>:

Illinois-källan kan plockas och kunden kan gå vidare till kassan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
