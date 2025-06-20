---
title: 'ACSD-65164: Felmeddelande när konfigurerbar produkt ordnas om med ett anpassat kryssrutealternativ valt'
description: Använd patchen ACSD-65164 för att åtgärda Adobe Commerce-problemet där felmeddelandet *Vissa av de valda alternativen inte är tillgängliga* inträffar när en konfigurerbar produkt med ett enda anpassat kryssrutealternativ sorteras.
feature: Products, Orders
role: Admin, Developer
exl-id: 22b72d24-4852-45ba-ac98-df9565f94539
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-65164: Felmeddelande när konfigurerbar produkt ordnas om med ett anpassat kryssrutealternativ valt

Korrigeringen ACSD-65164 åtgärdar ett problem där felmeddelandet *Vissa av de valda alternativen inte är tillgängliga* för tillfället när en konfigurerbar produkt sorteras om med ett enda anpassat kryssrutealternativ. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 har installerats. Korrigerings-ID är ACSD-65164. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du ändrar ordning på en konfigurerbar produkt med ett enda anpassat kryssrutealternativ returneras ett felmeddelande: *Vissa av de valda objektalternativen är inte tillgängliga*.

### Steg som ska replikeras:

1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Simple Product]** på Admin-panelen.
1. Lägg till en *kryssruta* under **[!UICONTROL Customizable Options]**.
   * Ange kryssrutealternativet som *Obligatorisk*.
   * Lägg till två alternativvärden.
1. Navigera till Storefront och logga in som en registrerad kund.
1. Lägg produkten i kundvagnen med ett kryssrutealternativ valt.
1. Gå till **[!UICONTROL Cart]** > **[!UICONTROL Proceed to Checkout]** > **[!UICONTROL Place an Order]**.
1. Gå till **[!UICONTROL My Account]** > **[!UICONTROL Orders]** > **[!UICONTROL Reorder]** om du vill lägga till samma produkt.

**Förväntade resultat:**

Produkten ska läggas till i kundvagnen.

**Faktiska resultat:**

Ett felmeddelande visas:

*Det gick inte att lägga till produkten med SKU &quot;24-MB01&quot; i kundvagnen: Vissa av de valda artikelalternativen är inte tillgängliga just nu.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
