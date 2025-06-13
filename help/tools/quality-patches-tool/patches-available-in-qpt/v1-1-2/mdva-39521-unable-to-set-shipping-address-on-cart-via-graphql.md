---
title: 'MDVA-39521: Det går inte att ange leveransadress för kundvagnar via GraphQL'
description: Korrigeringen MDVA-39521 löser problemet där användaren inte kan ange leveransadress på kundvagnar med ett tomt telefonnummer via GraphQL. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 är installerat. Korrigerings-ID är MDVA-39521. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: GraphQL, Orders, Shipping/Delivery, Shopping Cart
role: Admin
exl-id: aac44c20-b244-472b-bab0-7d6e7d99608a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39521: Det går inte att ange leveransadress för kundvagnar via GraphQL

Korrigeringen MDVA-39521 löser problemet där användaren inte kan ange leveransadress på kundvagnar med ett tomt telefonnummer via GraphQL. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 har installerats. Korrigerings-ID är MDVA-39521. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användaren kan inte ange leveransadress i kundvagnen med ett tomt telefonnummer via GraphQL trots att Visa telefonnummer är valfritt.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Gå till **Store** > **Konfiguration** > **Kunder** > **Kundkonfiguration** > **Namn- och adressalternativ** och ange Visa telefonnummer som valfritt.
1. Skapa en tom kundvagn på GraphQL-begäran.

   ```GraphQL
   mutation {
   createEmptyCart
   }
   ```

1. Lägg produkten i kundvagnen.

   ```GraphQL
   mutation {
   addSimpleProductsToCart(
   input: {
     cart_id: "{ CART_ID }"
     cart_items: [
       {
         data: {
           quantity: 1
           sku: "24-MG04"
         }
       }
     ]
   }
   ) {
   cart {
     items {
       id
       product {
         sku
         stock_status
       }
       quantity
     }
   }
   }
   }
   ```

1. Lägg till adress: GRAPHQL VARIABLES.

   ```GraphQL
   {
     "cartId": "6Efw00UbjPoP5cvTFhsswDTjpxs0Xupt"
   }
   ```

   ```GraphQL
   mutation ($cartId: String!) {
     setShippingAddressesOnCart(input: {cart_id: $cartId, shipping_addresses:
     {address: {firstname: "John", lastname: "Doe", company: "Company Name",
     street: ["820 Burrard Street"], city: "Vancouver", region: "BC", postcode: "V6Z 2J1",
     country_code: "CA", telephone: "123-456-0000", save_in_address_book: false}}}) {
       cart {
         shipping_addresses {
           firstname
           lastname
           company
           street
           city
           postcode
           telephone
           country {
             code
             label
           }
         }
       }
     }
   }
   ```

   Resultat:

   ```GraphQL
     {
         "data": {
             "setShippingAddressesOnCart": {
                 "cart": {
                     "shipping_addresses": [
                         {
                             "firstname": "John",
                             "lastname": "Canada",
                             "company": "Company Name",
                             "street": [
                                 "820 Burrard Street"
                             ],
                             "city": "Vancouver",
                             "postcode": "V6Z 2J1",
                             "telephone": "123-456-0000",
                             "country": {
                                 "code": "CA",
                                 "label": "CA"
                             }
                         }
                     ]
                 }
             }
         }
     }
   ```

1. Lägg till adress med tomt telefonnummer.

   ```GraphQL
   mutation ($cartId: String!) {
     setShippingAddressesOnCart(input: {cart_id: $cartId, shipping_addresses: {address: {firstname:
       "John", lastname: "Canada", company: "Company Name", street: ["820 Burrard Street"], city:
       "Vancouver", region: "BC", postcode: "V6Z 2J1", country_code: "CA", telephone: "123-456-0000",
       save_in_address_book: false}}}) {
       cart {
         shipping_addresses {
           firstname
           lastname
           company
           street
           city
           postcode
           telephone
           country {
             code
             label
           }
         }
       }
     }
   }
   ```

<u>Förväntade resultat</u>:

```GraphQL
 {
    "data": {
        "setShippingAddressesOnCart": {
            "cart": {
                "shipping_addresses": [
                    {
                        "firstname": "John",
                        "lastname": "Doe",
                        "company": "Company Name",
                        "street": [
                            "820 Burrard Street"
                        ],
                        "city": "Vancouver",
                        "postcode": "V6Z 2J1",
                        "telephone": "",
                        "country": {
                            "code": "CA",
                            "label": "CA"
                        }
                    }
                ]
            }
        }
    }
 }
```

<u>Faktiska resultat</u>:

```GraphQL
{
    "data": {
        "setShippingAddressesOnCart": {
            "cart": {
                "shipping_addresses": []
            }
        }
    }
}
```

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken distributionstyp du har när du vill använda enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
