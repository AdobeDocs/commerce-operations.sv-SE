---
title: 'ACSD-62758: Löste problem med videoåtergivning på konfigurerbara produktsidor'
description: Använd patchen ACSD-62758 för att åtgärda problemet med Adobe Commerce där produktvideor på konfigurerbara produktinformationssidor inte återges korrekt när URL:er innehåller förinställda alternativ för färgrutor.
feature: Catalog Management
role: Admin, Developer
source-git-commit: 313709361ee86e39b89c416f71a92b078318f4fb
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# ACSD-62758: Löste problem med videoåtergivning på konfigurerbara produktsidor

Korrigeringen för ACSD-62758 åtgärdar ett problem där produktvideor på konfigurationsbara produktinformationssidor inte återges korrekt när URL:er innehåller förvalda alternativ för färgrutor. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 är installerad. Korrigerings-ID är ACSD-62758. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktvideor återges inte korrekt på konfigurerbara produktinformationssidor när URL:en innehåller förvalda färgrutealternativ, vilket resulterar i att en statisk bild visas i stället för videon.

<u>Steg som ska återskapas</u>:

1. Navigera till [!UICONTROL Stores] > [!UICONTROL Attributes] > [!UICONTROL Product].
1. Markera attributet **[!UICONTROL Color]** och redigera det.
1. Uppdatera följande inställningar:
   1. Ange [!UICONTROL Catalog Input Type for Store Owner] till [!UICONTROL Visual Swatch].
   1. Ange **[!UICONTROL Update Product Preview Image]** till **[!UICONTROL Yes]**.
1. Skapa några alternativ för det här attributet.
1. Skapa en ny kategori och lägg till en ny konfigurerbar produkt i den med attributet **[!UICONTROL Color]**.
1. Lägg till en slumpmässig bild till den överordnade produkten.
1. Redigera nyligen skapade konfigurerbara underordnade produkter och lägg till en video i deras mediegalleri:
   1. Klicka på **[!UICONTROL Add Video]** och använd testvideons URL: https://vimeo.com/12860646.
1. Spara produkten, rensa cacheminnet och indexera om butiken.
1. Öppna den nya produkten i butiken, välj något av färgrutealternativen och bekräfta att videon läses in korrekt när spelarknappen visas.
1. Videon ska läsas in som förväntat och spelarknappen ska visas.
1. Högerklicka på något av färgrutealternativen, välj **[!UICONTROL Inspect]** och leta reda på attribut-id:t och alternativ-ID:t. Kopiera produkt-URL:en och lägg till följande i slutet av den: `www.product-url.com/producit-test#attribute_id=option_id`. Då är alternativet för färgruta förvalt. Öppna den uppdaterade URL:en i ett nytt fönster.

<u>Förväntade resultat</u>:

Videon ska läsas in korrekt, ungefär som när ett färgrutealternativ väljs manuellt.

<u>Faktiska resultat</u>:

En statisk bild visas i stället för videon. Konsolfel loggas, vilket indikerar ett fel i videoinitieringen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
