---
title: 'ACSD-60326: GraphQL-fråga om kundens [!UICONTROL Returns]-status ger ett fel'
description: Använd ACSD-60326-korrigeringen för att åtgärda Adobe Commerce-problemet där ett fel inträffar i GraphQL-frågan om kundens [!UICONTROL Returns]-status.
feature: GraphQL, Returns, Customers
role: Admin, Developer
exl-id: 5cfd7e0d-8703-43a0-86d3-e69612347534
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# ACSD-60326: GraphQL-fråga om kundens [!UICONTROL Returns]-status ger ett fel

ACSD-60326-korrigeringen åtgärdar ett problem där ett fel inträffar i GraphQL-frågan om kundens [!UICONTROL Returns]-status. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 är installerad. Korrigerings-ID är ACSD-60326. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL-fråga om kundens [!UICONTROL Returns]-status ger ett fel.

<u>Steg som ska återskapas</u>:

1. Initiera en ny instans med exempeldata.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]** i sidofältet *[!UICONTROL Admin]* och ange **[!UICONTROL Enable RMA on Storefront]** som *Ja*.
1. Gå till **[!UICONTROL Sales]** > **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** och fyll i adressen.
1. Ändra lösenordet för kunden `roni_cost@example.com`.
1. Logga in på administratörspanelen och gör en beställning för kunden `roni_cost@example.com` med följande produkter:
   * *WSH12-32-Red*
   * *WSH12-32-Purple*
   * *WSH12-32-Green*
1. Skapa en *[!UICONTROL Invoice]* och *[!UICONTROL Shipment]* för den här ordern.
1. Välj **[!UICONTROL Create Returns]**.
1. Gå till **[!UICONTROL Return Items]** > **[!UICONTROL Add Items]** och:
   * Välj *WSH12-32-Red* och *WSH12-32-Purple*
   * Klicka på **[!UICONTROL Add Selected Products to returns]**:
      * Ange **[!UICONTROL Requested]** = *1*
      * Ange **[!UICONTROL Return Reason]** som *Out of Service*
      * Ange **[!UICONTROL Item Condition]** till *Öppnad*
      * Ange **[!UICONTROL Resolution]** till *Återbetalning*
   * Klicka på **[!UICONTROL Submit Returns]**.
1. Öppna **[!UICONTROL Returns]** och välj **[!UICONTROL Return Items]** till vänster.
   * Ange **[!UICONTROL Authorized]** = *1* för båda produkterna
   * Ange **[!UICONTROL Status]** som *auktoriserad* för *WSH12-32-lila*
   * Ange **[!UICONTROL Status]** som *Nekad* för *WSH12-32-Red*
   * Klicka på **[!UICONTROL Save]**
1. Skapa en ny order med samma produkter.
1. Skapa en *[!UICONTROL Invoice]*, *[!UICONTROL Shipment]* och *[!UICONTROL Returns]* för samma produkter. Auktorisera båda och fortsätt till slutet av [!UICONTROL Returns]-processen.
1. Generera en kundtoken med följande GraphQL-fråga:

   ```GraphQL
    mutation {
     generateCustomerToken(email: "roni_cost@example.com", password: "password") {
       token
      }
   }
   ```

1. Autentisera med mottagen token och utför följande fråga:

   ```
   {
   customer {
       returns(pageSize: 20, currentPage: 1) {
        total_count
           items {
               uid
               number
               status
               created_at
           }
       }
   }
   }
   ```

<u>Förväntade resultat</u>:

Frågan innehåller inga fel. Status för den andra returen är inte *null*.

<u>Faktiska resultat</u>:

Frågan returnerar ett internt serverfel:

```
    {
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 8,
                    "column": 5
                }
            ],
            "path": [
                "customer",
                "returns",
                "items",
                1,
                "status"
            ]
        }
    ],
    "data": {
        "customer": {
            "returns": {
                "total_count": 2,
                "items": [
                    {
                        "uid": "MQ==",
                        "number": "000000001",
                        "status": "PARTIALLY_AUTHORIZED",
                        "created_at": "2024-07-09 10:35:55"
                    },
                    {
                        "uid": "Mg==",
                        "number": "000000002",
                        "status": null,
                        "created_at": "2024-07-09 10:50:02"
                    }
                ]
            }
        }
    }
    } 
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
