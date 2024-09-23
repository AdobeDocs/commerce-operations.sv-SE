---
title: 'MDVA-39163: Leveransmetoder som inte är tillgängliga för nyregistrerade användare med produkter från gästsession'
description: MDVA-39163-korrigeringen åtgärdar ett problem där leveransmetoderna inte är tillgängliga när en ny användare registreras och produkterna i kundvagnen kommer från gästsessionen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 är installerat. Korrigerings-ID är MDVA-39163. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# MDVA-39163: Leveransmetoder som inte är tillgängliga för nyregistrerade användare med produkter från gästsessionen

MDVA-39163-korrigeringen åtgärdar ett problem där leveransmetoderna inte är tillgängliga när en ny användare registreras och produkterna i kundvagnen kommer från gästsessionen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 har installerats. Korrigerings-ID är MDVA-39163. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Leveransmetoder är inte tillgängliga när den nya användaren registreras och produkter i kundvagnen kommer från gästsessionen.

<u>Steg som ska återskapas</u>:

1. Gå till **Admin** > **Lager** > **Konfiguration** > **Försäljning** > **Leveransmetoder**. Aktivera endast leveransmetoden **Platta priser** och inaktivera allt annat.
1. I leveransmetoden **Platta priser** väljer du alternativet **Specifikt** land i inställningen **Leverera till tillämpliga länder** och väljer ett land i listan (t.ex. USA).
1. Gå till **Admin** > **Lager** > **Konfiguration** > **Kund** > **Kundkonfiguration** och ange **Kräv e-postbekräftelse** till _Ja_.
1. Skapa en ny e-postmall i mallen **Admin** > **Marknadsföring** > **E-postmallar** och läs in mallen `Footer (magento/luma)` och ersätt mallinnehållet med ett CMS-block.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Gå till **Admin** > **Innehåll** > **Design** > **Konfiguration** och välj det tema som gäller din klientwebbplats. Ställ in sidfotsmallen på den nya e-postmallen som skapas.
1. Gå till frontend och lägg till en produkt i kundvagnen.
1. Skapa en kund. Du får ett e-postmeddelande som bekräftar e-postadressen. Klicka på verifieringslänken. Du loggas in på webbplatsen.
1. Gå till **Mitt konto** och lägg till en adress. Ange adresslandet till det leveransland som du angav i administratörskonfigurationen tidigare.
1. Gå till kassan.

<u>Förväntade resultat</u>:

Det finns en leveransmetod eftersom kunden har en adress som är kompatibel med det land där leveransen sker.

<u>Faktiska resultat</u>:

Leveransmetoden är inte tillgänglig.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
