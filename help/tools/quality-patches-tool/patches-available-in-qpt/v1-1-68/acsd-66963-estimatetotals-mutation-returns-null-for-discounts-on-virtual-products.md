---
title: 'ACSD-66963: mutationen "estimsums" returnerar null för rabatter på virtuella produkter'
description: Använd patchen ACSD-66963 för att korrigera Adobe Commerce-problemet där "estimsummor" returnerar *null* för rabatter när en rabattkod används i en kundvagn med enbart virtuella produkter.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0eede09026df98426cd3b6b1550be274c26d7e13
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# ACSD-66963: `estimateTotals`-mutation returnerar null för rabatter på virtuella produkter

Korrigeringen ACSD-66963 åtgärdar ett problem där `estimateTotals` returnerar *null* för rabatter när en rabattkod tillämpas på en kundvagn med enbart virtuella produkter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 har installerats. Korrigerings-ID är ACSD-66963. Observera att detta problem har åtgärdats i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`estimateTotals`-mutationen returnerar *null* för rabatter när en rabattkod tillämpas på en kundvagn som bara innehåller virtuella produkter.

<u>Steg som ska återskapas</u>:

1. Skapa en kundvagn som endast innehåller virtuella produkter.
1. Använd en rabattkod:

   ```
   mutation {
     estimateTotals(
       input: {
         cart_id: "cart_id",
         address: {
           country_code: US,
           postcode: "78732",
           region: {
             region_code: "TX"
           }
         },
         shipping_method: {
           carrier_code: "{$shipping}",
           method_code: "{$shipping}"
         }
       }
     ) {
       cart {
         prices {
           discounts {
             amount {
               value
               currency
             }
             label
             coupon {
               code
             }
             applied_to
             type
           }
         }
       }
     }
   }
   ```

<u>Förväntade resultat</u>:

Rabattinformation ingår för kundvagnar som endast innehåller virtuella produkter.

    &quot;
    &lbrace;
    &quot;data&quot;: &lbrace;
    &quot;estimsummor&quot;: &lbrace;
    &quot;kundvagn&quot;: &lbrace;
    &quot;priser&quot;: &lbrace;
    &quot;rabatter&quot;: &lbrack;
    &lbrace;
    &quot;belopp&quot;: &lbrace;
    &quot;värde&quot;: 100.5,
    &quot;valuta&quot;: &quot;USD&quot;
    &rbrace;,
     
    &quot;label&quot;: &quot;A second rabatt code for testing&quot;,
    &quot;coupon&quot;: &lbrace;
    &quot;code&quot;: &quot;z3r0c00l&quot;
    &rbrace;,
    &quot;applied_to&quot;: &quot;ITEM&quot;,
    &quot;type&quot;: null
    
    &rbrack;
    &rbrace; 
    &rbrace;
    ,
    &quot;extensions&quot;: {}
    &rbrace;
    &quot;

<u>Faktiska resultat</u>:

Rabattinformationen returneras som *null* för kundvagnar med endast virtuella produkter.

    &quot;
    &lbrace;
    &quot;data&quot;: 
    &quot;estimsummor&quot;: 
    &quot;kundvagn&quot;: 
    &quot;priser&quot;: 
    &quot;rabatter&quot;: null
    &rbrace;
    &rbrace;
    &rbrace;
    ,
    &quot;tillägg&quot;: {}
    &rbrace;
    &quot;
 15&rbrace;

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
