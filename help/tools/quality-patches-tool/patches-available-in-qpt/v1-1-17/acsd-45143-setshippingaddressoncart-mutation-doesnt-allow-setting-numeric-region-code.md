---
title: 'ACSD-45143: setShippingAddressesOnCart-mutation anger inte numerisk regionkod som region'
description: Korrigeringen ACSD-45143 åtgärdar ett problem där mutationen setShippingAddressesOnCart inte tillåter inställning av numerisk regionkod som "region". Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 är installerat. Korrigerings-ID är ACSD-45143. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
feature: Orders, Shipping/Delivery, Shopping Cart
role: Admin
exl-id: c7d9d1f2-4731-406f-93bd-036f0fe75b1d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-45143: setShippingAddressesOnCart-mutation anger inte numerisk regionkod som region

Korrigeringen ACSD-45143 åtgärdar ett problem där mutationen setShippingAddressesOnCart inte tillåter inställning av numerisk regionkod som &quot;region&quot;. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 är installerat. Korrigerings-ID är ACSD-45143. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

mutationen setShippingAddressesOnCart tillåter inte inställning av numerisk regionkod som &quot;region&quot;.

<u>Steg som ska återskapas</u>:

1. Skapa en kundvagn med frågan nedan.

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      createEmptyCart
    &rbrace;
    </code>
    </pre>

1. Skicka en begäran om att ange leveransadressen till kundvagnen.

   <pre>
    <code class="language-graphql">
    mutation ($cartId: String!) &lbrace;
      setShippingAddressesOnCart(
        input: &lbrace;
          cart_id: $cartId
          shipping_addresses: &lbrace;
            address: &lbrace;
              firstname: "Tomek"
              lastname: "Nowak"
              company: "Company Name"
              street: ["234 Rue de Rivoli"]
              region: "58"
              city: "Lille"
              postcode: "59800"
              country_code: "FR"
              telephone: "123-456-0000"
              save_in_address_book: false
            &rbrace;
          &rbrace;
        &rbrace;
        ) &lbrace;
          cart &lbrace;
            shipping_addresses &lbrace;
              firstname
              lastname
              company
              street
              city
              region &lbrace;
                code
                label
              &rbrace;
              postcode
              telephone
              country &lbrace;
                code
                label
              &rbrace;
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

   Obs! landskoden är inställd på&quot;FR&quot; och regionkoden på&quot;58&quot; i det här exemplet. Enligt datatabellen `directory_country_region` är regionkod 58&quot;Nièvre&quot;.

1. Kontrollera det returnerade svaret.

<u>Förväntade resultat</u>:

Adobe Commerce tillåter att du ställer in numerisk regionkod i GraphQL-begäran.

<u>Faktiska resultat</u>:

Regionkoden ändras till 47.

<pre>
<code class="language-graphql">
&lbrace;
  "data": &lbrace;
    "setShippingAddressesOnCart": &lbrace;
      "cart": &lbrace;
        "shipping_addresses": &lbrack;
        &lbrace;
          "firstname": "Tomek",
          "lastname": "Nowak",
          "company": "Company Name",
          "street": &lbrack;
          "234 Rue de Rivoli"
          &rbrack;,
          "city": "Lille",
          "region": &lbrace;
            "code": "47",
            "label": "Lot-et-Garonne"
            &rbrace;,
            "postcode": "59800",
            "telephone": "123-456-0000",
            "country": &lbrace;
              "code": "FR",
              "label": "FR"
            &rbrace;
          &rbrace;
        &rbrack;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
