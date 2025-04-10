---
title: 'ACSD-64137: Sökning efter upphämtningsplatser med hjälp av zip-kod fungerar inte korrekt för holländsk lokalisering'
description: Använd korrigeringsfilen ACSD-64137 för att åtgärda problemet där sökning efter upphämtningsplatser med hjälp av postnummer inte fungerar som den ska för holländska lokaliseringen.
feature: Shipping/Delivery
role: Admin, Developer
source-git-commit: 4947133daaffb919aeba986c8a6b88ecb2e1b943
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# ACSD-64137: Sökning efter upphämtningsplatser med hjälp av zip-kod fungerar inte korrekt för holländsk lokalisering

Korrigeringen ACSD-64137 åtgärdar ett problem där sökning efter upphämtningsplatser efter postnummer inte fungerar som den ska för holländska lokaliseringen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 har installerats. Korrigerings-ID är ACSD-64137. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

ZIP-kodsökningen för Nederländerna visar inte några resultat på utcheckningssidan för frontend. Den fungerar dock efter ort och visar motsvarande adress utan sökning.

<u>Steg som ska återskapas</u>:

1. Installera en ren instans med lagermoduler.
1. Skapa en anpassad Stock.
1. Skapa två källor med nederländska adresser och tilldela dem till aktierna (postnummer 7311ER och 7311AE).
1. Skapa en enkel produkt och lägg till lager.
1. Aktivera **[!UICONTROL In-Store Delivery]** genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]**.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Distance Provider for Distance Based SSA]**. Ange **[!UICONTROL Provider]** som *Offlineberäkning*.
1. Kör följande kommando för att importera geonamn för NL-land.

   ```bash
   bin/magento inventory-geonames:import NL
   ```

1. Lägg produkten i kundvagnen och gå till leveranssteget.
1. Välj **[!UICONTROL Pick In Store]**. Klicka sedan på **[!UICONTROL Select Other]** för att välja andra butiker.
1. Skriv *7311* eller *7311AE* i sökformuläret **[!UICONTROL Select Store]**.


**Förväntade resultat**:

* Matchade butiker ska fyllas i.

**Faktiska resultat**:

* Inga resultat hittades.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
