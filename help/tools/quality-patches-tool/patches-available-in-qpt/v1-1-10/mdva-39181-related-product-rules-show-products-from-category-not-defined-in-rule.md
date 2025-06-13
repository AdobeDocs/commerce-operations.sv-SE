---
title: 'MDVA-39181: Relaterade produktregler visar produkter från en kategori som inte definierats i regeln'
description: MDVA-39181-korrigeringen löser problemet där relaterade produktregler visar produkter från en kategori som inte definierats i regeln. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 är installerat. Korrigerings-ID är MDVA-39181. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Categories, Products
role: Admin
exl-id: 98f65b7d-2cb3-49ff-95ef-c23a922e49f2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-39181: Relaterade produktregler visar produkter från en kategori som inte definierats i regeln

MDVA-39181-korrigeringen löser problemet där relaterade produktregler visar produkter från en kategori som inte definierats i regeln. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 är installerat. Korrigerings-ID är MDVA-39181. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Relaterade produktregler visar produkter från kategorier som inte definierats i regeln.

<u>Förutsättningar</u>:

Installera exempeldata.

<u>Steg som ska återskapas</u>:

1. Skapa ett attributvarumärke och lägg till det i **Attributuppsättningen**.
1. Välj **Josie**, **Augusta** och **Ingrid**-fodral som du vill lägga till i kategorin Brand Kitty från **Women** > **Tops** > **Jackets**.
1. Välj **Beaumont**, **Hyperion** och **Kenobi**-schaket som du vill lägga till i Brand Kitty från **Men** > **Tops** > **Jacket-kategorin**.
1. Skapa en relaterad produkt med:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Produkter som ska matchas:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Produkter som ska visas:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Öppna SKU WJ04 från frontsidan och kontrollera relaterade produkter.
1. Uppdatera kategori-ID:t från **Kvinnor** > **Tops** > **Jackets** om det skiljer sig från detta.

<u>Förväntade resultat</u>:

Endast produkter från samma varumärke och samma underkategori visas i relaterade produkter.

<u>Faktiska resultat</u>:

Samhörande produkter visas med samma varumärke men med en slumpmässig överordnad kategori.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
