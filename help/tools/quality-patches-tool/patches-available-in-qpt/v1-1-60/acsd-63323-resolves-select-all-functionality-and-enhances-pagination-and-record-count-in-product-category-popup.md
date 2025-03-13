---
title: 'ACSD-63323: Korrigerar funktionen [!UICONTROL Select All] och förbättrar sidnumrering och antal poster i popup-fönstret för produktkategorier'
description: Använd korrigeringsfilen ACSD-63323 för att åtgärda Adobe Commerce-problemet där alternativet [!UICONTROL Select All] inte fungerar när du lägger till produkter i en kategori. Dessutom ser det till att sidnumrering och etiketten för antal poster fungerar korrekt när du lägger till produkter i en kategori via popup-rutnätet.
feature: Products
role: Admin, Developer
source-git-commit: f3f0cc93adf83b485ca50811adcc561638e3c5c2
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-63323: Korrigerar funktionen [!UICONTROL Select All] och förbättrar sidnumrering och antal poster i popup-fönstret för produktkategorier

Korrigeringen ACSD-63323 åtgärdar ett problem där alternativet **[!UICONTROL Select All]** inte fungerar när produkter läggs till i en kategori. Dessutom ser det till att sidnumrering och etiketten för antal poster fungerar korrekt när du lägger till produkter i en kategori via popup-rutnätet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) har installerats. Korrigerings-ID är ACSD-63323. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Åtgärdar problemet där alternativet **[!UICONTROL Select All]** inte fungerar i Admin > **[!UICONTROL Categories]** > välj en kategori > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**. Det underlättar också sidnumrering och att etiketten för antal poster fungerar korrekt när du lägger till produkter i en kategori via popup-rutnätet.


<u>Steg som ska återskapas</u>:

1. Generera *1200*-produkter med kommandot:

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Öppna **[!UICONTROL Catalog]** > **[!UICONTROL Products]** och se antalet produkter: *1200* poster hittades.
1. Öppna en standardkategori > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**.
1. Klicka på **[!UICONTROL Assign]** > **[!UICONTROL Select All]**.
1. Ändra antalet produkter på sidan till värdet = *5*.


**Förväntade resultat**:

*Meddelandet ska vara: 1 200 poster hittades (1 200 valda)*

**Faktiska resultat**:

* Sidindelning fungerar inte.
* Fel meddelande visas: *5* poster hittades (*20* valt)

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.


