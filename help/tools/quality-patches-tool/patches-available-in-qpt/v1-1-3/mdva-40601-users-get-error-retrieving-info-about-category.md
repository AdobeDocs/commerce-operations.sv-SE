---
title: 'MDVA-40601: Det går inte att hämta data om kategorin som ändrats av den schemalagda uppdateringen via GraphQL'
description: Adobe Commerce-kvalitetskorrigeringen MDVA-40601 åtgärdar ett problem där användare får ett felmeddelande när information om en kategori som ändrats vid en schemalagd uppdatering via GraphQL hämtas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 är installerat. Korrigerings-ID är MDVA-40601. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: Categories, GraphQL
role: Admin
exl-id: c50e9f77-66eb-4c4c-b0b5-b77db84a4a0b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-40601: Det går inte att hämta data om kategorin som ändrats av den schemalagda uppdateringen via GraphQL

Adobe Commerce-kvalitetskorrigeringen MDVA-40601 åtgärdar ett problem där användare får ett felmeddelande när information om en kategori som ändrats vid en schemalagd uppdatering via GraphQL hämtas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 har installerats. Korrigerings-ID är MDVA-40601. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.3.3 och 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användarna får ett felmeddelande när de försöker hämta information om en kategori som ändrats av en schemalagd uppdatering via GraphQL.

<u>Steg som ska återskapas</u>:

1. Ställ in en kategoristruktur med en underkategori enligt nedan:

   <pre>
   <code class="language-graphql">
   - Root
    - Some category
         - Some child category

   </code>
   </pre>

1. Kör GraphQL-fråga med &quot;Some Category&quot; ID 49.

   <pre>
    <code class="language-graphql">
    query &lbrace;
     category(id: 49) &lbrace;
      name
      children &lbrace;
        name
       &rbrace;
     &rbrace;
   &rbrace;
   </code>
   </pre>

   Resultat:

   <pre>
    <code class="language-graphql">
    &lbrace;
      "data": &lbrace;
        "category": &lbrace;
          "name": "Some category",
          "children": &lbrack;
            &lbrace;
              "name": "Some child category"
            &rbrace;
          &rbrack;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. Skapa en schemauppdatering för&quot;En kategori&quot; med ett annat kategorinamn.
1. Vänta tills schemauppdateringen har aktiverats.
1. Kör samma fråga som ovan.

<u>Förväntade resultat</u>:

Du får samma resultat men med det uppdaterade kategorinamnet.

<u>Faktiska resultat</u>:

Du får följande fel:

<pre>
<code class="language-graphql">
&lbrace;
  "errors": &lbrack;
    &lbrace;
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 2,
          "column": 3
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "category"
      &rbrack;
    &rbrace;
  &rbrack;,
  "data": &lbrace;
    "category": null
  &rbrace;
&rbrace;
</code>
</pre>

## Tillämpa korrigeringen

Använd följande länkar beroende på vilken distributionstyp du har när du vill använda enskilda korrigeringsfiler:

&#x200B;* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
&#x200B;* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om kvalitetspatchar för Adobe Commerce finns i:

&#x200B;* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
&#x200B;* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
