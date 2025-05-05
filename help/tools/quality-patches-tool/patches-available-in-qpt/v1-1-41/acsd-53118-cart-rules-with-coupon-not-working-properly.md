---
title: 'ACSD-53118: Kupongregler fungerar inte som de ska'
description: Använd patchen ACSD-53118 för att korrigera Adobe Commerce-problemet där kundvagnsprisregeln tillämpas med hjälp av en kupongkod medan produkten i kundvagnen har ett tomt matchande attribut.
feature: Shopping Cart, Price Rules
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-53118: Kupongregler fungerar inte som de ska

Korrigeringen ACSD-53118 åtgärdar ett problem där kundvagnsprisregeln tillämpas med hjälp av en kupongkod medan produkten i kundvagnen har ett tomt matchande attribut. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 är installerad. Korrigerings-ID är ACSD-53118. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kupongprisregeln tillämpas med en kupongkod medan produkten i kundvagnen har ett tomt matchande attribut.

<u>Steg som ska återskapas</u>:

1. Skapa ett prisattribut och lägg till det i attributuppsättningen. Gör attributet användbart i kampanjregelvillkoren.
1. Skapa en produkt och lämna det nya attributet tomt.
1. Skapa en kundprisregel med en viss kupong och följande villkor:

   * Om ett objekt hittas i vagnen med ALLA dessa villkor är sant: Attribute1 är 0.

1. Lägg produkten som skapades i steg 2 i kundvagnen.
1. Använd kupongkoden för kundvagnsregeln som skapades i steg 3.

<u>Förväntade resultat</u>:

Rabatten gäller inte kundvagnen.

<u>Faktiska resultat</u>:

Rabatten tillämpas på kundvagnen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
