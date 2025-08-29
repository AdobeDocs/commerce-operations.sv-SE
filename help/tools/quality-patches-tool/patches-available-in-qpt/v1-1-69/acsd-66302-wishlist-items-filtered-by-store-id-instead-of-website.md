---
title: 'ACSD-66302: Önsklisteobjekt filtrerade efter butiks-ID i stället för efter webbplats'
description: Använd patchen ACSD-66302 för att åtgärda Adobe Commerce-problemet där önskelisteobjekt filtreras efter butiks-ID i stället för webbplatser i  [!DNL GraphQL] begäranden.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: c1a9eadc-0321-4f5c-ba82-533286a1f24f
source-git-commit: bec27df19ce5d34be063dce3de74ffe253c3e8f4
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-66302: Önsklisteobjekt filtrerade efter butiks-ID i stället för efter webbplats

Korrigeringen ACSD-66302 åtgärdar ett problem där önskelisteobjekt filtreras efter butiks-ID i stället för webbplatser i [!DNL GraphQL]-begäranden. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACSD-66302. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Önsklisteobjekt filtreras felaktigt efter butiks-ID i stället för efter webbplats.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Skapa ytterligare en butiksgranskning.
1. Gå till **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Wish List]** > **[!UICONTROL General Options]** i Admin och ange **[!UICONTROL Enable Multiple Wish Lists]** till `Yes`.
1. Gå till **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]** och ställ in **[!UICONTROL Add Store Code to Urls]** på `Yes`.
1. Skapa ett kundkonto.
1. Använd en [!DNL GraphQL]-begäran för att hämta kundens autentiseringstoken.
1. Logga in som kund.
1. Markera **[!UICONTROL Default Store View]** och lägg till produkten i önskelistan.
1. Växla butiksvy till *test*.
1. Bekräfta att produkten fortfarande visas i önskelistan (korrekt beteende).
1. Kör följande [!DNL GraphQL]-fråga:

   ```
   {
     customer {
       wishlists {
         id
         name
         items_count
         items_v2 {
           items {
             id
             product {
               uid
               name
               sku
             }
           }
         }
       }
     }
   }
   ```

1. Utför frågan på standardbutiken - produkten visas som förväntat.
1. Utför samma fråga i testbutiken - produkten visas inte.

<u>Förväntade resultat</u>:

Produkten ska vara synlig i alla butiksvyer på samma webbplats via [!DNL GraphQL] frågor.

<u>Faktiska resultat</u>:

Produkten försvinner från önskelistan när butiksvyer växlas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
