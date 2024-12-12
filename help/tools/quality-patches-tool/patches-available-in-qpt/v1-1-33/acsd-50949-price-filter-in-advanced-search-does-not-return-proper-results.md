---
title: 'ACSD-50949: Prisfiltret i avancerad sökning returnerar inte korrekta resultat när det används tillsammans med SKU-filtret'
description: Använd patchen ACSD-50949 för att åtgärda Adobe Commerce-problemet där prisfiltret i den avancerade sökningen inte returnerar korrekta resultat när det används tillsammans med SKU-filtret.
feature: Orders, Search
role: Admin
exl-id: 89e54940-e763-4554-8641-a162516bcabd
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 1%

---

# ACSD-50949: Prisfilter vid avancerad sökning returnerar inte korrekta resultat när de används med SKU-filter

Korrigeringen ACSD-50949 åtgärdar ett problem där prisfiltret i den avancerade sökningen inte returnerar korrekta resultat när det används tillsammans med SKU-filtret. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 är installerad. Korrigerings-ID är ACSD-50949. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Problem

Prisfiltret i den avancerade sökningen returnerar inte korrekta resultat när det används tillsammans med SKU-filtret.

<u>Steg som ska återskapas</u>:

1. Skapa flera produkter, till exempel:

   | SKU | Namn | Pris | Kvantitet |
   |-----|-----------|-------|----------|
   | MJ1 | Produkt 1 | 10 dollar | 10 |
   | MJ2 | Produkt 2 | $15 | 10 |
   | MJ3 | Produkt 3 | 21 dollar | 10 |
   | MJ4 | Produkt 4 | 32 dollar | 10 |
   | MJ5 | Produkt 5 | 33 dollar | 10 |
   | MJ6 | Produkt 6 | 34 dollar | 10 |
   | MJ7 | Produkt 7 | 44 dollar | 10 |

1. Öppna **[!UICONTROL Advanced Search]** på Storefront och sök efter SKU: &quot;MJ&quot;.
1. Klicka på länken **[!UICONTROL Modify your search]**.
1. Lägg till ett prisintervall i villkoren från *1* till *21* och klicka på knappen **[!UICONTROL Search]**.

<u>Förväntade resultat</u>:

Endast produkter med priser i det definierade intervallet returneras.

<u>Faktiska resultat</u>:

Produkter med högre priser än *$21* returneras.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool]-handboken.
