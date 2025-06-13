---
title: 'ACSD-54660: Ny sortering av indataattribut för att sortera kundorder i  [!DNL GraphQL]'
description: Använd patchen ACSD-54660 för att åtgärda Adobe Commerce-problemet där ett nytt indatafält,"sort", läggs till för att sortera kundorder i  [!DNL GraphQL] efter"sort_field" och"sort_direction".
feature: GraphQL, Orders
role: Admin, Developer
exl-id: 3962d4b6-634e-4164-adae-fa840ca7d869
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# ACSD-54660: Sortering av nya indataattribut har lagts till för att sortera kundorder i [!DNL GraphQL]

Korrigeringen för ACSD-54660 åtgärdar ett problem där ett nytt inmatningsattribut, `sort`, lades till för att sortera kundorder i [!DNL GraphQL] av `sort_field` och `sort_direction`. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39 är installerad. Korrigerings-ID är ACSD-54660. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det nya indataattributet `sort` har lagts till för att sortera kundorder i [!DNL GraphQL] av `sort_field` och `sort_direction`.

<u>Steg som ska återskapas</u>:

Fråga kundorder med [!DNL GraphQL]:

```
  {
    customerOrders {
      items {
        order_number
        id
        created_at
        grand_total
        status
      }
    }
  }
```

<u>Förväntade resultat</u>:

Den här korrigeringen lägger till `sort` och `sort_direction` argument i `customer.orders`.

<u>Faktiska resultat</u>:

Det går inte att sortera sorteringarna med [!DNL GraphQL].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
