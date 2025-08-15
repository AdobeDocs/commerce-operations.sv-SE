---
title: 'ACSD-51120: Cacheminnet för GraphQL GET-begäranden har inte rensats för CMS-sidor som innehåller CMS-block'
description: Använd korrigeringsfilen ACSD-51120 för att åtgärda Adobe Commerce-problemet där GraphQL GET Request Cache inte rensas för CMS-sidor som innehåller CMS-block.
exl-id: e1b84db0-2441-4729-aeeb-8486a623aebf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-51120: Cacheminnet för GraphQL GET-begäranden har inte rensats för CMS-sidor som innehåller CMS-block

Korrigeringen ACSD-51120 åtgärdar ett problem där GraphQL GET Request Cache inte rensas för CMS-sidor som innehåller CMS-block som uppdateras via en mellanlagringsuppdatering. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 är installerad. Korrigerings-ID är ACSD-51120. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Cacheminnet för GraphQL GET-begäranden rensas inte för CMS-sidor som innehåller CMS-block som uppdateras via en mellanlagringsuppdatering.

<u>Steg som ska återskapas</u>:

1. Skapa ett CMS-block.
1. Inkludera CMS-blocket på en CMS-sida med [!DNL Page Builder].
1. Hämta CMS-sidan med den aktuella GraphQL-frågan från GET:

   ```GraphQL
   {
   cmsPage( identifier: "<CMS PAGE IDENTIFIER>") {
       content
       content_heading
       identifier
       meta_description
       meta_keywords
       meta_title
       page_layout
       title
       url_key
   }
   }
   ```

1. Kontrollera att GraphQL-svaret är cachelagrat i [!DNL Varnish].
1. Skapa en schemalagd uppdatering för blocket.
1. Vänta tills den schemalagda uppdateringen har tillämpats och kör kron-jobbet för att tillämpa den schemalagda uppdateringen.
1. Hämta CMS-sidan igen med den aktuella GraphQL-frågan genom en GET-begäran.

<u>Förväntade resultat</u>:

Svaret visar det uppdaterade innehållet.

<u>Faktiska resultat</u>:

Svaret visar fortfarande det gamla innehållet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
