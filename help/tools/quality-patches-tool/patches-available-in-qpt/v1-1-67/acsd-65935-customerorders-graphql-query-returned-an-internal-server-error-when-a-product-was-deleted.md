---
title: 'ACSD-65935: "customerOrders" GraphQL-frågan returnerade ett internt serverfel när en produkt tas bort'
description: Använd patchen ACSD-65935 för att åtgärda Adobe Commerce-problemet där GraphQL-frågan "customerOrders" returnerade ett internt serverfel när en produkt tas bort.
feature: Orders, GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: fd0b7043770bbbd12fbb9aad8cddaa2434d2ea5b
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# ACSD-65935: `customerOrders` GraphQL-frågan returnerade ett internt serverfel när en produkt tas bort

Korrigeringen ACSD-65935 åtgärdar ett problem där GraphQL-frågan `customerOrders` returnerade ett internt serverfel när en produkt tas bort. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 har installerats. Korrigerings-ID är ACSD-65935. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

GraphQL-frågan `customerOrders` returnerar ett internt serverfel när en produkt tas bort.

<u>Steg som ska återskapas</u>:

1. Skapa två enkla produkter
1. Skapa en kund och beställ två produkter från frontend.
1. Gå till serverdelen och ta bort en produkt.
1. Skapa en kundtoken:

```
https://localhost/pub/graphql
mutation {
  generateCustomerToken(email: "test@test.com", password: "123123qA") {
    token
  }
}
```

1. Hämta listan med order med hjälp av filtret `eligible_for_return` (används i PWA för att hämta kundorder):

```
https://localhost/pub/graphql
{
  customerOrders {
    items {
      order_number
      id
      created_at
      grand_total
      status
			items{
				eligible_for_return
			}
    }
  }
}
```

<u>Förväntade resultat</u>:

Orderlistan samlas in utan fel.

<u>Faktiska resultat</u>:

Undantag: *Internt serverfel*

```
[2025-05-16T23:42:15.174025+00:00] report.ERROR: Call to a member function getIsReturnable() on null

{"exception":"[object] (GraphQL\\Error\\Error(code: 0): Call to a member function getIsReturnable() on null at /var/www/html/localhost/vendor/webonyx/graphql-php/src/Error/Error.php:170) [previous exception] [object] (Error(code: 0): Call to a member function getIsReturnable() on null at /var/www/html/localhost/magento2ee/app/code/Magento/Rma/Helper/Data.php:644)"}

[]
```


## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
