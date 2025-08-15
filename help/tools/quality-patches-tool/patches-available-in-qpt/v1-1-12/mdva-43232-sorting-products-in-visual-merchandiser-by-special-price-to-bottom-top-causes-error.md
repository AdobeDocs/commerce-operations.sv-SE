---
title: 'MDVA-43232: Sortering av produkter i visuell handlare efter specialpris till överkant (eller underkant) orsakar ett fel'
description: Korrigeringen MDVA-43232 åtgärdar ett problem där sortering av produkter i visuell handlare efter specialpris till överkant (eller underkant) orsakar ett fel när kategorin sparas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Korrigerings-ID är MDVA-43232. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
exl-id: c977bec8-f99c-4799-abce-26aad49b77e8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-43232: Sortering av produkter i visuell handlare efter specialpris till överkant (eller underkant) orsakar ett fel

Korrigeringen MDVA-43232 åtgärdar ett problem där sortering av produkter i visuell handlare efter specialpris till överkant (eller underkant) orsakar ett fel när kategorin sparas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Korrigerings-ID är MDVA-43232. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du sorterar produkter i visuell återförsäljare efter specialpris överst (eller nederst) uppstår ett fel när du sparar kategorin.

<u>Steg som ska återskapas</u>:

1. Kontrollera att det finns två webbplatser.
1. Navigera till **Lager** > **Konfiguration** > **Katalog** > **Pris** och ange Katalogens prisomfång = webbplats.
1. Navigera återigen till **Lager** > **Konfiguration** > **Katalog** > **Visual Merchandiser** > **Synliga attribut för kategoriregler** > och lägg till specialpris.
1. Skapa en enkel produkt och tilldela produkterna till båda webbplatserna.
1. Lägg till ett specialpris i standardomfånget för produkten.
1. Byt till den andra butikens omfattning och åsidosätt både priset och specialpriset för den produkten.
1. Gör en `catalog_product_price`-omindexering.
1. Gå till **Katalog** > **Kategorier** och skapa en ny kategori.
1. Lägg till en kategoriregel för att filtrera produkter som har ett särskilt pris.
1. Spara kategorin.
1. Under avsnittet Produkter i kategorin anger du Sorteringsordning = Specialpris överst (eller nederst).
1. Spara kategorin igen.

<u>Förväntade resultat</u>:

Kategorin sparas utan fel.

<u>Faktiska resultat</u>:

Ett undantag genereras:

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
