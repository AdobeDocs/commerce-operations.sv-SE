---
title: 'ACSD-50815: Decimalkvantitet för enkel produkt kan inte användas för nya paketerade produkter'
description: Använd patchen ACSD-50815 för att åtgärda problemet med Adobe Commerce där decimalkvantiteten för en enkel produkt inte kan användas för ett nytt produktalternativ.
feature: Products
role: Admin
exl-id: 5cd69abe-bd88-497d-9696-804c787b73ef
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-50815: Decimalkvantitet för enkel produkt kan inte användas för nya paketerade produkter

Korrigeringen ACSD-50815 åtgärdar ett problem där decimalkvantiteten för en enkel produkt inte kan användas för ett nytt produktalternativ. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35 är installerad. Korrigerings-ID är ACSD-50815. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Decimalkvantiteten för en enkel produkt kan inte användas för ett nytt produktalternativ som paketeras.

<u>Steg som ska återskapas</u>:

1. Logga in som administratör.
1. Skapa en ny enkel produkt.
   * I fönstret **[!UICONTROL Advanced Inventory]** anger du [!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes].
   * Spara den enkla produkten.
1. Skapa en ny paketerad produkt.
1. Lägg till valfritt alternativ.
1. Lägg till den enkla produkten i det här alternativet.
1. Ange en decimalkvantitet för den enkla produkten i produktalternativet för paketerade produkter. Exempel: 1.5.

<u>Förväntade resultat</u>:

Det går att ange decimalkvantitet. Inga fel visas.

<u>Faktiska resultat</u>:

Felet *Ange ett giltigt nummer i fältet* visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
