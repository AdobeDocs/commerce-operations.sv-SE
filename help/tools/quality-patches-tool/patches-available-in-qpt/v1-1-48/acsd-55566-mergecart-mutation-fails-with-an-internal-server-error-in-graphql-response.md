---
title: 'ACSD-55566: [!UICONTROL mergeCart]-mutationen misslyckas med internt serverfel i  [!DNL GraphQL] response'
description: Använd ACSD-55566-korrigeringen för att åtgärda Adobe Commerce-problemet där mutationen "mergeCart" misslyckas med ett internt serverfel i svaret från  [!DNL GraphQL]  när källan och målvagnen som har samma paketobjekt sammanfogas.
feature: GraphQL, Shopping Cart
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-55566: `mergeCart`-mutationen misslyckas med internt serverfel i [!DNL GraphQL]-svaret

ACSD-55566-korrigeringen åtgärdar ett problem där mutationen `mergeCart` misslyckas med ett internt serverfel i svaret på [!DNL GraphQL]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48 har installerats. Korrigerings-ID:t är ACSD-5566. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`mergeCart`-mutationen misslyckas med ett internt serverfel i [!DNL GraphQL]-svaret när källan och målvagnen som har samma paketobjekt sammanfogas.

<u>Steg som ska återskapas</u>:

1. Skapa en anpassad källa och en anpassad Stock.
1. Tilldela det skapade arkivet till huvudwebbplatsen.
1. Skapa en enkel produkt och tilldela den skapade källan till den (qty=2).
1. Skapa en paketprodukt med ett alternativ och en underordnad produkt (produkt skapad i steg 3).
1. Skapa en gästvagn via [!DNL GraphQL].
1. Lägg till en paketprodukt med båda alternativen markerade.
1. Spara *cartID*.
1. Skapa en kund och generera en kundtoken.
1. Skapa en kundvagn.
1. Lägg samma paketprodukt med samma konfiguration i kundvagnen.
1. Försök att sammanfoga gästvagnen med kundvagnen.

<u>Förväntade resultat</u>:

Kundvagnen innehåller produkter från båda vagnarna.

<u>Faktiska resultat</u>:

Du får ett internt fel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
