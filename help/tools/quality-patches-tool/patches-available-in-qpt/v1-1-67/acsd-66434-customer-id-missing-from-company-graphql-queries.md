---
title: 'ACSD-66434: [!UICONTROL Customer ID] saknas i företag [!DNL GraphQL] frågor'
description: Använd ACSD-66434-korrigeringen för att åtgärda Adobe Commerce-problemet där [!UICONTROL Customer ID] saknas i  [!DNL GraphQL] företagsfrågorna.
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 422e5a9eb9948032cccaac98415cf4b92895d5a9
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# ACSD-66434: [!UICONTROL Customer ID] saknas i företagets [!DNL GraphQL]-frågor

ACSD-66434-korrigeringen åtgärdar ett problem där **[!UICONTROL Customer ID]** saknas i [!DNL GraphQL]-företagsfrågor. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 har installerats. Korrigerings-ID är ACSD-66434. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p10 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Företagsfrågan [!DNL GraphQL] returnerar `null` för **[!UICONTROL Customer ID]** i företagsstrukturen.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce 2.4-utveckling med modulerna B2B och Inventory.
1. Aktivera B2B-funktioner i Commerce Admin och skapa ett testföretag.
1. Generera en innehavartoken för företagsadministratören med följande [!DNL GraphQL]-mutation:

```
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. Använd den genererade token för att hämta kundens företagsstruktur med följande [!DNL GraphQL]-fråga:

```
query {
  company {
    id
    name
    legal_name
    structure {
      items {
        entity {
          __typename
          ... on Customer {
            firstname
            lastname
            email
            job_title
            id
          }
        }
      }
    }
  }
}
```

<u>Förväntade resultat</u>:

**[!UICONTROL Customer ID]** ska returneras i företagsfrågan [!DNL GraphQL].

<u>Faktiska resultat</u>:

**[!UICONTROL Customer ID]** returnerar som `null` i företagsfrågan [!DNL GraphQL].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
