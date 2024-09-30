---
title: 'ACSD-49970: Felaktig hantering av GraphQL-fel'
description: Använd korrigeringsfilen ACSD-49970 för att åtgärda Adobe Commerce-problemet där GraphQL-fel hanteras felaktigt när [!UICONTROL New Relic Reporting] är aktiverat.
feature: GraphQL, Observability
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-49970: Felaktig hantering av GraphQL-fel

Korrigeringen ACSD-49970 åtgärdar ett problem där fel hantering av GraphQL-fel inträffar när *[!UICONTROL New Relic Reporting]* aktiveras. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 är installerad. Korrigerings-ID är ACSD-49970. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`GraphQLOperationNames`-nyckeln hanteras inte korrekt vare sig `logDataHelper` innehåller den här nyckeln eller inte.

<u>Steg som ska återskapas</u>:

1. Kör `bin/magento deploy:mode:set developer`.
1. Logga in på Admin.
1. Aktivera **[!UICONTROL New Relic Integration]** från **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**
(Obs! Även om ett fel visas som anger att tillägget [!DNL New Relic] inte är tillgängligt sparas konfigurationen.)
1. Kör den här *GraphQL*-mutationen till `http://yourMagentoDomain/graphql` från *[!DNL Altair]*-klienten eller någon annan klient eller via cURL.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (Obs! Ange **[!UICONTROL Header]** till [!UICONTROL Content-Currency:CA] innan du kör det).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>Förväntade resultat</u>:

Det finns inget *500-undantag* i loggarna. Nyckeln `GraphQLOperationNames` hanteras korrekt.

<u>Faktiska resultat</u>:

Det finns ett *500-undantag* i loggarna. Nyckeln `GraphQLOperationNames` hanteras inte korrekt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
