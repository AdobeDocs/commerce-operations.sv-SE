---
title: 'ACSD-58352: Returattributetiketter för standardarkivet returneras via  [!DNL GraphQL] API'
description: Använd patchen ACSD-58352 för att åtgärda Adobe Commerce-problemet där returattributetiketter för standardbutiken returneras via  [!DNL GraphQL] API när en icke-standardbutiksvy anges i begärandehuvudet.
feature: GraphQL, Returns
role: Admin, Developer
exl-id: e513039e-42cd-4dac-963b-3068ba8bf7ee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-58352: Returattributetiketter för standardarkivet returneras via [!DNL GraphQL] API

Korrigeringen ACSD-58352 åtgärdar ett problem där returattributetiketter för standardarkivet returneras via [!DNL GraphQL] API när en icke-standardbutiksvy anges i begärandehuvudet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 är installerad. Korrigerings-ID är ACSD-58352. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Returattributetiketter för standardbutiken returneras via [!DNL GraphQL] API.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL Return Merchandising Authorization]**.
1. Skapa en *[!UICONTROL Additional Store]* och en *[!UICONTROL Store View]* under standardwebbplatsen.
1. Redigera returattributet **[!UICONTROL Reason for Return]** och lägg till etiketter för alla butiksvyer.
1. Skapa en *[!UICONTROL Order]*.
1. Skapa en *[!UICONTROL Return]* för den ordern. Kontrollera att *[!UICONTROL Return]* har statusen *[!UICONTROL Pending]*.
1. Skicka en fråga från kunden [!DNL GraphQL] med den angivna icke-standardinställningen [!UICONTROL Store View] i huvudet:

   ```
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. Observera svaret.

<u>Förväntade resultat</u>

Returetiketter i svaret [!DNL GraphQL] är för [!UICONTROL Store View] som angetts i begärandehuvudet.

<u>Faktiska resultat</u>:

Returetiketter i svaret [!DNL GraphQL] är för standardvärdet [!UICONTROL Store View].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
