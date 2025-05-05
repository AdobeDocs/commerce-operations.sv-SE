---
title: 'ACSD-48210: Store view specific scope attribute overrides global values'
description: Använd patchen ACSD-48210 för att åtgärda Adobe Commerce-problemet med att uppdatera ett *[!UICONTROL Website Scope]*-attribut i en viss butiksvy åsidosätter attributvärdena i det globala omfånget.
feature: Products, Attributes
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-48210: Store view specific scope attributes override global values

Korrigeringen ACSD-48210 åtgärdar ett problem där attributvärdena i det globala omfånget åsidosätts när ett *[!UICONTROL Website Scope]*-attribut uppdateras i en viss butiksvy. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 är installerad. Korrigerings-ID är ACSD-48210. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du uppdaterar ett *[!UICONTROL Website Scope]*-attribut i en viss lagringsvy åsidosätts attributvärdena i det globala omfånget.

Importering av produktpriser med flera rader som delar samma `SKU` och `store_view_code` orsakade felaktiga uppdateringar av priserna i *[!UICONTROL All Store View]*- och *[!UICONTROL Default Store]*-omfången. När du ändrar webbplatsens omfångsattribut i en viss butiksvy åsidosätts inte längre attributets värde i det globala omfånget.
<u>Steg som ska återskapas</u>:

1. Konfigurera *[!UICONTROL Catalog Price Scope]* till *[!UICONTROL Website]*.
1. Skapa en enkel produkt med namnet *SP01* och ange priset till *$84.50*.
1. Importera produkten med hjälp av följande CSV-fil:

   ```
   sku,store_view_code,price
   SP01,default,99.99
   SP01,default,86.59
   ```

1. Kontrollera produktpriset i områdena *[!UICONTROL All Store View]* och *[!UICONTROL Default Store]*.

<u>Förväntade resultat</u>:

* Det första icke-tomma värdet används för omfattningen *[!UICONTROL Default Store]*.
* Omfånget *[!UICONTROL All Store View]* ändras inte.

<u>Faktiska resultat</u>:

* Omfångspriset *[!UICONTROL All Store View]* ändras till *$86.59*.
* Omfångspriset *[!UICONTROL Default Store]* ändras till *$86.59*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
