---
title: 'ACSD-56546: Konfigurerbara produkter och paketprodukter visas som obefintliga i butiken'
description: Använd korrigeringsfilen ACSD-56546 för att åtgärda Adobe Commerce-problemet där de konfigurerbara produkterna och paketprodukterna visas som lagrade utanför butiken när konfigurationsalternativet *[!UICONTROL Display Out of Stock Products]* är inaktiverat.
feature: Storefront, Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-56546: Konfigurerbara produkter och paketprodukter visas som obefintliga i butiken

Korrigeringen ACSD-56546 åtgärdar ett problem där de konfigurerbara produkterna och paketprodukterna visas som lagrade utanför butiken. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48 har installerats. Korrigerings-ID är ACSD-56546. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Konfigurerbara produkter och paketprodukter visas som lager utanför butiken när alternativet *[!UICONTROL Display Out of Stock Products]* är inaktiverat.

<u>Steg som ska återskapas</u>:

1. Ställ in alternativet **[!UICONTROL Display Out of Stock Products]** på *Nej*.
1. Skapa en webbplats, butik och butik.
1. Skapa en källa och ett lager och tilldela det sedan till den andra webbplatsen.
1. Skapa en *konfigurerbar produkt* med två underordnade produkter. Tilldela båda de underordnade produkterna till både källor och båda webbplatser.
1. Uppdatera den första underordnade produkten så att den har *qty=0* i båda källorna.
1. Uppdatera den andra underordnade produkten och inaktivera den på den andra webbplatsen.
1. Gör en fullständig omindexering.
1. Kontrollera kategorin som innehåller den konfigurerbara produkten på den andra webbplatsen.

<u>Förväntade resultat</u>:

De färdiga konfigurerbara produkterna visas inte i butiken.

<u>Faktiska resultat</u>:

De färdiga konfigurerbara produkterna visas i butiken även när alternativet *[!UICONTROL Display Out of Stock Products]* är inaktiverat.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
