---
title: 'MDVA-41631: Fel vid hämtning av orderinformation utan "telefonvärde" (tillval)'
description: Korrigeringen MDVA-41631 åtgärdar ett problem där användare får ett fel när de hämtar orderinformation utan valfritt telefonvärde till och med  [!DNL GraphQL]. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 är installerat. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: Orders
role: Admin
exl-id: e56cea59-ffc1-4520-85ca-136cda613884
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-41631: Fel vid hämtning av orderinformation utan &quot;telefonvärde&quot; (tillval)

Korrigeringen MDVA-41631 åtgärdar ett problem där användare får ett fel när de hämtar orderinformation utan valfritt telefonvärde via [!DNL GraphQL]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 installeras. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användarna får ett fel vid hämtning av orderinformation utan valfritt telefonvärde till [!DNL GraphQL].

<u>Steg som ska återskapas</u>:

1. Gå till **Store** > **Konfiguration** > **Kunder** > **Kundkonfiguration** > **Alternativ för namn och adress** > **Visa telefonnummer** och ange telefonnumret som valfritt.
1. Gör en beställning med [!DNL GraphQL API] som inloggad kund.
   * Ange inte telefonnumret när du anger fakturerings- och leveransadress. Följ instruktionerna i [[!DNL GraphQL] självstudiekursen för utcheckning](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) i utvecklardokumentationen.
1. Hämta ordningen med [!DNL GraphQL] [`customerOrders`-frågan ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/).

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>Förväntade resultat</u>:

Användarna får orderinformationen.

<u>Faktiska resultat</u>:

Användarna får följande fel: *&quot;message&quot;: &quot;Internal server error&quot;,*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
