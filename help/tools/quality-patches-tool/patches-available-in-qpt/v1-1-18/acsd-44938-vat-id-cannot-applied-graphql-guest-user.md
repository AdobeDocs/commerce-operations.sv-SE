---
title: "ACSD-44938: VAT_ID kan inte användas i  [!DNL GraphQL] begäran för gästanvändare"
description: Korrigeringen ACSD-44938 åtgärdar ett problem där "VAT_ID" inte kan tillämpas i en  [!DNL GraphQL] begäran för en gästanvändare. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 är installerat. Korrigerings-ID är ACSD-44938. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
feature: Admin Workspace, GraphQL
role: Admin
exl-id: 62d36c27-545a-4c32-be69-a92e4b3ca2ca
source-git-commit: 3fdefc6201714c441d63574d293863e83205894b
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-44938: Det går inte att använda VAT_ID i [!DNL GraphQL]-begäran för gästanvändare

ACSD-44938-korrigeringen åtgärdar ett problem där `VAT_ID` inte kan tillämpas i en [!DNL GraphQL]-begäran för en gästanvändare. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 är installerat. Korrigerings-ID är ACSD-44938. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`VAT_ID` kan inte användas i en [!DNL GraphQL]-begäran för en gästanvändare.

<u>Steg som ska återskapas</u>:

1. Följ stegen som anges i [[!DNL GraphQL] självstudiekursen](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) i utvecklardokumentationen för att skapa en gästvagn.
1. Försök att använda `VAT_ID` för gästanvändaren med [!DNL GraphQL].

<u>Förväntade resultat</u>:

`VAT_ID` kan användas på samma sätt som för en registrerad kund. Läs artikeln [`createCustomerAddress` mutation ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/create-address/) i utvecklardokumentationen.

<u>Faktiska resultat</u>:

`VAT_ID` kan inte användas för en gästanvändare med [!DNL GraphQL].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
