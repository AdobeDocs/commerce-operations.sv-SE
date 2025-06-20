---
title: 'ACSD-56090: GraphQL-svar är inte specifikt för arkivering'
description: Använd patchen ACSD-56090 för att åtgärda Adobe Commerce-problemet där GraphQL-svaret innehåller alla lagrade data i stället för butiksspecifika data.
feature: GraphQL
role: Admin, Developer
exl-id: 0909c09c-3260-43d2-8eac-0e5d7639f24b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-56090: GraphQL-svar är inte specifikt för arkivering

Korrigeringen ACSD-56090 åtgärdar ett problem där GraphQL-svaret innehåller alla lagrade data i stället för butiksspecifika data. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 har installerats. Korrigerings-ID är ACSD-56090. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL-svar innehåller alla lagrar data i stället för butiksspecifika data.

<u>Steg som ska återskapas</u>:

1. Logga in på **[!UICONTROL Admin panel]** > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** och skapa två rotkategorier.
1. Varje rotkategori bör ha en underkategori.
1. Navigera till **[!UICONTROL Stores]** > **[!UICONTROL All stores]** > Två butiker finns med olika rotkategorier för var och en av dem. (Varje butik ska ha minst en butiksvy)
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > Skapa en produkt med

* Alla rot- och underkategorier som tilldelats
* Alla tilldelade webbplatser.

1. Kör GraphqQL-frågan (add header — store = &#39;storename ):

```
   query {
     products(filter: { url_key: { eq: "abc" } }) {
       items {
         categories {
           name
           id
           url_path
           breadcrumbs {
             category_id
             category_name
             category_level
           }
         }
       }
     }
   }
```

1. Kontrollera svaret när GraphqQL-frågan har körts.

<u>Förväntade resultat</u>:

Butiksspecifika data returneras

<u>Faktiska resultat</u>:

Data som returneras är inte lagringspecifika.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
