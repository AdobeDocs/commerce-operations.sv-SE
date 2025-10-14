---
title: 'ACSD-65777: Fältet "types" för produktbildtyper saknas i GraphQL-begäran "MediaGallery"'
description: Använd patchen ACSD-65777 för att åtgärda Adobe Commerce-problemet där fältet "types" saknas för produktbildtyper i GraphQL-begäran "MediaGallery".
feature: GraphQL, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 20866963-54a3-4859-9c2d-716945e37156
source-git-commit: 5bcafd22647f9a87596c4f2d852bda76a5d6427b
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# ACSD-65777: Fältet **[!UICONTROL types]** saknas för produktbildtyper i GraphQL-begäran `MediaGallery`

Korrigeringen ACSD-65777 åtgärdar ett problem där fältet **[!UICONTROL types]** saknades för produktbildtyper i GraphQL-begäran för `MediaGallery`. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 har installerats. Patch-ID:t är ACSD-65777. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Fältet **[!UICONTROL types]** saknas för produktavbildningstyper när mediedata hämtas via GraphQL-begäran `MediaGallery`.

<u>Steg som ska återskapas</u>:

1. Skapa en produkt.
1. Överför en bild till produkten.
1. Hämta mediedata med följande GraphQL.

   ```
   query{
     products(search:"",filter:{sku:{eq:"p1"}})\{
       items{
         media_gallery{
           disabled
           label
           position
           url
         }
         media_gallery_entries\{
           types
         }
       }
     }
   }
   ```

<u>Förväntade resultat</u>:

GraphQL-gränssnittet `media_gallery` ska innehålla fältet **[!UICONTROL types]**.

<u>Faktiska resultat</u>:

`media_gallery` innehåller inte mediefältet **[!UICONTROL types]**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
