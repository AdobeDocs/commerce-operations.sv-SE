---
title: 'ACSD-58566: GraphQL interna serverfel för inköpsorderkommentarer'
description: Använd patchen ACSD-58566 för att åtgärda Adobe Commerce-problemet där GraphQL returnerar ett internt serverfel när fältet "created_at" frågas i mutationen "addPurchaseOrderComment".
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
exl-id: 6d051f57-7a2f-44a5-a1c9-834917ed986c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-58566: GraphQL interna serverfel för inköpsorderkommentarer

Korrigeringen ACSD-58566 åtgärdar ett problem där frågan om fältet `created_at` i mutationen `addPurchaseOrderComment` returnerar ett null-värde i stället för det förväntade datetime-värdet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 är installerad. Patch-ID:t är ACSD-58566. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL returnerar ett internt serverfel när fältet `created_at` efterfrågas i mutationen `addPurchaseOrderComment`.

<u>Förutsättningar</u>:

B2B-moduler installeras och företags- och inköpsorder aktiveras.

<u>Steg som ska återskapas</u>:

1. Generera en kundtoken för en företagsanvändare.
1. Utför följande sekvens av GraphQL-förfrågningar:
   1. Skapa en *kundvagn* med `customerCart`.
   1. Lägg till en produkt i *kundvagnen* med `addProductsToCart`.
   1. Placera beställningen med `placePurchaseOrder`.
   1. Lägg till en kommentar till inköpsordern med `addPurchaseOrderComment`.

   ```
   mutation {
       addPurchaseOrderComment(
           input: { purchase_order_uid: "MQ==", comment: "Looks good to me" }
   ) {
           comment {
               uid
               created_at
               author {
                   firstname
                   lastname
                   email
               }
               text
           }
       }
   }
   ```

<u>Förväntade resultat</u>:

Fältet `created_at` returnerar datum/tid för inköpsorderkommentaren.

<u>Faktiska resultat</u>:

Visar null i stället för datumet `created_at`.

```
{
  "errors": [
    {
      "message": "Internal server error",
      "locations": [
        {
          "line": 10,
          "column": 1
        }
      ],
      "path": [
        "addPurchaseOrderComment",
        "comment",
        "created_at"
      ]
    }
  ],
  "data": {
    "addPurchaseOrderComment": null
  }
}
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

[[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
