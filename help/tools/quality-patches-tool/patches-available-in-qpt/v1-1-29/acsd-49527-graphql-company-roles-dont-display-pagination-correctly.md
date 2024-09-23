---
title: "ACSD-49527: GraphQL företagsroller visar inte sidnumreringen korrekt"
description: Använd patchen ACSD-49527 för att åtgärda Adobe Commerce-problemet där GraphQL företagsroller inte visar sidnumrering korrekt.
feature: B2B, GraphQL, Companies, Roles/Permissions
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-49527: GraphQL företagsroller visar inte sidnumrering korrekt

Korrigeringen ACSD-49527 åtgärdar ett problem där GraphQL företagsroller inte visar sidnumrering korrekt. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 är installerad. Korrigerings-ID är ACSD-49527. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL företagsroller visar inte sidnumrering korrekt.

<u>Steg som ska återskapas</u>:

1. Aktivera B2B-företag.
1. Skapa ett nytt företag i butiken.
1. Skapa minst två nya roller för det här företaget, så det finns totalt tre roller, eftersom en roll är standardrollen.
1. Skicka GraphQL-begäran om att få roller som anger [!UICONTROL pageSize]: 2.

   ```GraphQL
   query {
       company {
           roles(pageSize: 2, currentPage: 1) {
               items {
                   name
               }
               total_count
               page_info {
                   total_pages
                   current_page
               }
           }
       }
   } 
   ```

1. Se GraphQL svar.

<u>Förväntade resultat</u>:

`total_count: 3` och `total_pages: 2` returneras i GraphQL-svaret.

<u>Faktiska resultat</u>:

`total_count: 2` och `total_pages: 1` returneras i GraphQL-svaret.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
