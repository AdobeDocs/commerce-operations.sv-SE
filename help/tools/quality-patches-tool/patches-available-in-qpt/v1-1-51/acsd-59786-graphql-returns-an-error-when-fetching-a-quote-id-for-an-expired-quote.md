---
title: 'ACSD-59786: GraphQL returnerar ett fel när en offert_id hämtas för en offert som har gått ut'
description: Använd patchen ACSD-59786 för att åtgärda Adobe Commerce-problemet där en GraphQL-fråga returnerar ett fel när en offert_id hämtas för en offert som har gått ut.
feature: GraphQL, Quotes, Companies
role: Admin, Developer
exl-id: 3c7aaa99-a2e0-44fe-9426-b24095615915
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-59786: GraphQL returnerar ett fel när en `quote_id` för en offert som har upphört att gälla hämtas

Korrigeringen ACSD-59786 åtgärdar ett problem där en GraphQL-fråga returnerar ett fel när en `quote_id` hämtas för en offert som har gått ut. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 är installerad. Korrigerings-ID är ACSD-59786. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En GraphQL-fråga returnerar ett fel när en `quote_id` för en offert som har gått ut hämtas.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL Companies]** och **[!UICONTROL Purchase Orders]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** och ställ in **[!UICONTROL Enable Company]** på *Ja*.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** > **[!UICONTROL Order Approval Configuration]** och ställ in **[!UICONTROL Enable Purchase Orders]** på *Ja*.
1. Skapa ett nytt företag och ange **[!UICONTROL Enable Purchase Orders]** till *Ja* för samma.
1. Skapa en enkel produkt och tilldela den till en kategori.
1. Logga in på Storefront med hjälp av företagets administratörskonto och skapa en ny order med **[!UICONTROL Purchase Order]** som betalningsmetod.
1. Ändra **[!UICONTROL Quote Lifetime (days)]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*.
1. Kör kommandot `bin/magento c:f`.
1. Gå till databasen `quote_table` och ändra värdena `created_at` och `updated_at` en dag tidigare.
1. Kör kommandot `bin/magento cron:run --group="sales_clean_quotes`.
1. Kör GraphQL-begäran som anges nedan med en auktoriserad token för den administratör som skapar **[!UICONTROL Purchase Order]**:

   ```GraphQL
   {
       customer {
           purchase_order(uid: "MQ==") {
               quote {
                   id
               }
           }
       }
   } 
   ```

<u>Förväntade resultat</u>:

GraphQL-frågan returnerar `quote_id`.

<u>Faktiska resultat</u>:

GraphQL-frågan returnerar ett internt serverfel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
