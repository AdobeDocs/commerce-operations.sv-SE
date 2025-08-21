---
title: 'ACP2E-3731: Produktexporter med synligheten [!UICONTROL Catalog, Search] inkluderar poster från andra butiksvyer'
description: Använd korrigeringen ACP2E-3731 för att korrigera Adobe Commerce där produktexporter med synlighetsfiltret inställt på [!UICONTROL Catalog, Search] innehåller felaktiga rader i flerbutiksinställningar på grund av lageromfattande attributvariationer.
feature: Data Import/Export
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7a2e98b836fcc1759910777d1e9fe50e03dabb07
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACP2E-3731: Produktexporter med synligheten [!UICONTROL Catalog, Search] inkluderar poster från andra butiksvyer

Korrigeringen ACP2E-3731 åtgärdar ett problem där produktexporter med synligheten *[!UICONTROL Catalog, Search]* felaktigt inkluderar poster från andra butiksvyer i miljöer med flera butiker. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACP2E-3731. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p9

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktexporter innehåller felaktiga rader när synlighetsfiltret är inställt på *[!UICONTROL Catalog, Search]* i flerbutiksinställningar på grund av lageromfattande attributvariationer.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** på panelen Admin för att skapa ytterligare en webbplats-, butiks- och butiksvy.
1. Gå till **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* **[!UICONTROL Attribute Set]**. Klicka på **[!UICONTROL Add Attribute Set]** om du vill skapa ett attribut. Ange **[!UICONTROL Based On]** som *Standard*.
1. Skapa en produkt och tilldela den till både huvudwebbplatsen och den sekundära webbplatsen.
1. Ange ett textvärde för det nya attributet med **[!UICONTROL Scope]** inställt på *Alla butiksvyer*.
1. Ändra omfånget till vyn för den sekundära lagringsplatsen och uppdatera attributet med ett annat värde.
1. Ändra omfånget till standardbutiksvyn och den sekundära butiksvyn och ange sedan produktsynligheten till *Inte synlig enskilt*.
1. Gå till **[!UICONTROL System]** > **[!UICONTROL Export]** och välj *Produkter* i listrutan.
1. Ange ett filter där **[!UICONTROL Visibility]** = *[!UICONTROL Catalog, Search]* och klicka på **[!UICONTROL Continue]**.
1. Kör följande kommando för att bearbeta exporten:

   ```
   php bin/magento queue:consumers:start exportProcessor
   ```

1. Kontrollera den exporterade filen.

<u>Förväntade resultat</u>:

Endast filtrerade poster exporteras.

<u>Faktiska resultat</u>:

Den exporterade filen innehåller en rad för den sekundära lagringsvyn, som inte matchar filtervillkoren som angavs vid exporten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
