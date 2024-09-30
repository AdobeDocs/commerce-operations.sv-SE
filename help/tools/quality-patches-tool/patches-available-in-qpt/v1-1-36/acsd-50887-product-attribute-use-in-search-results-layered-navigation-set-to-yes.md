---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* inställt på Ja utan alternativet *[!UICONTROL Use in Search]*'
description: Använd patchen ACSD-50887 för att åtgärda Adobe Commerce-problemet där produktattributegenskapen *[!UICONTROL Use in Search Results Layered Navigation]* kan anges till *Ja* utan att alternativet *[!UICONTROL Use in Search]* också anges till *Ja*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* har angetts till *Yes* utan alternativet *[!UICONTROL Use in Search]*

Korrigeringen ACSD-50887 åtgärdar ett problem där produktattributegenskapen *[!UICONTROL Use in Search Results Layered Navigation]* kan ställas in på *Yes* utan att alternativet *[!UICONTROL Use in Search]* också ställs in på *Yes*. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.36 har installerats. Korrigerings-ID är ACSD-50887. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktattributegenskapen *[!UICONTROL Use in Search Results Layered Navigation]* kan anges till *Yes* utan att alternativet *[!UICONTROL Use in Search]* också anges till *Yes*.

De här inställningarna har utformats för att användas tillsammans. När korrigeringen används och alternativet *[!UICONTROL Use in Search]* är inställt på *Nej*, är alternativet *[!UICONTROL Use in Search Results Layered Navigation]* dolt så att det fungerar som om det även vore inställt på *Nej*.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** i Admin och skapa ett attribut med flervalstypen och ange följande:

   * *[!UICONTROL Use in Search]= Nej*
   * *[!UICONTROL Use in Layered Navigation]= (Valfritt alternativ)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Ja*
   * *Namn = Test_attribute*
   * *Alternativ*:
      * *Sticker*
      * *Väljare*

1. Lägg till det nya attributet i standardattributuppsättningen.
1. Skapa två produkter:

   1. Första produkten:
      * Namn = Sticker
      * Ange pris, ANTAL, vikt till 1
      * Test_attribute = välj alternativet *Sticker*

   1. Andra produkten:
      * Namn = Väljare
      * Ange pris, ANTAL, vikt till 1
      * Test_attribute = välj båda alternativen

1. Kör omindexering för `catalogsearch_fulltext`:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Sök efter ordet *sticker* på butiken.

<u>Förväntade resultat</u>:

Endast produkten *Sticker* returneras, eftersom [!DNL Elasticsearch] inte indexerar Test_attribute när *[!UICONTROL Use in Search]* har angetts till *No*.

<u>Faktiska resultat</u>:

Båda produkterna returneras.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
