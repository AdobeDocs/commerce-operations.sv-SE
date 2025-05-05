---
title: 'ACSD-63329: Datum- och tidsattribut anges inte när produkter skapas med REST API'
description: Använd patchen ACSD-63329 för att åtgärda Adobe Commerce-problemet där standardvärden inte har angetts för datum- och tidsfälten när du skapar produkter med REST API.
feature: REST
Role: Admin, Developers
source-git-commit: a7d719399425016da26c1065725a377bb82795f4
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# ACSD-63329: Standardvärden för datum- och tidsfält anges inte när produkter skapas med REST API

Korrigeringen ACSD-63329 åtgärdar ett problem där standardvärden inte har angetts för datum- och tidsfälten när en ny produkt skapas med REST API: `/rest/default/V1/products`. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 har installerats. Korrigerings-ID är ACSD-63329. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Standardvärden har inte angetts för datum- och tidsfälten när produkter skapas med REST API: `/rest/default/V1/products`

<u>Steg som ska återskapas</u>:

1. Skapa ett **[!UICONTROL Product]**-attribut, ställ in standardvärdet på `12/31/2020` och ställ in **[!UICONTROL Catalog Input Type for Store Owner]** på ***[!UICONTROL Date]*** eller ***[!UICONTROL Date and Time]***.
1. Skapa ett annat texttypsattribut och ange standardvärdet till ***test value***.
1. Skapa en ny produkt med en REST API-POST-förfrågan till `/rest/all/V1/products/`.

   ```
       {
           "product": {
               "sku": "testsku2",
               "name": "Test Api Product 2",
               "attribute_set_id": 4,
               "price": 100,
               "status": 1,
               "visibility": 4,
               "type_id": "simple",
               "weight": 20,
               "extension_attributes": {
                   "website_ids": [
                       1
                   ]
               }
           }
       }
   ```

1. Kontrollera de sparade värdena för de attribut som nämns ovan.

<u>Förväntade resultat</u>:

Standardvärdet bör sparas i **[!UICONTROL Date/Datetime]**-typattribut när du skapar en produkt med API:t.

<u>Faktiska resultat</u>:

Standardvärdet sparas för attributet **[!UICONTROL Text]**, men inte för attributet **[!UICONTROL Date type]**. Värdet för attributet **[!UICONTROL Date]** är tomt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
