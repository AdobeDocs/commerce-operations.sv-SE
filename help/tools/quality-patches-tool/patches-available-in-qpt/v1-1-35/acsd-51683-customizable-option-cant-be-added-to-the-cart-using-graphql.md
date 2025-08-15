---
title: 'ACSD-51683: Det går inte att lägga till det anpassningsbara alternativet i kundvagnen med GraphQL'
description: Använd patchen ACSD-51683 för att åtgärda Adobe Commerce-problemet där det anpassningsbara alternativet inte kan läggas till i kundvagnen med GraphQL.
feature: GraphQL
role: Admin
exl-id: 9cdf71aa-3dea-4f8c-b4d6-d6f192a9710d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51683: Det går inte att lägga till det anpassningsbara alternativet i kundvagnen med GraphQL

Korrigeringen ACSD-51683 åtgärdar ett problem där det anpassningsbara alternativet inte kan läggas till i kundvagnen med GraphQL. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35 är installerad. Korrigerings-ID är ACSD-51683. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det anpassningsbara alternativet kan inte läggas till i kundvagnen med GraphQL.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt med ett anpassningsbart **textfält**-alternativ.
1. [Lägg till den skapade produkten i varukorgen](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) med det anpassningsbara alternativet via GraphQL.
1. Skicka GraphQL-förfrågan [kundvagn](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) för att kontrollera produkten och dess information i kundvagnen.

<u>Förväntade resultat</u>

Avsnittet `Customizable_options` i GraphQL-svaret innehåller de data som angavs när produkten lades till i kundvagnen.

<u>Faktiska resultat</u>

Avsnittet `Customizable_options` i GraphQL-svaret är tomt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
